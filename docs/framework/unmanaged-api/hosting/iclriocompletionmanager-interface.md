---
title: ICLRIoCompletionManager, interface
ms.date: 03/30/2017
api_name:
- ICLRIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRIoCompletionManager
helpviewer_keywords:
- ICLRIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c6c3ace6-e5e7-4450-8cc5-a9a48208c493
topic_type:
- apiref
ms.openlocfilehash: e23675351e1fd0de510243c9ee8b3a6dd6f29cec
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714118"
---
# <a name="iclriocompletionmanager-interface"></a>ICLRIoCompletionManager, interface

Implémente une méthode de rappel qui permet à l’hôte de notifier le common language runtime (CLR) de l’état des demandes d’e/s spécifiées.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[OnComplete, méthode](iclriocompletionmanager-oncomplete-method.md)|Notifie le CLR de l’état d’une demande d’e/s qui a été effectuée à l’aide d’un appel à la méthode [IHostIoCompletionManager :: bind](ihostiocompletionmanager-bind-method.md) .|  
  
## <a name="remarks"></a>Remarques  

 L’hôte implémente l’abstraction de la fin d’exécution d’e/s à l’aide de l’interface [IHostIoCompletionManager](ihostiocompletionmanager-interface.md) . Le CLR effectue des demandes d’e/s via cette interface, et l’hôte notifie l’exécution du résultat de ces requêtes à l’aide de l' `ICLRIoCompletionManager` interface.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IHostIoCompletionManager, interface](ihostiocompletionmanager-interface.md)
- [IHostThreadPoolManager, interface](ihostthreadpoolmanager-interface.md)
- [Interfaces d'hébergement](hosting-interfaces.md)
