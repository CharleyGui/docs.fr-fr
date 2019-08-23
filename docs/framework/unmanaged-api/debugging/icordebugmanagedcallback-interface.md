---
title: ICorDebugManagedCallback, interface
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback
helpviewer_keywords:
- ICorDebugManagedCallback interface [.NET Framework debugging]
ms.assetid: b47f1d61-c7dc-4196-b926-0b08c94f7041
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25e40103a2925cbd2a181b8e39c3873e4d7c842c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940046"
---
# <a name="icordebugmanagedcallback-interface"></a>ICorDebugManagedCallback, interface
Fournit des méthodes pour traiter les rappels de débogueur.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Break, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-break-method.md)|Notifie le débogueur lorsqu’une <xref:System.Reflection.Emit.OpCodes.Break> instruction dans le flux de code est exécutée.|  
|[Breakpoint, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-breakpoint-method.md)|Notifie le débogueur lorsqu’un point d’arrêt est rencontré.|  
|[BreakpointSetError, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-breakpointseterror-method.md)|Notifie le débogueur que le common language runtime (CLR) n’a pas pu lier avec précision un point d’arrêt qui a été défini avant la compilation juste-à-temps (JIT) d’une fonction.|  
|[ControlCTrap, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-controlctrap-method.md)|Notifie le débogueur qu’un CTRL + C est intercepté dans le processus en cours de débogage.|  
|[CreateAppDomain, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createappdomain-method.md)|Notifie le débogueur qu’un domaine d’application a été créé.|  
|[CreateProcess, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md)|Notifie le débogueur lorsqu’un processus a été attaché ou démarré pour la première fois.|  
|[CreateThread, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md)|Notifie le débogueur qu’un thread a commencé à exécuter du code managé.|  
|[DebuggerError, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-debuggererror-method.md)|Notifie le débogueur qu’une erreur s’est produite lors de la tentative de gestion d’un événement à partir du CLR.|  
|[EditAndContinueRemap, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md)|Action déconseillée. Notifie le débogueur qu’un événement de remappage a été envoyé à l’IDE.|  
|[EvalComplete, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalcomplete-method.md)|Notifie le débogueur qu’une évaluation est terminée.|  
|[EvalException, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalexception-method.md)|Notifie le débogueur qu’une évaluation a été terminée avec une exception non gérée.|  
|[Exception, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exception-method.md)|Notifie le débogueur qu’une exception a été levée à partir du code managé.|  
|[ExitAppDomain, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md)|Notifie le débogueur qu’un domaine d’application s’est arrêté.|  
|[ExitProcess, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md)|Notifie le débogueur qu’un processus s’est arrêté.|  
|[ExitThread, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md)|Notifie le débogueur qu’un thread qui exécutait du code managé s’est arrêté.|  
|[LoadAssembly, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadassembly-method.md)|Notifie le débogueur qu’un assembly CLR a été chargé avec succès.|  
|[LoadClass, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)|Notifie le débogueur qu’une classe a été chargée.|  
|[LoadModule, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md)|Notifie le débogueur qu’un module CLR a été chargé avec succès.|  
|[LogMessage, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md)|Notifie le débogueur qu’un thread managé CLR a appelé une méthode dans la <xref:System.Diagnostics.EventLog> classe pour enregistrer un événement.|  
|[LogSwitch, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logswitch-method.md)|Notifie le débogueur qu’un thread managé CLR a appelé une méthode dans la <xref:System.Diagnostics.Switch> classe pour créer, modifier ou supprimer un commutateur de débogage/traçage.|  
|[NameChange, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-namechange-method.md)|Notifie le débogueur que le nom d’un thread ou d’un domaine d’application a changé.|  
|[StepComplete, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)|Notifie le débogueur qu’une étape est terminée.|  
|[UnloadAssembly, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadassembly-method.md)|Notifie le débogueur qu’un assembly CLR a été déchargé.|  
|[UnloadClass, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)|Notifie le débogueur qu’une classe est en cours de déchargement.|  
|[UnloadModule, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadmodule-method.md)|Notifie le débogueur qu’un module CLR (DLL) a été déchargé.|  
|[UpdateModuleSymbols, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md)|Notifie le débogueur que les symboles d’un module CLR ont changé.|  
  
## <a name="remarks"></a>Notes  
 Tous les rappels sont sérialisés, appelés dans le même thread et appelés avec le processus dans l’État Synchronized.  
  
 Chaque implémentation de rappel doit appeler [ICorDebugController:: continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) pour reprendre l’exécution. Si `ICorDebugController::Continue` n’est pas appelé avant le retour du rappel, le processus restera arrêté et aucun autre rappel d’événement ne `ICorDebugController::Continue` se produira tant que n’est pas appelé.  
  
 Un débogueur doit implémenter [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) s’il débogue des applications .NET Framework version 2,0. Une instance de `ICorDebugManagedCallback` ou `ICorDebugManagedCallback2` est passée en tant qu’objet de rappel à [ICorDebug:: SetManagedHandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md).  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug. idl, CorDebug. h  
  
 **Bibliothèque** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebug, interface](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [ICorDebugManagedCallback2, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
