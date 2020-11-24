---
title: IHostAutoEvent, interface
ms.date: 03/30/2017
api_name:
- IHostAutoEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAutoEvent
helpviewer_keywords:
- IHostAutoEvent interface [.NET Framework hosting]
ms.assetid: 6c1d15c1-a80a-4ee9-b1e4-6e859db6575a
topic_type:
- apiref
ms.openlocfilehash: 6893b019c7e86d3f359cf64752d30f7896203786
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680857"
---
# <a name="ihostautoevent-interface"></a>IHostAutoEvent, interface

Fournit une représentation de l’implémentation de l’hôte d’un événement de réinitialisation automatique.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Set, méthode](ihostautoevent-set-method.md)|Définit l' `IHostAutoEvent` état signalé de l’instance actuelle.|  
|[Wait, méthode](ihostautoevent-wait-method.md)|Entraîne l' `IHostAutoEvent` attente de l’instance actuelle jusqu’à ce que l’événement soit détenu ou qu’un laps de temps spécifié se soit écoulé.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRSyncManager, interface](iclrsyncmanager-interface.md)
- [IHostManualEvent, interface](ihostmanualevent-interface.md)
- [IHostSyncManager, interface](ihostsyncmanager-interface.md)
- [Interfaces d'hébergement](hosting-interfaces.md)
