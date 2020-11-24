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
ms.openlocfilehash: deb14d291bfd511e8f3534f3c5e32787c259c5e8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673109"
---
# <a name="ihosttaskmanager-interface"></a>IHostTaskManager, interface

Fournit des méthodes qui permettent au common language runtime (CLR) d’utiliser des tâches via l’hôte au lieu d’utiliser le thread de système d’exploitation standard ou les fonctions Fiber.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[BeginDelayAbort, méthode](ihosttaskmanager-begindelayabort-method.md)|Indique à l’hôte que le code managé entre dans une période dans laquelle la tâche en cours ne doit pas être abandonnée.|  
|[BeginThreadAffinity, méthode](ihosttaskmanager-beginthreadaffinity-method.md)|Indique à l’hôte que le code managé entre dans une période dans laquelle la tâche actuelle ne doit pas être déplacée vers un autre thread de système d’exploitation.|  
|[CallNeedsHostHook, méthode](ihosttaskmanager-callneedshosthook-method.md)|Permet à l’hôte de spécifier si l’common language runtime peut incorporer l’appel spécifié à une fonction non managée.|  
|[CreateTask, méthode](ihosttaskmanager-createtask-method.md)|Demande que l’hôte crée une nouvelle tâche.|  
|[EndDelayAbort, méthode](ihosttaskmanager-enddelayabort-method.md)|Indique à l’hôte que le code managé quitte la période pendant laquelle la tâche en cours ne doit pas être abandonnée, à la suite d’un appel antérieur à `BeginDelayAbort` .|  
|[EndThreadAffinity, méthode](ihosttaskmanager-endthreadaffinity-method.md)|Indique à l’hôte que le code managé sort de la période pendant laquelle la tâche actuelle ne doit pas être déplacée vers un autre thread de système d’exploitation, à la suite d’un appel antérieur à `BeginThreadAffinity` .|  
|[EnterRuntime, méthode](ihosttaskmanager-enterruntime-method.md)|Avertit l’hôte qu’un appel à une méthode non managée, tel qu’une méthode d’appel de code non managé, retourne le contrôle d’exécution au CLR.|  
|[GetCurrentTask, méthode](ihosttaskmanager-getcurrenttask-method.md)|Obtient un pointeur d’interface vers la tâche en cours d’exécution sur le thread de système d’exploitation à partir duquel cet appel est effectué.|  
|[GetStackGuarantee, méthode](ihosttaskmanager-getstackguarantee-method.md)|Obtient la quantité d’espace de pile dont la disponibilité est garantie après la fin d’une opération de pile, mais avant la fermeture d’un processus.|  
|[LeaveRuntime, méthode](ihosttaskmanager-leaveruntime-method.md)|Avertit l’hôte que le code managé va effectuer un appel à une fonction non managée.|  
|[ReverseEnterRuntime, méthode](ihosttaskmanager-reverseenterruntime-method.md)|Indique à l’hôte qu’un appel est effectué dans le common language runtime (CLR) à partir du code non managé.|  
|[ReverseLeaveRuntime, méthode](ihosttaskmanager-reverseleaveruntime-method.md)|Avertit l’hôte que le contrôle quitte le CLR et entre une fonction non managée qui a été, à son tour, appelée à partir du code managé.|  
|[SetCLRTaskManager, méthode](ihosttaskmanager-setclrtaskmanager-method.md)|Fournit à l’hôte un pointeur d’interface vers une instance [ICLRTaskManager](iclrtaskmanager-interface.md) implémentée par le CLR.|  
|[SetLocale, méthode](ihosttaskmanager-setlocale-method.md)|Avertit l’hôte que le CLR a modifié les paramètres régionaux de la tâche actuelle.|  
|[SetStackGuarantee, méthode](ihosttaskmanager-setstackguarantee-method.md)|Réservé à un usage interne uniquement.|  
|[SetUILocale, méthode](ihosttaskmanager-setuilocale-method.md)|Avertit l’hôte que les paramètres régionaux de l’interface utilisateur ont été modifiés sur la tâche actuelle.|  
|[Sleep, méthode](ihosttaskmanager-sleep-method.md)|Indique à l’hôte que la tâche en cours va se mettre en veille.|  
|[SwitchToTask, méthode](ihosttaskmanager-switchtotask-method.md)|Indique à l’hôte qu’il doit extraire la tâche actuelle.|  
  
## <a name="remarks"></a>Remarques  

 `IHostTaskManager` permet au CLR de créer et de gérer des tâches, de fournir des raccordements pour que l’hôte prenne des mesures lorsque le contrôle est transféré du code managé au code non managé, et vice versa, et de spécifier certaines actions que l’hôte peut et ne peut pas prendre pendant l’exécution du code.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRTask, interface](iclrtask-interface.md)
- [ICLRTaskManager, interface](iclrtaskmanager-interface.md)
- [IHostTask, interface](ihosttask-interface.md)
- [Interfaces d'hébergement](hosting-interfaces.md)
