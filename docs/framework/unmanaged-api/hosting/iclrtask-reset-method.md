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
ms.openlocfilehash: b87bc026a2cac2d0b913128c43142d56aee03025
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725194"
---
# <a name="iclrtaskreset-method"></a>ICLRTask::Reset, méthode

Informe le common language runtime (CLR) que l’hôte a terminé une tâche et permet au CLR de réutiliser l’instance d' [ICLRTask](iclrtask-interface.md) actuelle pour représenter une autre tâche.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Reset (  
    [in] BOOL fFull  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `fFull`  
 [in] `true` , si le runtime doit réinitialiser toutes les valeurs statiques liées aux threads en plus des informations de sécurité et de paramètres régionaux associées à l' `ICLRTask` instance actuelle ; sinon, `false` .  
  
 Si la valeur est `true` , le runtime réinitialise les données stockées à l’aide <xref:System.Threading.Thread.AllocateDataSlot%2A> de ou de <xref:System.Threading.Thread.AllocateNamedDataSlot%2A> .  
  
## <a name="return-value"></a>Valeur renvoyée  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`Reset` retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter l’appel. correctement|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Remarques  

 Le CLR peut recycler les `ICLRTask` instances créées précédemment pour éviter la surcharge liée à la création répétée de nouvelles instances chaque fois qu’il a besoin d’une nouvelle tâche. L’hôte active cette fonctionnalité en appelant `ICLRTask::Reset` au lieu de [ICLRTask :: ExitTask](iclrtask-exittask-method.md) lorsqu’il a terminé une tâche. La liste suivante résume le cycle de vie normal d’une `ICLRTask` instance :  
  
1. Le runtime crée une nouvelle `ICLRTask` instance.  
  
2. Le runtime appelle [IHostTaskManager :: GetCurrentTask,](ihosttaskmanager-getcurrenttask-method.md) pour obtenir une référence à la tâche hôte actuelle.  
  
3. Le runtime appelle [IHostTask :: SetCLRTask,](ihosttask-setclrtask-method.md) pour associer la nouvelle instance à la tâche hôte.  
  
4. La tâche s’exécute et se termine.  
  
5. L’hôte détruit la tâche en appelant `ICLRTask::ExitTask` .  
  
 `Reset` modifie ce scénario de deux façons. À l’étape 5 ci-dessus, l’hôte appelle `Reset` pour réinitialiser la tâche à un état propre, puis découple l' `ICLRTask` instance de l’instance [IHostTask](ihosttask-interface.md) qui lui est associée. Si vous le souhaitez, l’hôte peut également mettre en cache l' `IHostTask` instance en vue de sa réutilisation. À l’étape 1 ci-dessus, le runtime extrait un recyclé du `ICLRTask` cache au lieu de créer une nouvelle instance.  
  
 Cette approche fonctionne bien lorsque l’hôte possède également un pool de tâches de travail réutilisables. Lorsque l’hôte détruit l’une de ses `IHostTask` instances, il détruit le correspondant `ICLRTask` en appelant `ExitTask` .  
  
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
