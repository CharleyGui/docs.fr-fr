---
title: IHostTask, interface
ms.date: 03/30/2017
api_name:
- IHostTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask
helpviewer_keywords:
- IHostTask interface [.NET Framework hosting]
ms.assetid: a71dbbd5-64b8-47eb-9f03-8e8c85fbe2bc
topic_type:
- apiref
ms.openlocfilehash: 10efe853c9a7ad7676058bc01b07063c557623d8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699220"
---
# <a name="ihosttask-interface"></a>IHostTask, interface

Fournit des méthodes qui permettent au common language runtime (CLR) de communiquer avec l’hôte pour gérer des tâches.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Alert, méthode](ihosttask-alert-method.md)|Demande que l’hôte réactive la tâche représentée par l' `IHostTask` instance actuelle, afin que la tâche puisse être abandonnée.|  
|[GetPriority, méthode](ihosttask-getpriority-method.md)|Obtient le niveau de priorité de thread de la tâche représentée par l' `IHostTask` instance actuelle.|  
|[Join, méthode](ihosttask-join-method.md)|Bloque la tâche appelante jusqu’à ce que la tâche représentée par l' `IHostTask` instance actuelle se termine, que l’intervalle de temps spécifié s’écoule, ou que la méthode [IHostTask :: Alert](ihosttask-alert-method.md) soit appelée.|  
|[SetCLRTask, méthode](ihosttask-setclrtask-method.md)|Associe une instance d' [interface ICLRTask](iclrtask-interface.md) à l' `IHostTask` instance actuelle.|  
|[SetPriority, méthode](ihosttask-setpriority-method.md)|Demande que l’hôte ajuste le niveau de priorité de thread pour la tâche représentée par l' `IHostTask` instance actuelle.|  
|[Start, méthode](ihosttask-start-method.md)|Demande que l’hôte déplace la tâche représentée par l' `IHostTask` instance actuelle d’un état suspendu à un état actif, dans lequel le code peut être exécuté.|  
  
## <a name="remarks"></a>Remarques  

 Le CLR appelle des méthodes définies par `IHostTask` pour démarrer une tâche, définir son niveau de priorité de thread, et ainsi de suite.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRTask, interface](iclrtask-interface.md)
- [ICLRTaskManager, interface](iclrtaskmanager-interface.md)
- [IHostTaskManager, interface](ihosttaskmanager-interface.md)
- [Interfaces d'hébergement](hosting-interfaces.md)
