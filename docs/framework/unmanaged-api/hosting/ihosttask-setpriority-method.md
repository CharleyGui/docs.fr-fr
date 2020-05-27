---
title: IHostTask::SetPriority, méthode
ms.date: 03/30/2017
api_name:
- IHostTask.SetPriority
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::SetPriority
helpviewer_keywords:
- IHostTask::SetPriority method [.NET Framework hosting]
- SetPriority method [.NET Framework hosting]
ms.assetid: cd8c379b-c7a0-434f-8e23-899bd26be75d
topic_type:
- apiref
ms.openlocfilehash: ac3a8479cdf05e55885bd55d4e4fb8e6e47686f9
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842396"
---
# <a name="ihosttasksetpriority-method"></a>IHostTask::SetPriority, méthode
Demande que l’hôte ajuste le niveau de priorité de thread pour la tâche représentée par l’instance [IHostTask](ihosttask-interface.md) actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetPriority (  
    [in] int newPriority  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `newPriority`  
 dans Entier qui représente la valeur de priorité de thread demandée pour la tâche représentée par l' `IHostTask` instance actuelle.  
  
## <a name="return-value"></a>Valeur renvoyée  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`SetPriority`retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Remarques  
 Le temps de traitement des threads est accordé à l’aide d’un système de tourniquet (Round Robin) basé en partie sur le niveau de priorité d’un thread. `SetPriority`permet au CLR de définir ce niveau de priorité de thread pour la tâche actuelle. Les `newPriority` valeurs suivantes sont prises en charge.  
  
- THREAD_PRIORITY_ABOVE_NORMAL  
  
- THREAD_PRIORITY_BELOW_NORMAL  
  
- THREAD_PRIORITY_HIGHEST  
  
- THREAD_PRIORITY_IDLE  
  
- THREAD_PRIORITY_LOWEST  
  
- THREAD_PRIORITY_NORMAL  
  
- THREAD_PRIORITY_TIME_CRITICAL  
  
 Le CLR appelle `SetPriority` lorsque la valeur de <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> est modifiée par le code utilisateur. Un hôte peut définir ses propres algorithmes pour l’affectation de priorité de thread et il est libre d’ignorer cette requête.  
  
> [!NOTE]
> `SetPriority`ne signale pas si le niveau de priorité du thread a été modifié. Appelez [IHostTask :: getPriority,](ihosttask-getpriority-method.md) pour déterminer la valeur du niveau de priorité de thread de la tâche.  
  
 Les valeurs de niveau de priorité de thread sont définies par la `SetThreadPriority` fonction Win32. Pour plus d’informations sur la priorité des threads, consultez la documentation de la plateforme Windows.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Threading.Thread>
- [ICLRTask, interface](iclrtask-interface.md)
- [ICLRTaskManager, interface](iclrtaskmanager-interface.md)
- [IHostTask, interface](ihosttask-interface.md)
- [GetPriority, méthode](ihosttask-getpriority-method.md)
- [IHostTaskManager, interface](ihosttaskmanager-interface.md)
