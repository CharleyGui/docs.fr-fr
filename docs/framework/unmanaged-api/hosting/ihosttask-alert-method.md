---
title: IHostTask::Alert, méthode
ms.date: 03/30/2017
api_name:
- IHostTask.Alert
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::Alert
helpviewer_keywords:
- IHostTask::Alert method [.NET Framework hosting]
- Alert method, IHostTask interface [.NET Framework hosting]
ms.assetid: 5245d4b5-b6c3-48df-9cb9-8caf059f43fb
topic_type:
- apiref
ms.openlocfilehash: 5a4870a4472081a78cd1fade51f441c22aa5eb48
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720475"
---
# <a name="ihosttaskalert-method"></a>IHostTask::Alert, méthode

Demande que l’hôte réactive la tâche représentée par l’instance [IHostTask](ihosttask-interface.md) actuelle, afin que la tâche puisse être abandonnée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Alert ();  
```  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|Retour réussi de la méthode.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Remarques  

 Le CLR appelle la `Alert` méthode quand <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> est appelé à partir du code utilisateur ou lorsque le <xref:System.AppDomain> associé à l’objet actuel <xref:System.Threading.Thread> s’arrête. L’hôte doit être retourné immédiatement, car l’appel est effectué de façon asynchrone. Si l’hôte ne peut pas alerter la tâche immédiatement, il doit se réveiller la prochaine fois qu’il entre dans un État dans lequel il peut être alerté.  
  
> [!NOTE]
> `Alert` affecte uniquement les tâches auxquelles le runtime a passé une [WAIT_OPTION](wait-option-enumeration.md) valeur de WAIT_ALERTABLE à des méthodes telles que [join](ihosttask-join-method.md).  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRTask, interface](iclrtask-interface.md)
- [ICLRTaskManager, interface](iclrtaskmanager-interface.md)
- [IHostTask, interface](ihosttask-interface.md)
- [IHostTaskManager, interface](ihosttaskmanager-interface.md)
