---
title: IHostManualEvent, interface
ms.date: 03/30/2017
api_name:
- IHostManualEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent
helpviewer_keywords:
- IHostManualEvent interface [.NET Framework hosting]
ms.assetid: 300c2661-b7d1-4c39-b080-9ebdef0fd523
topic_type:
- apiref
ms.openlocfilehash: 8eba189d6dfca3781c28631a72a9af3c037efeda
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136794"
---
# <a name="ihostmanualevent-interface"></a>IHostManualEvent, interface
Fournit l’implémentation de l’hôte d’une représentation d’un événement de réinitialisation manuelle.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Reset, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md)|Réinitialise l’instance de `IHostManualEvent` actuelle à un État non signalé.|  
|[Set, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-set-method.md)|Définit l’instance de `IHostManualEvent` actuelle à un état signalé.|  
|[Wait, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-wait-method.md)|Entraîne l’attente de l’instance de `IHostManualEvent` actuelle jusqu’à ce qu’elle appartienne ou qu’un laps de temps spécifié se soit écoulé.|  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRSyncManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [IHostAutoEvent, interface](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [IHostSemaphore, interface](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [IHostSyncManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [Interfaces d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
