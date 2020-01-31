---
title: ICorDebugManagedCallback2, interface
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2
helpviewer_keywords:
- ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: cf7b7cfa-1c4b-4d8c-be70-4f9ed15a788b
topic_type:
- apiref
ms.openlocfilehash: 43982ebb634843c0130c3321aa84c90b84e8c786
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793315"
---
# <a name="icordebugmanagedcallback2-interface"></a>ICorDebugManagedCallback2, interface
Fournit des méthodes pour prendre en charge la gestion des exceptions et les Assistants Débogage managé (MDA) du débogueur. `ICorDebugManagedCallback2` est une extension logique de l’interface [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) .  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[ChangeConnection, méthode](icordebugmanagedcallback2-changeconnection-method.md)|Notifie le débogueur que l’ensemble des tâches associées à la connexion spécifiée a changé.|  
|[CreateConnection, méthode](icordebugmanagedcallback2-createconnection-method.md)|Notifie le débogueur qu’une nouvelle connexion a été créée.|  
|[DestroyConnection, méthode](icordebugmanagedcallback2-destroyconnection-method.md)|Notifie le débogueur que la connexion spécifiée a été arrêtée.|  
|[Exception, méthode](icordebugmanagedcallback2-exception-method.md)|Notifie le débogueur qu’une recherche d’un gestionnaire d’exceptions a démarré.|  
|[ExceptionUnwind, méthode](icordebugmanagedcallback2-exceptionunwind-method.md)|Fournit une notification d’État pendant le processus de déroulement de l’exception.|  
|[FunctionRemapComplete, méthode](icordebugmanagedcallback2-functionremapcomplete-method.md)|Notifie le débogueur que l’exécution du code a basculé vers une nouvelle version d’une fonction modifiée.|  
|[FunctionRemapOpportunity, méthode](icordebugmanagedcallback2-functionremapopportunity-method.md)|Notifie le débogueur que l’exécution du code a atteint un point de séquence dans une version antérieure d’une fonction modifiée.|  
|[MDANotification, méthode](icordebugmanagedcallback2-mdanotification-method.md)|Fournit une notification indiquant que l’exécution du code a rencontré un message de l’Assistant Débogage managé (MDA).|  
  
## <a name="remarks"></a>Notes  
 L’interface `ICorDebugManagedCallback2` étend l’interface `ICorDebugManagedCallback` pour gérer les nouveaux événements de débogage introduits dans le .NET Framework version 2,0.  
  
 Un débogueur doit implémenter `ICorDebugManagedCallback2` s’il débogue des applications .NET Framework 2,0. Une instance de `ICorDebugManagedCallback` ou `ICorDebugManagedCallback2` est passée en tant qu’objet de rappel à [ICorDebug :: SetManagedHandler](icordebug-setmanagedhandler-method.md).  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Diagnostic d’erreurs avec les Assistants Débogage managé](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Interfaces de débogage](debugging-interfaces.md)
- [ICorDebugManagedCallback, interface](icordebugmanagedcallback-interface.md)
