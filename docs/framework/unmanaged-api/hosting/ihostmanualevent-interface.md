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
ms.openlocfilehash: 50e37b770e3ee6e0a5cdfca61fc5b09749e5735f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673196"
---
# <a name="ihostmanualevent-interface"></a>IHostManualEvent, interface

Fournit l’implémentation de l’hôte d’une représentation d’un événement de réinitialisation manuelle.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Reset, méthode](ihostmanualevent-reset-method.md)|Rétablit l' `IHostManualEvent` État non signalé de l’instance actuelle.|  
|[Set, méthode](ihostmanualevent-set-method.md)|Définit l' `IHostManualEvent` état signalé de l’instance actuelle.|  
|[Wait, méthode](ihostmanualevent-wait-method.md)|Fait en sorte que l' `IHostManualEvent` instance actuelle attende jusqu’à ce qu’elle appartienne ou qu’un laps de temps spécifié se soit écoulé.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRSyncManager, interface](iclrsyncmanager-interface.md)
- [IHostAutoEvent, interface](ihostautoevent-interface.md)
- [IHostSemaphore, interface](ihostsemaphore-interface.md)
- [IHostSyncManager, interface](ihostsyncmanager-interface.md)
- [Interfaces d'hébergement](hosting-interfaces.md)
