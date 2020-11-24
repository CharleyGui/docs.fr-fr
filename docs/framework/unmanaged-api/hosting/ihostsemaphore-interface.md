---
title: IHostSemaphore, interface
ms.date: 03/30/2017
api_name:
- IHostSemaphore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSemaphore
helpviewer_keywords:
- IHostSemaphore interface [.NET Framework hosting]
ms.assetid: c0765321-656c-441e-bab5-58176292be1e
topic_type:
- apiref
ms.openlocfilehash: cccbf9a28b16ffee14b3fd3ec43c376109d6ccec
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683054"
---
# <a name="ihostsemaphore-interface"></a>IHostSemaphore, interface

Représente l’implémentation de l’hôte d’un sémaphore pour le Threading.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[ReleaseSemaphore, méthode](ihostsemaphore-releasesemaphore-method.md)|Augmente le nombre de l’instance actuelle de `IHostSemaphore` la valeur spécifiée.|  
|[Wait, méthode](ihostsemaphore-wait-method.md)|Fait en sorte que l' `IHostSemaphore` instance actuelle attende jusqu’à ce qu’elle appartienne ou que la durée spécifiée soit écoulée.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRSyncManager, interface](iclrsyncmanager-interface.md)
- [IHostAutoEvent, interface](ihostautoevent-interface.md)
- [IHostManualEvent, interface](ihostmanualevent-interface.md)
- [IHostSyncManager, interface](ihostsyncmanager-interface.md)
- [Interfaces d'hébergement](hosting-interfaces.md)
