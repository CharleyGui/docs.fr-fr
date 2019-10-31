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
ms.openlocfilehash: ae40d8adaae70ccff6e8058858a506267d58873f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133749"
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
|`dwAppDomainId`|Identificateur unique pour le `IStream` retourné par un appel à la méthode [IHostAssemblyStore ::P rovidemodule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md) à partir de laquelle le module référencé doit être chargé.|  
|`lpAssemblyIdentity`|Identificateur unique de l’assembly qui contient le module référencé.|  
|`lpModuleName`|Nom du module référencé.|  
  
## <a name="remarks"></a>Notes  
 `ModuleBindInfo` est passé en tant que paramètre à `IHostAssemblyStore::ProvideModule`. L’hôte fournit l’identificateur unique `dwAppDomainId` au common language runtime (CLR). Après qu’un appel à la méthode [IHostAssemblyStore ::P rovideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) retourne, le runtime utilise l’identificateur pour déterminer si le contenu du `IStream` a été mappé. Dans ce cas, le runtime charge la copie existante au lieu de remapper le flux. Le runtime utilise également cet identificateur comme clé de recherche pour les flux retournés par les appels à la méthode `IHostAssemblyStore::ProvideAssembly`. Par conséquent, l’identificateur doit être unique pour les requêtes de module, ainsi que pour les demandes d’assembly.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. idl  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [AssemblyBindInfo, structure](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)
- [ICLRAssemblyIdentityManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList, interface](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
