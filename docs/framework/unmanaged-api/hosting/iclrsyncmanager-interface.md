---
title: ICLRSyncManager, interface
ms.date: 03/30/2017
api_name:
- ICLRSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager
helpviewer_keywords:
- ICLRSyncManager interface [.NET Framework hosting]
ms.assetid: a49f9d80-1c76-4ddd-8c49-34f913a5c596
topic_type:
- apiref
ms.openlocfilehash: b0b9c0b7d178557806a9ab2893bff2d34dc408ff
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557734"
---
# <a name="iclrsyncmanager-interface"></a>ICLRSyncManager, interface
Définit des méthodes qui permettent à l’hôte d’obtenir des informations sur les tâches demandées et de détecter les interblocages dans son implémentation de synchronisation.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[CreateRWLockOwnerIterator, méthode](iclrsyncmanager-createrwlockowneriterator-method.md)|Demande que le common language runtime (CLR) crée un itérateur que l’hôte doit utiliser pour déterminer l’ensemble des tâches en attente sur un verrou de lecteur-writer.|  
|[DeleteRWLockOwnerIterator, méthode](iclrsyncmanager-deleterwlockowneriterator-method.md)|Demande que le CLR détruise un itérateur qui a été créé par un appel à `CreateRWLockOwnerIterator` .|  
|[GetMonitorOwner, méthode](iclrsyncmanager-getmonitorowner-method.md)|Obtient la tâche qui possède l’analyse spécifiée.|  
|[GetRWLockOwnerNext, méthode](iclrsyncmanager-getrwlockownernext-method.md)|Obtient la tâche suivante qui attend le verrou de lecteur-writer actuel.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Threading.Thread>
- [IHostSyncManager, interface](ihostsyncmanager-interface.md)
- [Threading managé et non managé](/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))
- [Interfaces d'hébergement](hosting-interfaces.md)
