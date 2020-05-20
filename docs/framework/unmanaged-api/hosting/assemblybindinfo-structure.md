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
ms.openlocfilehash: 615637813b08629aaea74b23fa2737f52d61bafb
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616916"
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
|`dwAppDomainId`|Identificateur unique pour le `IStream` retourné par un appel à [IHostAssemblyStore ::P rovideassembly](ihostassemblystore-provideassembly-method.md), à partir duquel l’assembly référencé doit être chargé.|  
|`lpReferencedIdentity`|Identificateur unique de l’assembly référencé.|  
|`lpPostPolicyIdentity`|Identificateur de l’assembly référencé après l’application des valeurs de stratégie de liaison.|  
|`ePolicyLevel`|L’une des valeurs [EPolicyAction](epolicyaction-enumeration.md) qui indiquent les stratégies de contrôle de version, le cas échéant, qui doivent être appliquées à l’assembly référencé.|  
  
## <a name="remarks"></a>Notes  
 L’hôte fournit l’identificateur unique `dwAppDomainId` au Common Language Runtime (CLR). Après qu’un appel à `IHostAssemblyStore::ProvideAssembly` retourne, le runtime utilise l’identificateur pour déterminer si le contenu du `IStream` a été mappé. Dans ce cas, le runtime charge la copie existante au lieu de remapper le flux. Le runtime utilise également cet identificateur comme clé de recherche pour les flux retournés par les appels à [IHostAssemblyStore ::P rovidemodule](ihostassemblystore-providemodule-method.md). Par conséquent, l’identificateur doit être unique pour les demandes de module et pour les demandes d’assembly.  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. idl  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures d'hébergement](hosting-structures.md)
- [ICLRAssemblyIdentityManager, interface](iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList, interface](iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager, interface](ihostassemblymanager-interface.md)
- [IHostAssemblyStore, interface](ihostassemblystore-interface.md)
- [ModuleBindInfo, structure](modulebindinfo-structure.md)
