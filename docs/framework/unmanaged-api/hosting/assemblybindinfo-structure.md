---
title: AssemblyBindInfo, structure
ms.date: 03/30/2017
api_name:
- AssemblyBindInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyBindInfo
helpviewer_keywords:
- AssemblyBindInfo structure [.NET Framework hosting]
ms.assetid: 6fc01e98-c2e7-49de-ab9f-95937cc89017
topic_type:
- apiref
ms.openlocfilehash: 8764a3d665c997460419561eb168f92ca769c30c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192109"
---
# <a name="assemblybindinfo-structure"></a>AssemblyBindInfo, structure
Fournit des informations détaillées sur l’assembly référencé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _AssemblyBindInfo {  
    DWORD       dwAppDomainId;  
    LPCWSTR     lpReferencedIdentity;  
    LPCWSTR     lpPostPolicyIdentity;  
    DWORD       ePolicyLevel;  
} AssemblyBindInfo;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`dwAppDomainId`|Identificateur unique pour le `IStream` retourné par un appel à [IHostAssemblyStore ::P rovideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md), à partir duquel l’assembly référencé doit être chargé.|  
|`lpReferencedIdentity`|Identificateur unique de l’assembly référencé.|  
|`lpPostPolicyIdentity`|Identificateur de l’assembly référencé après l’application des valeurs de stratégie de liaison.|  
|`ePolicyLevel`|L’une des valeurs [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) qui indiquent les stratégies de contrôle de version, le cas échéant, qui doivent être appliquées à l’assembly référencé.|  
  
## <a name="remarks"></a>Notes  
 L’hôte fournit l’identificateur unique `dwAppDomainId` au common language runtime (CLR). Après qu’un appel à `IHostAssemblyStore::ProvideAssembly` retourne, le runtime utilise l’identificateur pour déterminer si le contenu du `IStream` a été mappé. Dans ce cas, le runtime charge la copie existante au lieu de remapper le flux. Le runtime utilise également cet identificateur comme clé de recherche pour les flux retournés par les appels à [IHostAssemblyStore ::P rovidemodule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md). Par conséquent, l’identificateur doit être unique pour les demandes de module et pour les demandes d’assembly.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. idl  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [ICLRAssemblyIdentityManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList, interface](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [IHostAssemblyStore, interface](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [ModuleBindInfo, structure](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md)
