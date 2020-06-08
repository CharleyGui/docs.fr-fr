---
title: IHostTaskManager::LeaveRuntime, méthode
ms.date: 03/30/2017
api_name:
- IHostTaskManager.LeaveRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::LeaveRuntime
helpviewer_keywords:
- IHostTaskManager::LeaveRuntime method [.NET Framework hosting]
- LeaveRuntime method [.NET Framework hosting]
ms.assetid: 43689cc4-e48e-46e5-a22d-bafd768b8759
topic_type:
- apiref
ms.openlocfilehash: deaebbce3b9b8a26bf9668b826a6818dba94dcc3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501376"
---
# <a name="ihosttaskmanagerleaveruntime-method"></a>IHostTaskManager::LeaveRuntime, méthode
Indique à l’hôte que la tâche en cours d’exécution est sur le point de sortir du common language runtime (CLR) et d’entrer du code non managé.  
  
> [!IMPORTANT]
> Un appel correspondant à [IHostTaskManager :: EnterRuntime](ihosttaskmanager-enterruntime-method.md) avertit l’hôte que la tâche en cours d’exécution est en cours d’entrée dans le code managé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT LeaveRuntime (  
    [in] SIZE_T target  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `target`  
 dans Adresse dans le fichier exécutable portable mappé de la fonction non managée à appeler.  
  
## <a name="return-value"></a>Valeur renvoyée  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`LeaveRuntime`retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|La mémoire disponible est insuffisante pour terminer l’allocation demandée.|  
  
## <a name="remarks"></a>Remarques  
 Les séquences d’appel vers et depuis du code non managé peuvent être imbriquées. Par exemple, la liste ci-dessous décrit une situation hypothétique dans laquelle la séquence d’appels à `LeaveRuntime` , [IHostTaskManager :: ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md), [IHostTaskManager :: ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md), et `IHostTaskManager::EnterRuntime` permet à l’hôte d’identifier les couches imbriquées.  
  
|Action|Appel de méthode correspondant|  
|------------|-------------------------------|  
|Un exécutable Visual Basic managé appelle une fonction non managée écrite en C à l’aide de l’appel de code non managé.|`IHostTaskManager::LeaveRuntime`|  
|La fonction C non managée appelle une méthode dans une DLL managée écrite en C#.|`IHostTaskManager::ReverseEnterRuntime`|  
|La fonction C# managée appelle une autre fonction non managée écrite en C, en utilisant également l’appel de code non managé.|`IHostTaskManager::LeaveRuntime`|  
|La deuxième fonction non managée retourne l’exécution à la fonction C#.|`IHostTaskManager::EnterRuntime`|  
|La fonction C# retourne l’exécution à la première fonction non managée.|`IHostTaskManager::ReverseLeaveRuntime`|  
|La première fonction non managée retourne l’exécution au programme Visual Basic.|`IHostTaskManager::EnterRuntime`|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRTask, interface](iclrtask-interface.md)
- [ICLRTaskManager, interface](iclrtaskmanager-interface.md)
- [IHostTask, interface](ihosttask-interface.md)
- [IHostTaskManager, interface](ihosttaskmanager-interface.md)
