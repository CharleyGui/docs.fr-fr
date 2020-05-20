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
ms.openlocfilehash: 822b51531b7afc1c824c74b9580d9208e347e13b
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703554"
---
# <a name="iclriocompletionmanager-interface"></a>ICLRIoCompletionManager, interface
Implémente une méthode de rappel qui permet à l’hôte de notifier le common language runtime (CLR) de l’état des demandes d’e/s spécifiées.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[OnComplete, méthode](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)|Notifie le CLR de l’état d’une demande d’e/s qui a été effectuée à l’aide d’un appel à la méthode [IHostIoCompletionManager :: bind](ihostiocompletionmanager-bind-method.md) .|  
  
## <a name="remarks"></a>Notes  
 L’hôte implémente l’abstraction de la fin d’exécution d’e/s à l’aide de l’interface [IHostIoCompletionManager](ihostiocompletionmanager-interface.md) . Le CLR effectue des demandes d’e/s via cette interface, et l’hôte notifie l’exécution du résultat de ces requêtes à l’aide de l' `ICLRIoCompletionManager` interface.  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IHostIoCompletionManager, interface](ihostiocompletionmanager-interface.md)
- [IHostThreadPoolManager, interface](ihostthreadpoolmanager-interface.md)
- [Interfaces d'hébergement](hosting-interfaces.md)
