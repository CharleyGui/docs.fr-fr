---
title: ICLRTask::Reset, méthode
ms.date: 03/30/2017
api_name:
- ICLRTask.Reset
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::Reset
helpviewer_keywords:
- ICLRTask::Reset method [.NET Framework hosting]
- Reset method, ICLRTask interface [.NET Framework hosting]
ms.assetid: 1bfb5d3a-0ffd-4bb4-9bf6-aec00cb675b7
topic_type:
- apiref
ms.openlocfilehash: 17fca3e5a2d763277d3a5f9f72e2d35be6fc350c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124641"
---
# <a name="iclrtaskreset-method"></a>ICLRTask::Reset, méthode
Informe le common language runtime (CLR) que l’hôte a terminé une tâche et permet au CLR de réutiliser l’instance d' [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) actuelle pour représenter une autre tâche.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Reset (  
    [in] BOOL fFull  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `fFull`  
 [in] `true`, si le runtime doit réinitialiser toutes les valeurs statiques liées aux threads en plus des informations de sécurité et de paramètres régionaux relatives à l’instance de `ICLRTask` actuelle ; Sinon, `false`.  
  
 Si la valeur est `true`, le runtime réinitialise les données stockées à l’aide de <xref:System.Threading.Thread.AllocateDataSlot%2A> ou <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`Reset` retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter l’appel. correctement|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Notes  
 Le CLR peut recycler les instances créées précédemment `ICLRTask` pour éviter la surcharge liée à la création de nouvelles instances à plusieurs reprises à chaque fois qu’il a besoin d’une nouvelle tâche. L’hôte active cette fonctionnalité en appelant `ICLRTask::Reset` au lieu de [ICLRTask :: ExitTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md) lorsqu’il a terminé une tâche. La liste suivante résume le cycle de vie normal d’une instance de `ICLRTask` :  
  
1. Le runtime crée une nouvelle instance de `ICLRTask`.  
  
2. Le runtime appelle [IHostTaskManager :: GetCurrentTask,](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md) pour obtenir une référence à la tâche hôte actuelle.  
  
3. Le runtime appelle [IHostTask :: SetCLRTask,](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md) pour associer la nouvelle instance à la tâche hôte.  
  
4. La tâche s’exécute et se termine.  
  
5. L’hôte détruit la tâche en appelant `ICLRTask::ExitTask`.  
  
 `Reset` modifie ce scénario de deux façons. À l’étape 5 ci-dessus, l’hôte appelle `Reset` pour réinitialiser la tâche à un état propre, puis elle découple l’instance de `ICLRTask` de l’instance de la vue [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) qui lui est associée. Si vous le souhaitez, l’hôte peut également mettre en cache l’instance de `IHostTask` en vue de sa réutilisation. À l’étape 1 ci-dessus, le runtime extrait un `ICLRTask` recyclé du cache au lieu de créer une nouvelle instance.  
  
 Cette approche fonctionne bien lorsque l’hôte possède également un pool de tâches de travail réutilisables. Lorsque l’hôte détruit l’une de ses instances de `IHostTask`, il détruit le `ICLRTask` correspondant en appelant `ExitTask`.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRTask, interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask, interface](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
