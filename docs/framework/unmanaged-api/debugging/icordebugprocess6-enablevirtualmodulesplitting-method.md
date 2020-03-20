---
title: ICorDebugProcess6::EnableVirtualModuleSplitting, méthode
ms.date: 03/30/2017
ms.assetid: e7733bd3-68da-47f9-82ef-477db5f2e32d
ms.openlocfilehash: 8ad15d11ce81323b30434b3db98259a74a198f29
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178573"
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
  
## <a name="remarks"></a>Notes   
 Le fractionnement virtuel du module fait reconnaître [ICorDebug](icordebug-interface.md) des modules qui ont été fusionnés au cours du processus de construction et les présenter comme un groupe de modules distincts plutôt qu’un seul grand module. Cela change le comportement de diverses méthodes [ICorDebug](icordebug-interface.md) décrites ci-dessous.  
  
> [!NOTE]
> Cette méthode est uniquement disponible avec .NET Native.  
  
 Cette méthode peut être appelée et la valeur de `enableSplitting` peut être modifiée à tout moment. Il ne provoque aucun changement fonctionnel majestueux dans un objet [ICorDebug,](icordebug-interface.md) autre que de modifier le comportement des méthodes énumérées dans le [fractionnement du module virtuel et la section non gestion des API débogage](#APIs) au moment où ils sont appelés. L'utilisation de modules virtuels entraîne une baisse des performances lors de l'appel de ces méthodes. En outre, la mise en cache en mémoire significative des métadonnées virtualisées peut être nécessaire pour implémenter correctement les API [IMetaDataImport,](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) et ces caches peuvent être conservés même après le fractionnement virtuel du module a été désactivé.  
  
## <a name="terminology"></a>Terminologie  
 Les termes suivants sont employés dans le cadre du fractionnement de module virtuel :  
  
 modules conteneurs ou conteneurs  
 Modules d'agrégation.  
  
 sous-modules ou modules virtuels  
 Modules trouvés dans un conteneur.  
  
 modules standards  
 Modules non fusionnés au moment de la génération. Ce ne sont ni des modules conteneurs ni des sous-modules.  
  
 Les modules conteneurs et les sous-modules sont représentés par des objets de l'interface ICorDebugModule. Cependant, le comportement de l’interface est légèrement \<différent dans chaque cas, comme le x-ref à la section> section décrit.  
  
## <a name="modules-and-assemblies"></a>Modules et assemblys  
 Les assemblys composés de plusieurs modules ne sont pas pris en charge dans le cadre de la fusion d'assemblys, où il existe une relation un-à-un entre un module et un assembly. Chaque objet ICorDebugModule, représentant un module conteneur ou un sous-module, est associé à un objet ICorDebugAssembly correspondant. La méthode [ICorDebugModule::GetAssembly](icordebugmodule-getassembly-method.md) méthode convertit du module à l’assemblage. Pour cartographier dans l’autre sens, la méthode [ICorDebugAssembly::EnumerateModules](icordebugassembly-enumeratemodules-method.md) méthode énumère seulement 1 module. Comme l'assembly et le module forment ici une paire fortement couplée, les termes assembly et module sont largement interchangeables.  
  
## <a name="behavioral-differences"></a>Différences de comportement  
 Les modules conteneurs présentent les comportements et caractéristiques suivants :  
  
- Leurs métadonnées pour tous les sous-modules constitutifs sont fusionnées.  
  
- Leurs noms de type peuvent être altérés.  
  
- La méthode [ICorDebugModule::GetName](icordebugmodule-getname-method.md) retourne le chemin vers un module sur disque.  
  
- La méthode [ICorDebugModule::GetSize](icordebugmodule-getsize-method.md) méthode retourne la taille de cette image.  
  
- La méthode ICorDebugAssembly3.EnumerateContainedAssemblies répertorie les sous-modules.  
  
- La méthode ICorDebugAssembly3.GetContainerAssembly retourne `S_FALSE`.  
  
 Les sous-modules présentent les comportements et caractéristiques suivants :  
  
- Ils comportent un jeu réduit de métadonnées qui correspond uniquement à l’assembly d’origine ayant été fusionné.  
  
- Les noms des métadonnées ne sont pas altérés.  
  
- Les jetons de métadonnées ne correspondent généralement pas aux jetons présents dans l’assembly d’origine avant sa fusion au moment de la génération.  
  
- [L’ICorDebugModule::GetName](icordebugmodule-getname-method.md) méthode retourne le nom de l’assemblage, pas un chemin de fichier.  
  
- La méthode [ICorDebugModule::GetSize](icordebugmodule-getsize-method.md) méthode retourne la taille d’image originale nonmétisée.  
  
- La méthode ICorDebugModule3.EnumerateContainedAssemblies retourne `S_FALSE`.  
  
- La méthode ICorDebugAssembly3.GetContainerAssembly retourne le module conteneur.  
  
## <a name="interfaces-retrieved-from-modules"></a>Interfaces récupérées des modules  
 Diverses interfaces peuvent être créées ou récupérées à partir des modules. entres autres :  
  
- Un objet ICorDebugClass, qui est retourné par [l’ICorDebugModule::GetClassFromToken](icordebugmodule-getclassfromtoken-method.md) méthode.  
  
- Un objet ICorDebugAssembly, qui est retourné par [l’ICorDebugModule::GetAssembly](icordebugmodule-getassembly-method.md) méthode.  
  
 Ces objets sont toujours mis en cache par [ICorDebug](icordebug-interface.md), et ils auront la même identité de pointeur indépendamment du fait qu’ils aient été créés ou interrogés à partir du module de conteneur ou d’un sous-module. Le sous-module présente une vue filtrée de ces objets mis en cache, pas un cache distinct avec ses propres copies.  
  
<a name="APIs"></a>
## <a name="virtual-module-splitting-and-the-unmanaged-debugging-apis"></a>Fractionnement de module virtuel et API de débogage non managées  
 Le tableau suivant montre de quelle manière le fractionnement de module virtuel modifie le comportement d'autres méthodes dans l'API de débogage non managée.  
  
|Méthode|`enableSplitting` = `true`|`enableSplitting` = `false`|  
|------------|---------------------------------|----------------------------------|  
|[ICorDebugFunction::GetModule](icordebugfunction-getmodule-method.md)|Retourne le sous-module dans lequel cette fonction a été initialement définie.|Retourne le module conteneur dans lequel cette fonction a été fusionnée.|  
|[ICorDebugClass::GetModule](icordebugclass-getmodule-method.md)|Retourne le sous-module dans lequel cette classe a été initialement définie.|Retourne le module conteneur dans lequel cette classe a été fusionnée.|  
|ICorDebugModuleDebugEvent::GetModule|Retourne le module conteneur qui a été chargé. Les sous-modules ne reçoivent pas d'événements de chargement, indépendamment de la valeur de ce paramètre.|Retourne le module conteneur qui a été chargé.|  
|[ICorDebugAppDomain::EnumerateAssemblies](icordebugappdomain-enumerateassemblies-method.md)|Retourne une liste des sous-assemblys et des assemblys standards. La liste n'inclut pas les assemblys conteneurs. **Note:**  Si un assemblage de conteneurs manque des symboles, aucun de ses sous-assemblages ne sera énuméré. S'il manque des symboles dans un assembly standard, celui-ci pourra ou non être énuméré, en fonction des cas.|Retourne une liste des assemblys conteneurs et des assemblys standards. La liste n'inclut pas les sous-assemblys. **Note:**  Si un assemblage régulier manque des symboles, il peut ou non être énuméré.|  
|[ICorDebugCode::GetCode](icordebugcode-getcode-method.md) (en se référant au code IL seulement)|Retourne le code IL qui serait valide dans une image d’assembly avant la fusion. En particulier, les jetons de métadonnées inline doivent être des jetons TypeRef ou MemberRef quand les types référencés ne sont pas définis dans le module virtuel qui contient le code IL. Ces jetons TypeRef ou MemberRef peuvent être levés dans [l’objet IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) pour l’objet virtuel correspondant ICorDebugModule.|Retourne le code IL dans l’image d’assembly après la fusion.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **.NET Versions-cadre:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugProcess6, interface](icordebugprocess6-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
