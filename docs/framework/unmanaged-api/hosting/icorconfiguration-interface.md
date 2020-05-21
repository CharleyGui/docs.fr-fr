---
title: ICorConfiguration, interface
ms.date: 03/30/2017
api_name:
- ICorConfiguration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorConfiguration
helpviewer_keywords:
- ICorConfiguration interface [.NET Framework hosting]
ms.assetid: aaf96116-372b-4538-afb1-9e0fcdac1f98
topic_type:
- apiref
ms.openlocfilehash: 3b8c9421dea4040a9f183b886f1ad8575cace780
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762425"
---
# <a name="icorconfiguration-interface"></a>ICorConfiguration, interface
Fournit des méthodes pour configurer le common language runtime (CLR).  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[AddDebuggerSpecialThread, méthode](icorconfiguration-adddebuggerspecialthread-method.md)|Indique aux services de débogage qu’un thread particulier doit pouvoir continuer à s’exécuter pendant que le débogueur a une application arrêtée pendant des scénarios de débogage managés ou non managés.|  
|[SetDebuggerThreadControl, méthode](icorconfiguration-setdebuggerthreadcontrol-method.md)|Définit l’interface de rappel que les services de débogage appellera en tant que threads CLR sont bloqués et débloqués pour le débogage.|  
|[SetGCHostControl, méthode](icorconfiguration-setgchostcontrol-method.md)|Définit l’interface de rappel que le garbage collector doit utiliser pour demander à l’hôte de modifier les limites de la mémoire virtuelle.|  
|[SetGCThreadControl, méthode](icorconfiguration-setgcthreadcontrol-method.md)|Définit l’interface de rappel pour les threads de planification pour les tâches non-Runtime qui seraient sinon bloquées pour un garbage collection.|  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces d'hébergement](hosting-interfaces.md)
- [CorRuntimeHost, coclasse](corruntimehost-coclass.md)
