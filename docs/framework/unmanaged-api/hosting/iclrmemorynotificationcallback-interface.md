---
title: ICLRMemoryNotificationCallback, interface
ms.date: 03/30/2017
api_name:
- ICLRMemoryNotificationCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMemoryNotificationCallback
helpviewer_keywords:
- ICLRMemoryNotificationCallback interface [.NET Framework hosting]
ms.assetid: 873639e2-4837-4568-83b3-4493e67e4174
topic_type:
- apiref
ms.openlocfilehash: 5762a354bec485cb382b5460dfd2a337f79bee1a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689535"
---
# <a name="iclrmemorynotificationcallback-interface"></a>ICLRMemoryNotificationCallback, interface

Permet à l’hôte de signaler des conditions de sollicitation de la mémoire à l’aide d’une approche similaire à celle de la `CreateMemoryResourceNotification` fonction Win32.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[OnMemoryNotification, méthode](iclrmemorynotificationcallback-onmemorynotification-method.md)|Notifie le common language runtime (CLR) de la charge de mémoire sur l’ordinateur.|  
  
## <a name="remarks"></a>Remarques  

 L’hôte utilise l' `ICLRMemoryNotificationCallback` interface pour demander que le CLR libère des ressources mémoire.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IHostMemoryManager, interface](ihostmemorymanager-interface.md)
- [Interfaces d'hébergement](hosting-interfaces.md)
