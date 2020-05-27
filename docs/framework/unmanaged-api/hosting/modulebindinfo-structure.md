---
title: ModuleBindInfo, structure
ms.date: 03/30/2017
api_name:
- ModuleBindInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ModuleBindInfo
helpviewer_keywords:
- ModuleBindInfo structure [.NET Framework hosting]
ms.assetid: 632d4adc-dbc9-4ce8-9397-abc3285c1c69
topic_type:
- apiref
ms.openlocfilehash: 31be0525c637e50c1161129277d651b56dadfaa3
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006751"
---
# <a name="modulebindinfo-structure"></a>ModuleBindInfo, structure
Fournit des informations détaillées sur le module référencé et l’assembly qui le contient.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _ModuleBindInfo {  
    DWORD    dwAppDomainId;  
    LPCWSTR  lpAssemblyIdentity;  
    LPCWSTR  lpModuleName  
} ModuleBindInfo;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`dwAppDomainId`|Identificateur unique pour le `IStream` retourné par un appel à la méthode [IHostAssemblyStore ::P rovidemodule](ihostassemblystore-providemodule-method.md) à partir de laquelle le module référencé doit être chargé.|  
|`lpAssemblyIdentity`|Identificateur unique de l’assembly qui contient le module référencé.|  
|`lpModuleName`|Nom du module référencé.|  
  
## <a name="remarks"></a>Remarques  
 `ModuleBindInfo`est passé en tant que paramètre à `IHostAssemblyStore::ProvideModule` . L’hôte fournit l’identificateur unique `dwAppDomainId` au Common Language Runtime (CLR). Après qu’un appel à la méthode [IHostAssemblyStore ::P rovideassembly](ihostassemblystore-provideassembly-method.md) retourne, le runtime utilise l’identificateur pour déterminer si le contenu du `IStream` a été mappé. Dans ce cas, le runtime charge la copie existante au lieu de remapper le flux. Le runtime utilise également cet identificateur comme clé de recherche pour les flux retournés par les appels à la `IHostAssemblyStore::ProvideAssembly` méthode. Par conséquent, l’identificateur doit être unique pour les requêtes de module, ainsi que pour les demandes d’assembly.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. idl  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures d'hébergement](hosting-structures.md)
- [AssemblyBindInfo, structure](assemblybindinfo-structure.md)
- [ICLRAssemblyIdentityManager, interface](iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList, interface](iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager, interface](ihostassemblymanager-interface.md)
