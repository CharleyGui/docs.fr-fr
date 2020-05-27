---
title: IGCThreadControl, interface
ms.date: 03/30/2017
api_name:
- IGCThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCThreadControl
helpviewer_keywords:
- IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 3ff04d75-85ac-4df9-886d-dbaa037c0552
topic_type:
- apiref
ms.openlocfilehash: 78e667acf1573769a1a67b4c964d7801f11838fe
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805125"
---
# <a name="igcthreadcontrol-interface"></a>IGCThreadControl, interface
Fournit des méthodes pour participer à la planification des threads qui seraient sinon bloqués pour un garbage collection.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[SuspensionEnding, méthode](igcthreadcontrol-suspensionending-method.md)|Indique à l’hôte que le runtime reprend les threads après une garbage collection ou une autre suspension.|  
|[SuspensionStarting, méthode](igcthreadcontrol-suspensionstarting-method.md)|Indique à l’hôte que le runtime commence une suspension de thread pour une garbage collection ou une autre suspension.|  
|[ThreadIsBlockingForSuspension, méthode](igcthreadcontrol-threadisblockingforsuspension-method.md)|Avertit l’hôte que le thread qui effectue l’appel est sur le présent bloqué, peut-être pour une garbage collection ou une autre suspension.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces d'hébergement](hosting-interfaces.md)
