---
title: IHostTaskManager, interface
ms.date: 03/30/2017
api_name:
- IHostTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager
helpviewer_keywords:
- IHostTaskManager interface [.NET Framework hosting]
ms.assetid: 4a0b05b9-3ef1-4607-b7c8-bd4dd43647a0
topic_type:
- apiref
ms.openlocfilehash: 470e2ac06f433dc12d66f6cac97337a6de1d8183
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133019"
---
# <a name="ihosttaskmanager-interface"></a>IHostTaskManager, interface
Fournit des méthodes qui permettent au common language runtime (CLR) d’utiliser des tâches via l’hôte au lieu d’utiliser le thread de système d’exploitation standard ou les fonctions Fiber.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[BeginDelayAbort, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md)|Indique à l’hôte que le code managé entre dans une période dans laquelle la tâche en cours ne doit pas être abandonnée.|  
|[BeginThreadAffinity, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md)|Indique à l’hôte que le code managé entre dans une période dans laquelle la tâche actuelle ne doit pas être déplacée vers un autre thread de système d’exploitation.|  
|[CallNeedsHostHook, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-callneedshosthook-method.md)|Permet à l’hôte de spécifier si l’common language runtime peut incorporer l’appel spécifié à une fonction non managée.|  
|[CreateTask, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md)|Demande que l’hôte crée une nouvelle tâche.|  
|[EndDelayAbort, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md)|Indique à l’hôte que le code managé quitte la période pendant laquelle la tâche en cours ne doit pas être abandonnée, à la suite d’un appel antérieur à `BeginDelayAbort`.|  
|[EndThreadAffinity, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md)|Indique à l’hôte que le code managé sort de la période pendant laquelle la tâche actuelle ne doit pas être déplacée vers un autre thread de système d’exploitation, à la suite d’un appel antérieur à `BeginThreadAffinity`.|  
|[EnterRuntime, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)|Avertit l’hôte qu’un appel à une méthode non managée, tel qu’une méthode d’appel de code non managé, retourne le contrôle d’exécution au CLR.|  
|[GetCurrentTask, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md)|Obtient un pointeur d’interface vers la tâche en cours d’exécution sur le thread de système d’exploitation à partir duquel cet appel est effectué.|  
|[GetStackGuarantee, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getstackguarantee-method.md)|Obtient la quantité d’espace de pile dont la disponibilité est garantie après la fin d’une opération de pile, mais avant la fermeture d’un processus.|  
|[LeaveRuntime, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)|Avertit l’hôte que le code managé va effectuer un appel à une fonction non managée.|  
|[ReverseEnterRuntime, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)|Indique à l’hôte qu’un appel est effectué dans le common language runtime (CLR) à partir du code non managé.|  
|[ReverseLeaveRuntime, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md)|Avertit l’hôte que le contrôle quitte le CLR et entre une fonction non managée qui a été, à son tour, appelée à partir du code managé.|  
|[SetCLRTaskManager, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setclrtaskmanager-method.md)|Fournit à l’hôte un pointeur d’interface vers une instance [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) implémentée par le CLR.|  
|[SetLocale, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setlocale-method.md)|Avertit l’hôte que le CLR a modifié les paramètres régionaux de la tâche actuelle.|  
|[SetStackGuarantee, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setstackguarantee-method.md)|Réservé à un usage interne uniquement.|  
|[SetUILocale, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setuilocale-method.md)|Avertit l’hôte que les paramètres régionaux de l’interface utilisateur ont été modifiés sur la tâche actuelle.|  
|[Sleep, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md)|Indique à l’hôte que la tâche en cours va se mettre en veille.|  
|[SwitchToTask, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md)|Indique à l’hôte qu’il doit extraire la tâche actuelle.|  
  
## <a name="remarks"></a>Notes  
 `IHostTaskManager` permet au CLR de créer et de gérer des tâches, de fournir des raccordements pour que l’hôte prenne des mesures lorsque le contrôle est transféré du code managé au code non managé, et vice versa, et de spécifier certaines actions que l’hôte peut et ne peut pas prendre pendant l’exécution du code.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRTask, interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask, interface](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [Interfaces d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
