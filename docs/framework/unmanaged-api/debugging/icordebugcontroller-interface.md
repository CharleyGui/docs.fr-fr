---
title: ICorDebugController, interface
ms.date: 03/30/2017
api_name:
- ICorDebugController
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController
helpviewer_keywords:
- ICorDebugController interface [.NET Framework debugging]
ms.assetid: dbb1c4dc-269a-459b-ab1d-6c70788782ce
topic_type:
- apiref
ms.openlocfilehash: 1ca9e55a2183ca4293d30607496b588cbf21d6dd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679947"
---
# <a name="icordebugcontroller-interface"></a>ICorDebugController, interface

Représente une portée, un <xref:System.Diagnostics.Process> ou un <xref:System.AppDomain>, où le contexte d'exécution du code peut être contrôlé.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|Cette méthode est obsolète.|  
|`ICorDebugController::CommitChanges`|Cette méthode est obsolète.|  
|[Continue, méthode](icordebugcontroller-continue-method.md)|Reprend l’exécution des threads managés après un appel à [ICorDebugController :: Stop](icordebugcontroller-stop-method.md).|  
|[Detach, méthode](icordebugcontroller-detach-method.md)|Détache le débogueur du processus ou du domaine d’application.|  
|[EnumerateThreads, méthode](icordebugcontroller-enumeratethreads-method.md)|Obtient un énumérateur pour les threads managés actifs dans le processus.|  
|[HasQueuedCallbacks, méthode](icordebugcontroller-hasqueuedcallbacks-method.md)|Obtient une valeur qui indique si tous les rappels managés sont actuellement mis en file d’attente pour le thread spécifié.|  
|[IsRunning, méthode](icordebugcontroller-isrunning-method.md)|Obtient une valeur qui indique si les threads du processus sont en cours d’exécution librement.|  
|[SetAllThreadsDebugState, méthode](icordebugcontroller-setallthreadsdebugstate-method.md)|Définit l’état de débogage de tous les threads managés dans le processus.|  
|[Stop (méthode)](icordebugcontroller-stop-method.md)|Exécute un arrêt coopératif sur tous les threads qui exécutent du code managé dans le processus.|  
|[Terminate, méthode](icordebugcontroller-terminate-method.md)|Termine le processus avec le code de sortie spécifié.|  
  
## <a name="remarks"></a>Remarques  

 Si `ICorDebugController` contrôle un processus, l’étendue comprend tous les threads du processus. Si `ICorDebugController` contrôle un domaine d’application, l’étendue comprend uniquement les threads de ce domaine d’application particulier.  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
