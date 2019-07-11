---
title: EMemoryCriticalLevel, énumération
ms.date: 03/30/2017
api_name:
- EMemoryCriticalLevel
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EMemoryCriticalLevel
helpviewer_keywords:
- EMemoryCriticalLevel enumeration [.NET Framework hosting]
ms.assetid: 2ca8a7a2-7b54-4ba3-8e73-277c7df485f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 26b3761ab49f36c5f687ff2c62882667e044d299
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774219"
---
# <a name="ememorycriticallevel-enumeration"></a>EMemoryCriticalLevel, énumération
Contient des valeurs qui indiquent l’impact d’un échec lors de l’allocation de mémoire spécifique a été demandée mais ne peut pas être satisfaite.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    eTaskCritical      = 0,  
    eAppDomainCritical = 1,  
    eProcessCritical   = 2  
} EMemoryCriticalLevel;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`eAppDomainCritical`|Indique que l’allocation est critique pour l’exécution de code managé dans le domaine qui a demandé l’allocation. Si la mémoire ne peut pas être allouée, le CLR ne garantit pas que le domaine est toujours utilisable. L’hôte décide d’action à entreprendre lorsque l’allocation ne peut pas être satisfaite. Il peut indiquer au CLR pour abandonner la `AppDomain` automatiquement, ou lui permettre de poursuivre son exécution en appelant des méthodes sur [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).|  
|`eProcessCritical`|Indique que l’allocation est critique pour l’exécution du code managé dans le processus. Cette valeur est utilisée lors du démarrage et lors de l’exécution des finaliseurs. Si la mémoire ne peut pas être allouée, le CLR ne peut pas fonctionner dans le processus. Si l’allocation échoue, le CLR est désactivé. Tous les appels ultérieurs dans le CLR échouent avec HOST_E_CLRNOTAVAILABLE.|  
|`eTaskCritical`|Indique que l’allocation est critique pour l’exécution de la tâche qui a demandé l’allocation. Si la mémoire ne peut pas être allouée, le CLR ne garantit pas que la tâche peut être exécutée. En cas de défaillance, le CLR lève une <xref:System.Threading.ThreadAbortException> sur le thread de système d’opération physique.|  
  
## <a name="remarks"></a>Notes  
 Les méthodes d’allocation de mémoire définies dans le [IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md) et [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) interfaces prennent un paramètre de ce type. Selon la gravité d’une défaillance, un hôte peut décider à échouer la demande d’allocation immédiatement ou attendre jusqu'à ce qu’il peut être satisfaite.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** MSCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRMemoryNotificationCallback, interface](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
- [Énumérations d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
