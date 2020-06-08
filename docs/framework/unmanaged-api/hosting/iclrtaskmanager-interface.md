---
title: ICLRTaskManager, interface
ms.date: 03/30/2017
api_name:
- ICLRTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager
helpviewer_keywords:
- ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: 2bd55e0c-001b-41fd-b29d-f01670fe8216
topic_type:
- apiref
ms.openlocfilehash: f918d4e7b95922734d70ed832581e6c494c70b05
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501636"
---
# <a name="iclrtaskmanager-interface"></a>ICLRTaskManager, interface
Fournit des méthodes qui permettent à l’hôte de demander explicitement que le common language runtime (CLR) crée une nouvelle tâche, d’obtenir la tâche en cours d’exécution et de définir la langue géographique et la culture de la tâche.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[CreateTask, méthode](iclrtaskmanager-createtask-method.md)|Demande explicitement que le CLR crée une nouvelle instance [ICLRTask](iclrtask-interface.md) .|  
|[GetCurrentTask, méthode](iclrtaskmanager-getcurrenttask-method.md)|Obtient l' `ICLRTask` instance qui représente la tâche en cours d’exécution.|  
|[GetCurrentTaskType, méthode](iclrtaskmanager-getcurrenttasktype-method.md)|Obtient le type de la tâche en cours d’exécution.|  
|[SetLocale, méthode](iclrtaskmanager-setlocale-method.md)|Notifie le CLR que l’hôte a modifié l’identificateur de paramètres régionaux sur la tâche en cours d’exécution.|  
|[SetUILocale, méthode](iclrtaskmanager-setuilocale-method.md)|Avertit le common language runtime que l’hôte a modifié l’identificateur de paramètres régionaux de l’interface utilisateur sur la tâche en cours d’exécution.|  
  
## <a name="remarks"></a>Remarques  
 Chaque tâche qui s’exécute dans un environnement hébergé a des représentations à la fois du côté hôte (une instance de [IHostTask](ihosttask-interface.md)) et du côté CLR (une instance d' [ICLRTask](iclrtask-interface.md)). L’hôte ou le CLR peut lancer la création d’une tâche, mais la représentation côté hôte doit être associée à une représentation côté CLR correspondante pour garantir la réussite de la communication entre l’hôte et le CLR concernant la tâche. Les deux objets doivent être créés et instanciés pour que le code managé puisse s’exécuter sur un thread de système d’exploitation.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRTask, interface](iclrtask-interface.md)
- [IHostTask, interface](ihosttask-interface.md)
- [IHostTaskManager, interface](ihosttaskmanager-interface.md)
- [Interfaces d'hébergement](hosting-interfaces.md)
