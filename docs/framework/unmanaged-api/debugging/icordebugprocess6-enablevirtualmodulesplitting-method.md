---
title: ICorDebugProcess6::EnableVirtualModuleSplitting, méthode
ms.date: 03/30/2017
ms.assetid: e7733bd3-68da-47f9-82ef-477db5f2e32d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f0f4a1de47670c59f2794feecd0be301a68b8724
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64613794"
---
# <a name="icordebugprocess6enablevirtualmodulesplitting-method"></a>ICorDebugProcess6::EnableVirtualModuleSplitting, méthode
Active ou désactive le fractionnement de module virtuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnableVirtualModuleSplitting(  
   BOOL enableSplitting  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `enableSplitting`  
 `true` pour activer le fractionnement de module virtuel ; `false` pour le désactiver.  
  
## <a name="remarks"></a>Notes  
 Les causes de fractionnement de module virtuel [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) pour reconnaître des modules qui ont été fusionnés lors de la génération, traitement et les présentent en tant que groupe de modules distincts plutôt qu’un seul module de grande taille. Cette opération modifie le comportement de divers [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) méthodes décrites ci-dessous.  
  
> [!NOTE]
>  Cette méthode est uniquement disponible avec .NET Native.  
  
 Cette méthode peut être appelée et la valeur de `enableSplitting` peut être modifiée à tout moment. Cela n’entraîne pas de modifications fonctionnelles avec état dans un [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) objet, autre que la modification du comportement des méthodes répertoriées dans le [fractionnement de module virtuel et les API de débogage non managés](#APIs) section à la fois qu’elles sont appelées. L'utilisation de modules virtuels entraîne une baisse des performances lors de l'appel de ces méthodes. En outre, significative en mémoire de mise en cache de métadonnées virtualisées être amené à implémenter correctement le [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) API et ces caches peuvent être conservées, même après le fractionnement de module virtuel a été désactivé.  
  
## <a name="terminology"></a>Terminologie  
 Les termes suivants sont employés dans le cadre du fractionnement de module virtuel :  
  
 modules conteneurs ou conteneurs  
 Modules d'agrégation.  
  
 sous-modules ou modules virtuels  
 Modules trouvés dans un conteneur.  
  
 modules standards  
 Modules non fusionnés au moment de la génération. Ce ne sont ni des modules conteneurs ni des sous-modules.  
  
 Les modules conteneurs et les sous-modules sont représentés par les objets d’interface ICorDebugModule. Toutefois, le comportement de l’interface est légèrement différent dans chaque cas, comme le \<x-ref à la section > décrit la section.  
  
## <a name="modules-and-assemblies"></a>Modules et assemblys  
 Les assemblys composés de plusieurs modules ne sont pas pris en charge dans le cadre de la fusion d'assemblys, où il existe une relation un-à-un entre un module et un assembly. Chaque objet ICorDebugModule, qu’elle représente un module conteneur ou un sous-module, a un objet ICorDebugAssembly correspondant. Le [ICorDebugModule::GetAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md) méthode convertit à partir du module à l’assembly. Pour mapper dans l’autre sens, le [ICorDebugAssembly::EnumerateModules](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md) méthode énumère uniquement 1 module. Comme l'assembly et le module forment ici une paire fortement couplée, les termes assembly et module sont largement interchangeables.  
  
## <a name="behavioral-differences"></a>Différences comportementales  
 Les modules conteneurs présentent les comportements et caractéristiques suivants :  
  
- Leurs métadonnées pour tous les sous-modules constitutifs sont fusionnées.  
  
- Leurs noms de type peuvent être altérés.  
  
- Le [ICorDebugModule::GetName](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md) méthode retourne le chemin d’accès à un module sur le disque.  
  
- Le [ICorDebugModule::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md) méthode retourne la taille de cette image.  
  
- La méthode ICorDebugAssembly3.EnumerateContainedAssemblies répertorie les sous-modules.  
  
- La méthode ICorDebugAssembly3.GetContainerAssembly retourne `S_FALSE`.  
  
 Les sous-modules présentent les comportements et caractéristiques suivants :  
  
- Ils comportent un jeu réduit de métadonnées qui correspond uniquement à l’assembly d’origine ayant été fusionné.  
  
- Les noms des métadonnées ne sont pas altérés.  
  
- Les jetons de métadonnées ne correspondent généralement pas aux jetons présents dans l’assembly d’origine avant sa fusion au moment de la génération.  
  
- Le [ICorDebugModule::GetName](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md) méthode retourne le nom de l’assembly, pas un chemin d’accès de fichier.  
  
- Le [ICorDebugModule::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md) méthode retourne la taille d’image non fusionnée d’origine.  
  
- La méthode ICorDebugModule3.EnumerateContainedAssemblies retourne `S_FALSE`.  
  
- La méthode ICorDebugAssembly3.GetContainerAssembly retourne le module conteneur.  
  
## <a name="interfaces-retrieved-from-modules"></a>Interfaces récupérées des modules  
 Diverses interfaces peuvent être créées ou récupérées à partir des modules. Certaines interfaces incluent :  
  
- Un objet ICorDebugClass, qui est retourné par la [ICorDebugModule::GetClassFromToken](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md) (méthode).  
  
- Un objet ICorDebugAssembly, qui est retourné par la [ICorDebugModule::GetAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md) (méthode).  
  
 Ces objets sont toujours mis en cache par [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md), et ont la même identité de pointeur qu’ils ont été créés ou interrogées à partir du module conteneur ou un sous-module. Le sous-module présente une vue filtrée de ces objets mis en cache, pas un cache distinct avec ses propres copies.  
  
<a name="APIs"></a>   
## <a name="virtual-module-splitting-and-the-unmanaged-debugging-apis"></a>Fractionnement de module virtuel et API de débogage non managées  
 Le tableau suivant montre de quelle manière le fractionnement de module virtuel modifie le comportement d'autres méthodes dans l'API de débogage non managée.  
  
|Méthode|`enableSplitting` = `true`|`enableSplitting` = `false`|  
|------------|---------------------------------|----------------------------------|  
|[ICorDebugFunction::GetModule](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|Retourne le sous-module dans lequel cette fonction a été initialement définie.|Retourne le module conteneur dans lequel cette fonction a été fusionnée.|  
|[ICorDebugClass::GetModule](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|Retourne le sous-module dans lequel cette classe a été initialement définie.|Retourne le module conteneur dans lequel cette classe a été fusionnée.|  
|ICorDebugModuleDebugEvent::GetModule|Retourne le module conteneur qui a été chargé. Les sous-modules ne reçoivent pas d'événements de chargement, indépendamment de la valeur de ce paramètre.|Retourne le module conteneur qui a été chargé.|  
|[ICorDebugAppDomain::EnumerateAssemblies](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|Retourne une liste des sous-assemblys et des assemblys standards. La liste n'inclut pas les assemblys conteneurs. **Remarque :**  Si un assembly conteneur ne contient pas tous les symboles nécessaires, aucun de ses sous-assemblys ne sera énuméré. S'il manque des symboles dans un assembly standard, celui-ci pourra ou non être énuméré, en fonction des cas.|Retourne une liste des assemblys conteneurs et des assemblys standards. La liste n'inclut pas les sous-assemblys. **Remarque :**  S'il manque des symboles dans un assembly standard, celui-ci pourra ou non être énuméré, en fonction des cas.|  
|[ICorDebugCode::GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md) (lors de la référence au code IL uniquement)|Retourne le code IL qui serait valide dans une image d’assembly avant la fusion. En particulier, les jetons de métadonnées inline doivent être des jetons TypeRef ou MemberRef quand les types référencés ne sont pas définis dans le module virtuel qui contient le code IL. Ces jetons TypeRef ou MemberRef peuvent être recherchés le [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) objet pour l’objet ICorDebugModule virtuel correspondant.|Retourne le code IL dans l’image d’assembly après la fusion.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugProcess6, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
