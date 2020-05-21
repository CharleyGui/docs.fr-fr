---
title: ICLRTask, interface
ms.date: 03/30/2017
api_name:
- ICLRTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask
helpviewer_keywords:
- ICLRTask interface [.NET Framework hosting]
ms.assetid: b3a44df3-578a-4451-b55e-70c8e7695f5e
topic_type:
- apiref
ms.openlocfilehash: 419baaf64397830ef86cfd9e5c3437e3f5b57795
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763005"
---
# <a name="iclrtask-interface"></a>ICLRTask, interface
Fournit des méthodes qui permettent à l’hôte de faire des demandes du common language runtime (CLR) ou de fournir une notification au CLR sur la tâche associée.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Abort, méthode](iclrtask-abort-method.md)|Demande que le CLR abandonne la tâche représentée par l' `ICLRTask` instance actuelle.|  
|[ExitTask, méthode](iclrtask-exittask-method.md)|Notifie le CLR que la tâche associée à l' `ICLRTask` instance actuelle se termine et tente d’arrêter la tâche correctement.|  
|[GetMemStats, méthode](iclrtask-getmemstats-method.md)|Obtient des informations statistiques sur l’utilisation des ressources mémoire par la tâche représentée par l' `ICLRTask` instance actuelle.|  
|[LocksHeld, méthode](iclrtask-locksheld-method.md)|Obtient le nombre de verrous actuellement détenus sur la tâche.|  
|[NeedsPriorityScheduling, méthode](iclrtask-needspriorityscheduling-method.md)|Obtient une valeur indiquant si l’hôte doit assigner une priorité élevée pour replanifier la tâche représentée par l' `ICLRTask` instance actuelle.|  
|[Reset, méthode](iclrtask-reset-method.md)|Informe le CLR que l’hôte a terminé une tâche et permet au CLR de réutiliser l' `ICLRTask` instance actuelle pour représenter une autre tâche.|  
|[RudeAbort, méthode](iclrtask-rudeabort-method.md)|Force le CLR à abandonner immédiatement la tâche représentée par l' `ICLRTask` instance actuelle, sans garantir que les finaliseurs seront exécutés.|  
|[SetTaskIdentifier, méthode](iclrtask-settaskidentifier-method.md)|Définit un identificateur unique pour la tâche représentée par l’instance actuelle `ICLRTask` , à utiliser lors du débogage.|  
|[SwitchIn, méthode](iclrtask-switchin-method.md)|Notifie le CLR que la tâche représentée par l' `ICLRTask` instance actuelle est dans un état opérationnel.|  
|[SwitchOut, méthode](iclrtask-switchout-method.md)|Notifie le CLR que la tâche représentée par l' `ICLRTask` instance actuelle n’est plus dans un état opérationnel.|  
|[YieldTask, méthode](iclrtask-yieldtask-method.md)|Demande que le CLR rende le temps processeur disponible pour d’autres tâches. Le CLR ne garantit pas que la tâche sera placée dans un État où elle peut générer du temps de traitement.|  
  
## <a name="remarks"></a>Notes  
 Un `ICLRTask` est la représentation d’une tâche pour le CLR. À tout moment pendant l’exécution du code, une tâche peut être décrite comme en cours d’exécution ou en attente d’exécution. L’hôte appelle la `ICLRTask::SwitchIn` méthode pour informer le CLR que la tâche représentée par l' `ICLRTask` instance actuelle est désormais dans un état de fonctionnement. Après un appel à `ICLRTask::SwitchIn` , l’hôte peut planifier la tâche sur n’importe quel thread de système d’exploitation, sauf dans les cas où le runtime requiert l’affinité de thread, comme spécifié par les appels aux méthodes [IHostTaskManager :: BeginThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md) et [IHostTaskManager :: EndThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md) . Un certain temps plus tard, le système d’exploitation peut décider de supprimer la tâche du thread et de la placer dans un état de non-exécution. Par exemple, cela peut se produire chaque fois que la tâche bloque sur les primitives de synchronisation, ou attend la fin des opérations d’e/s. L’hôte appelle [SwitchOut](iclrtask-switchout-method.md) pour informer le CLR que la tâche représentée par l' `ICLRTask` instance actuelle n’est plus dans un état opérationnel.  
  
 Une tâche se termine généralement à la fin de l’exécution du code. À ce moment-là, l’hôte appelle `ICLRTask::ExitTask` pour détruire le associé `ICLRTask` . Toutefois, les tâches peuvent également être recyclées à l’aide d’un appel à `ICLRTask::Reset` , ce qui permet `ICLRTask` à l’instance d’être réutilisée. Cette approche empêche la surcharge liée à la création et à la destruction répétées d’instances.  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRTaskManager, interface](iclrtaskmanager-interface.md)
- [IHostTask, interface](ihosttask-interface.md)
- [IHostTaskManager, interface](ihosttaskmanager-interface.md)
- [Interfaces d'hébergement](hosting-interfaces.md)
- [ICLRTask2, interface](iclrtask2-interface.md)
