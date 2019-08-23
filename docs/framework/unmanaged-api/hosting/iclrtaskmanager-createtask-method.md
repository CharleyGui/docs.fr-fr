---
title: ICLRTaskManager::CreateTask, méthode
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.CreateTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::CreateTask
helpviewer_keywords:
- ICLRTaskManager::CreateTask method [.NET Framework hosting]
- CreateTask method, ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: eea570d9-2e53-4320-9ea0-eb777bf9dcf3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a89ea76d78431ae8833602588379d5150e473710
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938303"
---
# <a name="iclrtaskmanagercreatetask-method"></a>ICLRTaskManager::CreateTask, méthode
Demande explicitement que le common language runtime (CLR) crée une nouvelle tâche.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateTask (  
    [out] ICLRTask **pTask  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pTask`  
 à Pointeur vers l’adresse d’un [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)nouvellement créé, ou null, si la tâche n’a pas pu être créée.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La méthode a été retournée avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|La mémoire disponible est insuffisante pour allouer la ressource demandée.|  
  
## <a name="remarks"></a>Notes  
 Le CLR crée automatiquement une nouvelle tâche lors de l’initialisation, lorsque le code utilisateur crée un thread à l’aide <xref:System.Threading> de types dans l’espace de noms ou lorsque la taille du pool de threads augmente. Elle crée également des tâches lorsque du code non managé effectue un appel à une fonction managée.  
  
 `CreateTask`permet à l’hôte de faire une demande explicite que le CLR crée une nouvelle tâche. Par exemple, l’hôte peut appeler cette méthode pour préinitialiser les structures de données.  
  
> [!IMPORTANT]
> La nouvelle tâche est retournée dans un état suspendu et reste suspendue jusqu’à ce que l’hôte appelle explicitement [IHostTask:: Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRTask, interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask, interface](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
