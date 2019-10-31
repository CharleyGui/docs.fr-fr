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
ms.openlocfilehash: 18dfee606f3d41229aa58a5b4bb9380b87c4efa5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121390"
---
# <a name="ihosttask-interface"></a>IHostTask, interface
Fournit des méthodes qui permettent au common language runtime (CLR) de communiquer avec l’hôte pour gérer des tâches.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Alert, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)|Demande que l’hôte réactive la tâche représentée par l’instance de `IHostTask` actuelle, afin que la tâche puisse être abandonnée.|  
|[GetPriority, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)|Obtient le niveau de priorité de thread de la tâche représentée par l’instance de `IHostTask` actuelle.|  
|[Join, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md)|Bloque la tâche appelante jusqu’à ce que la tâche représentée par l’instance de `IHostTask` actuelle se termine, que l’intervalle de temps spécifié s’écoule, ou que la méthode [IHostTask :: Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) soit appelée.|  
|[SetCLRTask, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md)|Associe une instance d' [interface ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) à l’instance de `IHostTask` actuelle.|  
|[SetPriority, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setpriority-method.md)|Demande que l’hôte ajuste le niveau de priorité de thread pour la tâche représentée par l’instance de `IHostTask` actuelle.|  
|[Start, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)|Demande que l’hôte déplace la tâche représentée par l’instance de `IHostTask` actuelle d’un état suspendu à un état actif, dans lequel le code peut être exécuté.|  
  
## <a name="remarks"></a>Notes  
 Le CLR appelle des méthodes définies par `IHostTask` pour démarrer une tâche, définir son niveau de priorité de thread, et ainsi de suite.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRTask, interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTaskManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [Interfaces d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
