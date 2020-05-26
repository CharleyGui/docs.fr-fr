---
title: IHostGCManager, interface
ms.date: 03/30/2017
api_name:
- IHostGCManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager
helpviewer_keywords:
- IHostGCManager interface [.NET Framework hosting]
ms.assetid: 820330a4-244c-4f67-ab5e-f24b0b3c2080
topic_type:
- apiref
ms.openlocfilehash: 428e4cf8997713b08e40d9376c34ae5eee8cfa32
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804855"
---
# <a name="ihostgcmanager-interface"></a>IHostGCManager, interface
Fournit des méthodes qui notifient l’hôte d’événements dans le mécanisme de garbage collection implémenté par le common language runtime (CLR).  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|[SuspensionEnding, méthode](ihostgcmanager-suspensionending-method.md)|Avertit l’hôte que le CLR reprend l’exécution des tâches sur les threads suspendus pour un garbage collection.|  
|[SuspensionStarting, méthode](ihostgcmanager-suspensionstarting-method.md)|Avertit l’hôte que le CLR interrompt l’exécution des tâches, pour effectuer une garbage collection.|  
|[ThreadIsBlockingForSuspension, méthode](ihostgcmanager-threadisblockingforsuspension-method.md)|Avertit l’hôte que le thread à partir duquel l’appel de méthode a été effectué est sur le le bloc pour un garbage collection.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRTask, interface](iclrtask-interface.md)
- [ICLRTaskManager, interface](iclrtaskmanager-interface.md)
- [IHostTask, interface](ihosttask-interface.md)
- [IHostTaskManager, interface](ihosttaskmanager-interface.md)
- [Interfaces d'hébergement](hosting-interfaces.md)
