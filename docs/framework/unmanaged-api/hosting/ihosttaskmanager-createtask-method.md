---
title: IHostTaskManager::CreateTask, méthode
ms.date: 03/30/2017
api_name:
- IHostTaskManager.CreateTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::CreateTask
helpviewer_keywords:
- CreateTask method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::CreateTask method [.NET Framework hosting]
ms.assetid: a6f8ad36-61e1-42b0-9db2-add575646d18
topic_type:
- apiref
ms.openlocfilehash: fef2f56fd000a8610a40661a30aa306ae5a7884e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178000"
---
# <a name="ihosttaskmanagercreatetask-method"></a>IHostTaskManager::CreateTask, méthode
Demande que l’hôte crée une nouvelle tâche.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateTask (  
    [in]  DWORD stacksize,
    [in]  LPTHREAD_START_ROUTINE pStartAddress,  
    [in]  PVOID pParameter,  
    [out] IHostTask **ppTask  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `stacksize`  
 [dans] La taille demandée, dans les octets, de la pile demandée, ou 0 (zéro) pour la taille par défaut.  
  
 `pStartAddress`  
 [dans] Un pointeur à la fonction de la tâche est d’exécuter.  
  
 `pParameter`  
 [dans] Un pointeur sur les données de l’utilisateur à transmettre à la fonction, ou nul si la fonction ne prend aucun paramètre.  
  
 `ppTask`  
 [out] Un pointeur à l’adresse d’une instance [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) créé par l’hôte, ou nul si la tâche ne peut pas être créée. La tâche reste dans un état suspendu jusqu’à ce qu’il soit explicitement commencé par un appel à [IHostTask::Démarrer](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`CreateTask`retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|L’heure courante de l’exécution de la langue (CLR) n’a pas été chargée dans un processus, ou le CLR est dans un état où il ne peut pas exécuter le code géré ou traiter l’appel avec succès.|  
|HOST_E_TIMEOUT|L’appel s’est fait chronométrer.|  
|HOST_E_NOT_OWNER|L’appelant n’est pas propriétaire de la serrure.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un fil bloqué ou une fibre l’attendait.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Lorsqu’une méthode revient E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels ultérieurs aux méthodes d’hébergement reviennent HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Pas assez de mémoire était disponible pour créer la tâche demandée.|  
  
## <a name="remarks"></a>Notes   
 Le CLR `CreateTask` appelle à demander à l’hôte de créer une nouvelle tâche. L’hôte renvoie un `IHostTask` pointeur d’interface à une instance. La tâche retournée doit rester suspendue jusqu’à `IHostTask::Start`ce qu’elle soit explicitement commencée par un appel à .  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor  
  
 **Bibliothèque:** Inclus comme une ressource dans MSCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRTask, interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask, interface](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
