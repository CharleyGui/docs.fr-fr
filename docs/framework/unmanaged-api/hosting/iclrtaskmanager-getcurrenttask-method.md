---
title: ICLRTaskManager::GetCurrentTask, méthode
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.GetCurrentTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::GetCurrentTask
helpviewer_keywords:
- GetCurrentTask method, ICLRTaskManager interface [.NET Framework hosting]
- ICLRTaskManager::GetCurrentTask method [.NET Framework hosting]
ms.assetid: c0b82a9f-edc6-4878-9c81-48de53c02142
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9996b1a84a5f095cf12d74d0c6f594911e7a7788
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67770201"
---
# <a name="iclrtaskmanagergetcurrenttask-method"></a>ICLRTaskManager::GetCurrentTask, méthode
Obtient le [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance en cours d’exécution sur le thread de système d’exploitation d'où provenance l’appel de méthode.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCurrentTask (  
    [out] ICLRTask **ppTask  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ppTask`  
 [out] Un pointeur vers l’adresse d’un `ICLRTask` instance en cours d’exécution sur le thread de système d’exploitation à partir duquel provient l’appel, ou null si aucune tâche n’est en cours d’exécution sur ce thread.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La méthode a été retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.|  
|HOST_E_TIMEOUT|L’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Notes  
 Le `ICLRTask` de l’instance qui le `ppTask` paramètre pointe représente la tâche en cours d’exécution pour le CLR. Le `ICLRTask` instance est associée à un correspondant [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance qui représente la tâche pour l’hôte.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRTask, interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask, interface](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
