---
title: ICorProfilerCallback, interface
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback
helpviewer_keywords:
- ICorProfilerCallback interface [.NET Framework profiling]
ms.assetid: 4bae06f7-94d7-4ba8-b250-648b2da78674
topic_type:
- apiref
ms.openlocfilehash: 487f347c19ab513f328a9f1a02601fc72c233eb5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449925"
---
# <a name="icorprofilercallback-interface"></a>ICorProfilerCallback, interface
Fournit des méthodes qui sont utilisées par le common language runtime (CLR) pour notifier un profileur de code lorsque les événements auxquels le profileur s’est abonné se produisent.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[AppDomainCreationFinished, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md)|Notifie le profileur qu’un domaine d’application a été créé.|  
|[AppDomainCreationStarted, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationstarted-method.md)|Notifie le profileur qu’un domaine d’application est en cours de création.|  
|[AppDomainShutdownFinished, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownfinished-method.md)|Notifie le profileur qu’un domaine d’application a été déchargé d’un processus.|  
|[AppDomainShutdownStarted, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md)|Notifie le profileur qu’un domaine d’application est en cours de déchargement d’un processus.|  
|[AssemblyLoadFinished, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md)|Notifie le profileur qu’un chargement de l’assembly est terminé.|  
|[AssemblyLoadStarted, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadstarted-method.md)|Notifie le profileur qu’un assembly est en cours de chargement.|  
|[AssemblyUnloadFinished, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadfinished-method.md)|Notifie le profileur qu’un assembly a été déchargé.|  
|[AssemblyUnloadStarted, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md)|Notifie le profileur qu’un assembly est en cours de déchargement.|  
|[ClassLoadFinished, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)|Notifie le profileur qu’une classe a fini de se charger.|  
|[ClassLoadStarted, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)|Notifie le profileur qu’une classe est en cours de chargement.|  
|[ClassUnloadFinished, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadfinished-method.md)|Notifie le profileur qu’une classe a terminé le déchargement.|  
|[ClassUnloadStarted, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadstarted-method.md)|Notifie le profileur qu’une classe est en cours de déchargement.|  
|[COMClassicVTableCreated, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtablecreated-method.md)|Notifie le profileur qu’un wrapper RCW (Runtime Callable Wrapper) pour l’IID et la classe spécifiés a été créé.|  
|[COMClassicVTableDestroyed, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtabledestroyed-method.md)|Notifie le profileur qu’un wrapper RCW est en cours de destruction.|  
|[ExceptionCatcherEnter, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)|Indique au profileur que le contrôle est passé au bloc de `catch` approprié.|  
|[ExceptionCatcherLeave, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)|Indique au profileur que le contrôle est passé en dehors du bloc de `catch` approprié.|  
|[ExceptionCLRCatcherExecute, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherexecute-method.md)|Obsolète dans la version 2,0 de .NET Framework.|  
|[ExceptionCLRCatcherFound, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherfound-method.md)|Obsolète dans le .NET Framework 2,0.|  
|[ExceptionOSHandlerEnter, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionoshandlerenter-method.md)|Non implémenté. Un profileur qui a besoin d’informations sur les exceptions non managées doit obtenir ces informations par d’autres moyens.|  
|[ExceptionOSHandlerLeave, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionoshandlerleave-method.md)|Non implémenté. Un profileur qui a besoin d’informations sur les exceptions non managées doit obtenir ces informations par d’autres moyens.|  
|[ExceptionSearchCatcherFound, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchcatcherfound-method.md)|Notifie le profileur que la phase de recherche de la gestion des exceptions a localisé un gestionnaire pour l’exception qui a été levée.|  
|[ExceptionSearchFilterEnter, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)|Indique au profileur qu’un filtre utilisateur est en cours d’exécution.|  
|[ExceptionSearchFilterLeave, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)|Notifie le profileur qu’un filtre utilisateur vient de terminer son exécution.|  
|[ExceptionSearchFunctionEnter, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md)|Notifie le profileur que la phase de recherche de la gestion des exceptions a entré une fonction.|  
|[ExceptionSearchFunctionLeave, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionleave-method.md)|Indique au profileur que la phase de recherche de la gestion des exceptions a fini de rechercher une fonction.|  
|[ExceptionThrown, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionthrown-method.md)|Notifie le profileur qu’une exception a été levée.|  
|[ExceptionUnwindFinallyEnter, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)|Notifie le profileur que la phase de déroulement de la gestion des exceptions introduit une clause `finally` contenue dans la fonction spécifiée.|  
|[ExceptionUnwindFinallyLeave, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)|Notifie le profileur que la phase de déroulement de la gestion des exceptions a quitté une clause `finally`.|  
|[ExceptionUnwindFunctionEnter, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)|Notifie le profileur que la phase de déroulement de la gestion des exceptions a entré une fonction.|  
|[ExceptionUnwindFunctionLeave, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionleave-method.md)|Notifie le profileur que la phase de déroulement de la gestion des exceptions a terminé le déroulement d’une fonction.|  
|[FunctionUnloadStarted, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-functionunloadstarted-method.md)|Notifie le profileur que le runtime a commencé à décharger une fonction.|  
|[Initialize, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)|Appelé pour initialiser le profileur chaque fois qu’une nouvelle application CLR est démarrée.|  
|[JITCachedFunctionSearchFinished, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md)|Notifie le profileur qu’une recherche est terminée pour une fonction qui a été compilée précédemment à l’aide de NGen. exe.|  
|[JITCachedFunctionSearchStarted, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md)|Notifie le profileur qu’une recherche a démarré pour une fonction qui a été compilée précédemment à l’aide de NGen. exe.|  
|[JITCompilationFinished, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)|Notifie le profileur que le compilateur JIT a terminé la compilation d’une fonction.|  
|[JITCompilationStarted, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)|Notifie le profileur que le compilateur juste-à-temps (JIT) a commencé à compiler une fonction.|  
|[JITFunctionPitched, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitfunctionpitched-method.md)|Notifie le profileur qu’une fonction qui a été compilée juste-à-temps a été supprimée de la mémoire.|  
|[JITInlining, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md)|Indique au profileur que le compilateur JIT va insérer une fonction en ligne avec une autre fonction.|  
|[ManagedToUnmanagedTransition, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md)|Notifie le profileur qu’une transition du code managé au code non managé s’est produite.|  
|[ModuleAttachedToAssembly, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md)|Notifie le profileur qu’un module est attaché à son assembly parent.|  
|[ModuleLoadFinished, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)|Notifie le profileur qu’un module a fini de se charger.|  
|[ModuleLoadStarted, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadstarted-method.md)|Notifie le profileur qu’un module est en cours de chargement.|  
|[ModuleUnloadFinished, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadfinished-method.md)|Notifie le profileur qu’un module a terminé le déchargement.|  
|[ModuleUnloadStarted, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md)|Notifie le profileur qu’un module est en cours de déchargement.|  
|[MovedReferences, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)|Notifie le profileur des références d’objet qui ont été déplacées pendant garbage collection.|  
|[ObjectAllocated, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md)|Indique au profileur que la mémoire dans le tas a été allouée pour un objet.|  
|[ObjectReferences, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)|Notifie le profileur des objets en mémoire référencés par l’objet spécifié.|  
|[ObjectsAllocatedByClass, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectsallocatedbyclass-method.md)|Notifie le profileur du nombre d’instances de chaque classe spécifiée qui ont été créées depuis le garbage collection précédent.|  
|[RemotingClientInvocationFinished, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)|Notifie le profileur qu’un appel de communication à distance a été exécuté sur le client.|  
|[RemotingClientInvocationStarted, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationstarted-method.md)|Notifie le profileur qu’un appel de communication à distance a démarré.|  
|[RemotingClientReceivingReply, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md)|Indique au profileur que la partie côté serveur d’un appel de communication à distance est terminée et que le client reçoit et est à présent en train de traiter la réponse.|  
|[RemotingClientSendingMessage, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)|Indique au profileur que le client envoie une demande au serveur.|  
|[RemotingServerInvocationReturned, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md)|Notifie le profileur que le processus a fini d’appeler une méthode en réponse à une demande d’appel de méthode distante.|  
|[RemotingServerInvocationStarted, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationstarted-method.md)|Notifie le profileur que le processus appelle une méthode en réponse à une demande d’appel de méthode distante.|  
|[RemotingServerReceivingMessage, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md)|Indique au profileur que le processus reçoit une demande d’activation ou d’appel de méthode distante.|  
|[RemotingServerSendingReply, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)|Indique au profileur que le processus a terminé le traitement d’une demande d’appel de méthode distante et qu’il est sur le paragraphe de transmettre la réponse via un canal.|  
|[RootReferences, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)|Notifie le profileur des informations sur les références racines après garbage collection.|  
|[RuntimeResumeFinished, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumefinished-method.md)|Notifie le profileur que le runtime a repris tous les threads d’exécution et qu’il a retourné un fonctionnement normal.|  
|[RuntimeResumeStarted, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md)|Indique au profileur que le runtime reprend tous les threads d’exécution.|  
|[RuntimeSuspendAborted, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)|Notifie le profileur que le runtime a abandonné l’interruption au moment de l’exécution qui s’est produite.|  
|[RuntimeSuspendFinished, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)|Notifie le profileur que le runtime a terminé la suspension de tous les threads d’exécution.|  
|[RuntimeSuspendStarted, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)|Indique au profileur que le runtime est sur le point d’interrompre tous les threads d’exécution.|  
|[RuntimeThreadResumed, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)|Notifie le profileur que le thread spécifié a repris après avoir été suspendu.|  
|[RuntimeThreadSuspended, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)|Notifie le profileur que le thread spécifié a été ou est en suspens.|  
|[Shutdown, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md)|Notifie le profileur que l’application est en cours d’arrêt.|  
|[ThreadAssignedToOSThread, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadassignedtoosthread-method.md)|Notifie le profileur qu’un thread managé est implémenté à l’aide d’un thread de système d’exploitation particulier.|  
|[ThreadCreated, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadcreated-method.md)|Notifie le profileur qu’un thread a été créé.|  
|[ThreadDestroyed, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md)|Notifie le profileur qu’un thread a été détruit.|  
|[UnmanagedToManagedTransition, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md)|Notifie le profileur qu’une transition du code non managé au code managé s’est produite.|  
  
## <a name="remarks"></a>Notes  
 Le CLR appelle une méthode dans l’interface `ICorProfilerCallback` (ou [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)) pour notifier le profileur lorsqu’un événement auquel le profileur s’est abonné, se produit. Il s’agit de l’interface de rappel principale par le biais de laquelle le CLR communique avec le profileur de code.  
  
 Un profileur de code doit implémenter les méthodes de l’interface `ICorProfilerCallback`. Pour la .NET Framework version 2,0 ou ultérieure, le profileur doit également implémenter les méthodes `ICorProfilerCallback2`. Chaque implémentation de méthode doit retourner un HRESULT ayant la valeur S_OK en cas de réussite ou E_FAIL en cas d’échec. Actuellement, le CLR ignore le HRESULT retourné par chaque rappel, à l’exception de [ICorProfilerCallback :: ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md).  
  
 Dans le Registre Microsoft Windows, un profileur de code doit inscrire son objet COM (Component Object Model) qui implémente les interfaces `ICorProfilerCallback` et `ICorProfilerCallback2`. Un profileur de code s’abonne aux événements pour lesquels il souhaite recevoir une notification en appelant [ICorProfilerInfo :: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md). Cela se fait généralement dans l’implémentation de [ICorProfilerCallback :: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)du profileur. Le profileur est ensuite en mesure de recevoir une notification de la part du runtime lorsqu’un événement est sur le ou s’est produit dans un processus du runtime en cours d’exécution.  
  
> [!NOTE]
> Le profileur inscrit un objet COM unique. Si le profileur cible le .NET Framework version 1,0 ou 1,1, cet objet COM doit implémenter uniquement les méthodes de `ICorProfilerCallback`. S’il cible .NET Framework version 2,0 ou ultérieure, l’objet COM doit également implémenter les méthodes de `ICorProfilerCallback2`.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerCallback2, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [ICorProfilerCallback3, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)
- [ICorProfilerCallback4, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
