---
title: ICorDebugProcess6::EnableVirtualModuleSplitting, méthode
ms.date: 03/30/2017
ms.assetid: e7733bd3-68da-47f9-82ef-477db5f2e32d
ms.openlocfilehash: ac61ffc553191aa70bdf5c04822a25b1074c2099
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209355"
---
# <a name="icordebugprocess6enablevirtualmodulesplitting-method"></a>ICorDebugProcess6::EnableVirtualModuleSplitting, méthode
Active ou désactive le fractionnement de module virtuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnableVirtualModuleSplitting(  
   BOOL enableSplitting  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `enableSplitting`  
 `true` pour activer le fractionnement de module virtuel ; `false` pour le désactiver.  
  
## <a name="remarks"></a>Remarks  
 Le fractionnement de modules virtuels fait que [ICorDebug](icordebug-interface.md) reconnaît les modules qui ont été fusionnés au cours du processus de génération et les présente sous la forme d’un groupe de modules distincts plutôt qu’un seul module de grande taille. Cela modifie le comportement de diverses méthodes [ICorDebug](icordebug-interface.md) décrites ci-dessous.  
  
> [!NOTE]
> Cette méthode est uniquement disponible avec .NET Native.  
  
 Cette méthode peut être appelée et la valeur de `enableSplitting` peut être modifiée à tout moment. Elle n’entraîne pas de modifications fonctionnelles avec état dans un objet [ICorDebug](icordebug-interface.md) , à l’exception de la modification du comportement des méthodes répertoriées dans la section [fractionnement de module virtuel et API de débogage non managé](#APIs) au moment où elles sont appelées. L'utilisation de modules virtuels entraîne une baisse des performances lors de l'appel de ces méthodes. En outre, une mise en cache significative des métadonnées virtualisées peut être nécessaire pour implémenter correctement les API [IMetaDataImport](../metadata/imetadataimport-interface.md) , et ces caches peuvent être conservés même après la désactivation du fractionnement de module virtuel.  
  
## <a name="terminology"></a>Terminologie  
 Les termes suivants sont employés dans le cadre du fractionnement de module virtuel :  
  
 modules conteneurs ou conteneurs  
 Modules d'agrégation.  
  
 sous-modules ou modules virtuels  
 Modules trouvés dans un conteneur.  
  
 modules standards  
 Modules non fusionnés au moment de la génération. Ce ne sont ni des modules conteneurs ni des sous-modules.  
  
 Les modules conteneurs et les sous-modules sont représentés par des objets de l'interface ICorDebugModule. Toutefois, le comportement de l’interface est légèrement différent dans chaque cas, comme décrit dans la section \< x-Ref to section>.  
  
## <a name="modules-and-assemblies"></a>Modules et assemblys  
 Les assemblys composés de plusieurs modules ne sont pas pris en charge dans le cadre de la fusion d'assemblys, où il existe une relation un-à-un entre un module et un assembly. Chaque objet ICorDebugModule, représentant un module conteneur ou un sous-module, est associé à un objet ICorDebugAssembly correspondant. La méthode [ICorDebugModule :: GetAssembly](icordebugmodule-getassembly-method.md) convertit le module en assembly. Pour mapper dans l’autre sens, la méthode [ICorDebugAssembly :: EnumerateModules,](icordebugassembly-enumeratemodules-method.md) énumère uniquement 1 module. Comme l'assembly et le module forment ici une paire fortement couplée, les termes assembly et module sont largement interchangeables.  
  
## <a name="behavioral-differences"></a>Différences de comportement  
 Les modules conteneurs présentent les comportements et caractéristiques suivants :  
  
- Leurs métadonnées pour tous les sous-modules constitutifs sont fusionnées.  
  
- Leurs noms de type peuvent être altérés.  
  
- La méthode [ICorDebugModule :: GetName](icordebugmodule-getname-method.md) retourne le chemin d’accès à un module sur disque.  
  
- La méthode [ICorDebugModule ::](icordebugmodule-getsize-method.md) Desize retourne la taille de cette image.  
  
- La méthode ICorDebugAssembly3.EnumerateContainedAssemblies répertorie les sous-modules.  
  
- La méthode ICorDebugAssembly3.GetContainerAssembly retourne `S_FALSE`.  
  
 Les sous-modules présentent les comportements et caractéristiques suivants :  
  
- Ils comportent un jeu réduit de métadonnées qui correspond uniquement à l’assembly d’origine ayant été fusionné.  
  
- Les noms des métadonnées ne sont pas altérés.  
  
- Les jetons de métadonnées ne correspondent généralement pas aux jetons présents dans l’assembly d’origine avant sa fusion au moment de la génération.  
  
- La méthode [ICorDebugModule :: GetName](icordebugmodule-getname-method.md) retourne le nom de l’assembly, et non un chemin d’accès au fichier.  
  
- La méthode [ICorDebugModule ::](icordebugmodule-getsize-method.md) Desize retourne la taille d’image non fusionnée d’origine.  
  
- La méthode ICorDebugModule3.EnumerateContainedAssemblies retourne `S_FALSE`.  
  
- La méthode ICorDebugAssembly3.GetContainerAssembly retourne le module conteneur.  
  
## <a name="interfaces-retrieved-from-modules"></a>Interfaces récupérées des modules  
 Diverses interfaces peuvent être créées ou récupérées à partir des modules. entres autres :  
  
- Objet ICorDebugClass, qui est retourné par la méthode [ICorDebugModule :: GetClassFromToken,](icordebugmodule-getclassfromtoken-method.md) .  
  
- Objet ICorDebugAssembly, qui est retourné par la méthode [ICorDebugModule :: GetAssembly](icordebugmodule-getassembly-method.md) .  
  
 Ces objets sont toujours mis en cache par [ICorDebug](icordebug-interface.md)et ils auront la même identité de pointeur, qu’ils aient été créés ou interrogés à partir du module de conteneur ou d’un sous-module. Le sous-module présente une vue filtrée de ces objets mis en cache, pas un cache distinct avec ses propres copies.  
  
<a name="APIs"></a>
## <a name="virtual-module-splitting-and-the-unmanaged-debugging-apis"></a>Fractionnement de module virtuel et API de débogage non managées  
 Le tableau suivant montre de quelle manière le fractionnement de module virtuel modifie le comportement d'autres méthodes dans l'API de débogage non managée.  
  
|Méthode|`enableSplitting` = `true`|`enableSplitting` = `false`|  
|------------|---------------------------------|----------------------------------|  
|[ICorDebugFunction::GetModule](icordebugfunction-getmodule-method.md)|Retourne le sous-module dans lequel cette fonction a été initialement définie.|Retourne le module conteneur dans lequel cette fonction a été fusionnée.|  
|[ICorDebugClass::GetModule](icordebugclass-getmodule-method.md)|Retourne le sous-module dans lequel cette classe a été initialement définie.|Retourne le module conteneur dans lequel cette classe a été fusionnée.|  
|ICorDebugModuleDebugEvent::GetModule|Retourne le module conteneur qui a été chargé. Les sous-modules ne reçoivent pas d'événements de chargement, indépendamment de la valeur de ce paramètre.|Retourne le module conteneur qui a été chargé.|  
|[ICorDebugAppDomain::EnumerateAssemblies](icordebugappdomain-enumerateassemblies-method.md)|Retourne une liste des sous-assemblys et des assemblys standards. La liste n'inclut pas les assemblys conteneurs. **Remarque :**  S’il manque des symboles dans un assembly de conteneur, aucun de ses sous-assemblys ne sera énuméré. S'il manque des symboles dans un assembly standard, celui-ci pourra ou non être énuméré, en fonction des cas.|Retourne une liste des assemblys conteneurs et des assemblys standards. La liste n'inclut pas les sous-assemblys. **Remarque :**  Si des symboles manquent dans un assembly normal, il est possible qu’il ne soit pas énuméré.|  
|[ICorDebugCode :: GetCode](icordebugcode-getcode-method.md) (en cas de référence au code il uniquement)|Retourne le code IL qui serait valide dans une image d’assembly avant la fusion. En particulier, les jetons de métadonnées inline doivent être des jetons TypeRef ou MemberRef quand les types référencés ne sont pas définis dans le module virtuel qui contient le code IL. Ces jetons TypeRef ou MemberRef peuvent être recherchés dans l’objet [IMetaDataImport](../metadata/imetadataimport-interface.md) pour l’objet virtuel ICorDebugModule correspondant.|Retourne le code IL dans l’image d’assembly après la fusion.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugProcess6, interface](icordebugprocess6-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
