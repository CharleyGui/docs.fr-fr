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
ms.openlocfilehash: c4f27a73022b0495b2772c0485c14a1b007dc883
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132648"
---
# <a name="iclrtask-interface"></a>ICLRTask, interface
Fournit des méthodes qui permettent à l’hôte de faire des demandes du common language runtime (CLR) ou de fournir une notification au CLR sur la tâche associée.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Abort, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrtask-abort-method.md)|Demande que le CLR abandonne la tâche que l’instance de `ICLRTask` actuelle représente.|  
|[ExitTask, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md)|Notifie le CLR que la tâche associée à l’instance de `ICLRTask` actuelle se termine et tente d’arrêter la tâche correctement.|  
|[GetMemStats, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md)|Obtient des informations statistiques sur l’utilisation des ressources mémoire par la tâche représentée par l’instance de `ICLRTask` actuelle.|  
|[LocksHeld, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrtask-locksheld-method.md)|Obtient le nombre de verrous actuellement détenus sur la tâche.|  
|[NeedsPriorityScheduling, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrtask-needspriorityscheduling-method.md)|Obtient une valeur indiquant si l’hôte doit affecter une priorité élevée pour replanifier la tâche représentée par l’instance de `ICLRTask` actuelle.|  
|[Reset, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrtask-reset-method.md)|Informe le CLR que l’hôte a terminé une tâche et permet au CLR de réutiliser l’instance de `ICLRTask` actuelle pour représenter une autre tâche.|  
|[RudeAbort, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrtask-rudeabort-method.md)|Force le CLR à abandonner immédiatement la tâche représentée par l’instance actuelle de `ICLRTask`, sans garantir que les finaliseurs seront exécutés.|  
|[SetTaskIdentifier, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrtask-settaskidentifier-method.md)|Définit un identificateur unique pour la tâche représentée par l’instance de `ICLRTask` actuelle, à utiliser lors du débogage.|  
|[SwitchIn, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchin-method.md)|Notifie le CLR que la tâche représentée par l’instance de `ICLRTask` actuelle est dans un état opérationnel.|  
|[SwitchOut, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md)|Notifie le CLR que la tâche représentée par l’instance actuelle de `ICLRTask` n’est plus dans un état opérationnel.|  
|[YieldTask, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrtask-yieldtask-method.md)|Demande que le CLR rende le temps processeur disponible pour d’autres tâches. Le CLR ne garantit pas que la tâche sera placée dans un État où elle peut générer du temps de traitement.|  
  
## <a name="remarks"></a>Notes  
 Une `ICLRTask` est la représentation d’une tâche pour le CLR. À tout moment pendant l’exécution du code, une tâche peut être décrite comme en cours d’exécution ou en attente d’exécution. L’hôte appelle la méthode `ICLRTask::SwitchIn` pour notifier le CLR que la tâche représentée par l’instance de `ICLRTask` actuelle est désormais dans un état de fonctionnement. Après un appel à `ICLRTask::SwitchIn`, l’hôte peut planifier la tâche sur n’importe quel thread de système d’exploitation, sauf dans les cas où le runtime requiert l’affinité de thread, comme spécifié par les appels à la fonction [IHostTaskManager :: BeginThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md) et [IHostTaskManager :: Méthodes EndThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md) . Un certain temps plus tard, le système d’exploitation peut décider de supprimer la tâche du thread et de la placer dans un état de non-exécution. Par exemple, cela peut se produire chaque fois que la tâche bloque sur les primitives de synchronisation, ou attend la fin des opérations d’e/s. L’hôte appelle [SwitchOut](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md) pour informer le CLR que la tâche représentée par l’instance actuelle `ICLRTask` n’est plus dans un état opérationnel.  
  
 Une tâche se termine généralement à la fin de l’exécution du code. À ce moment-là, l’hôte appelle `ICLRTask::ExitTask` pour détruire le `ICLRTask`associé. Toutefois, les tâches peuvent également être recyclées à l’aide d’un appel à `ICLRTask::Reset`, ce qui permet de réutiliser l’instance `ICLRTask`. Cette approche empêche la surcharge liée à la création et à la destruction répétées d’instances.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRTaskManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask, interface](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [Interfaces d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [ICLRTask2, interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)
