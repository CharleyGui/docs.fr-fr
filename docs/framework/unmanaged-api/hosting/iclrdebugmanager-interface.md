---
title: ICLRDebugManager, interface
ms.date: 03/30/2017
api_name:
- ICLRDebugManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager
helpviewer_keywords:
- ICLRDebugManager interface [.NET Framework hosting]
ms.assetid: e835062c-c7d6-4945-8a44-2de7ebf3928e
topic_type:
- apiref
ms.openlocfilehash: 3836bd349423670a19a19dda67eba75419507a29
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724284"
---
# <a name="iclrdebugmanager-interface"></a>ICLRDebugManager, interface

Fournit des méthodes qui permettent à un hôte d’associer un ensemble de tâches à un identificateur et un nom convivial.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[BeginConnection, méthode](iclrdebugmanager-beginconnection-method.md)|Établit une nouvelle connexion entre l’hôte et le débogueur pour associer des tâches à un identificateur et un nom convivial.|  
|[EndConnection, méthode](iclrdebugmanager-endconnection-method.md)|Supprime l’association entre une liste de tâches et un identificateur et un nom convivial.|  
|[GetDacl, méthode](iclrdebugmanager-getdacl-method.md)|Cette méthode n’est pas implémentée.|  
|[IsDebuggerAttached, méthode](iclrdebugmanager-isdebuggerattached-method.md)|Obtient une valeur qui indique si un débogueur est attaché au processus.|  
|[SetConnectionTasks, méthode](iclrdebugmanager-setconnectiontasks-method.md)|Associe une liste d’instances d' [ICLRTask](iclrtask-interface.md) à un identificateur et un nom convivial.|  
|[SetDacl, méthode](iclrdebugmanager-setdacl-method.md)|Cette méthode n’est pas implémentée.|  
|[SetSymbolReadingPolicy, méthode](iclrdebugmanager-setsymbolreadingpolicy-method.md)|Définit la stratégie de lecture des fichiers de base de données du programme (PDB). La stratégie détermine si les informations sur les numéros de ligne et les fichiers sont incluses dans les piles des appels.|  
  
## <a name="remarks"></a>Remarques  

 Dans les scénarios de débogage, un hôte peut souhaiter regrouper des tâches en fonction de sa propre logique de programmation. Par exemple, un regroupement permettrait à un développeur de voir uniquement les tâches requises par les API du développeur, au lieu de voir toutes les tâches en cours d’exécution dans le processus. `ICLRDebugManager` permet à l’hôte d’implémenter ce type de regroupement.  
  
> [!IMPORTANT]
> Trois `ICLRDebugManager` méthodes, `BeginConnection` `SetConnectionTasks` et `EndConnection` sont dépendantes les unes des autres. Elles doivent être appelées dans l’ordre donné pour fonctionner comme prévu.  
  
 Le regroupement, les identificateurs et les noms conviviaux que l’hôte assigne au regroupement n’ont aucune signification pour le common language runtime (CLR). Le CLR transmet simplement les informations au débogueur.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces d'hébergement](hosting-interfaces.md)
