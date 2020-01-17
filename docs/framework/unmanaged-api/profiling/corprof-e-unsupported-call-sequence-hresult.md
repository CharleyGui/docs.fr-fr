---
title: CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT
ms.date: 03/30/2017
f1_keywords:
- CORPROF_E_UNSUPPORTED_CALL_SEQUENCE
helpviewer_keywords:
- CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT [.NET Framework profiling]
ms.assetid: f2fc441f-d62e-4f72-a011-354ea13c8c59
ms.openlocfilehash: 0cf3e05a0353a17541ee890f0871d694acac09fd
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116555"
---
# <a name="corprof_e_unsupported_call_sequence-hresult"></a>CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT

La CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT a été introduite dans .NET Framework version 2,0. .NET Framework 4 retourne ce HRESULT dans deux scénarios :  
  
- Lorsqu’un profileur de piratage réinitialise de force le contexte de registre d’un thread à un moment arbitraire afin que le thread tente d’accéder à des structures qui sont dans un état incohérent.  
  
- Lorsqu’un profileur essaie d’appeler une méthode d’information qui déclenche des garbage collection à partir d’une méthode de rappel qui interdit garbage collection.  
  
Ces deux scénarios sont présentés dans les sections suivantes.  
  
## <a name="hijacking-profilers"></a>Profileurs de détournement  

  (Ce scénario est principalement un problème avec les profileurs de détournement, bien que dans certains cas, les profileurs non détournés puissent voir ce HRESULT).  
  
 Dans ce scénario, un profileur de piratage réinitialise de force le contexte de registre d’un thread à un moment arbitraire afin que le thread puisse entrer le code du profileur ou entrer à nouveau le common language runtime (CLR) par le biais d’une méthode [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) .  
  
 La plupart des ID que l’API de profilage fournit pointent vers des structures de données dans le CLR. De nombreux `ICorProfilerInfo` appels lisent simplement les informations de ces structures de données et les transmettent. Toutefois, le CLR peut modifier des éléments dans ces structures à mesure qu’il s’exécute, et il peut utiliser des verrous pour le faire. Supposons que le CLR détient déjà (ou tente d’acquérir) un verrou au moment où le profileur a détourné le thread. Si le thread réintroduit le CLR et tente de prendre plus de verrous ou d’inspecter les structures qui étaient en cours de modification, ces structures peuvent être dans un état incohérent. Les interblocages et les violations d’accès peuvent facilement se produire dans de telles situations.  
  
 En général, lorsqu’un profileur de non-piratage exécute du code à l’intérieur d’une méthode [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) et appelle une méthode `ICorProfilerInfo` avec des paramètres valides, il ne doit pas se bloquer ou recevoir une violation d’accès. Par exemple, le code du profileur qui s’exécute à l’intérieur de la méthode [ICorProfilerCallback :: ClassLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md) peut demander des informations sur la classe en appelant la méthode [ICorProfilerInfo2 :: GetClassIDInfo2,](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md) . Le code peut recevoir un CORPROF_E_DATAINCOMPLETE HRESULT pour indiquer que les informations ne sont pas disponibles. Toutefois, il ne peut pas se bloquer ou recevoir une violation d’accès. Ces appels dans `ICorProfilerInfo` sont considérés comme synchrones, car ils sont effectués à partir d’une méthode `ICorProfilerCallback`.  
  
 Toutefois, un thread managé qui exécute du code qui ne se trouve pas dans une méthode `ICorProfilerCallback` est considéré comme effectuant un appel asynchrone. Dans .NET Framework version 1, il était difficile de déterminer ce qui peut se produire dans un appel asynchrone. L’appel peut se bloquer, se bloquer ou fournir une réponse non valide. .NET Framework version 2,0 a introduit quelques vérifications simples pour vous aider à éviter ce problème. Dans .NET Framework 2,0, si vous appelez une fonction de `ICorProfilerInfo` potentiellement dangereuse de manière asynchrone, elle échoue avec un CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT.  
  
 En général, les appels asynchrones ne sont pas sécurisés. Toutefois, les méthodes suivantes sont sûres et prennent en charge spécifiquement les appels asynchrones :  
  
- [GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)  
  
- [SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)  
  
- [GetCurrentThreadID](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcurrentthreadid-method.md)  
  
- [GetThreadContext](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getthreadcontext-method.md)  
  
- [GetThreadAppDomain](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadappdomain-method.md)  
  
- [GetFunctionFromIP](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md)  
  
- [GetFunctionInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctioninfo-method.md)  
  
- [Getfunctioninfo2,](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)  
  
- [GetCodeInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcodeinfo-method.md)  
  
- [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)  
  
- [GetModuleInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md)  
  
- [GetClassIDInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md)  
  
- [GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md)  
  
- [IsArrayClass,](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-isarrayclass-method.md)  
  
- [SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
  
- [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)  
  
 Pour plus d’informations, consultez l’entrée « [pourquoi nous avons CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](https://docs.microsoft.com/archive/blogs/davbr/why-we-have-corprof_e_unsupported_call_sequence) dans le blog de l’API de profilage CLR.  
  
## <a name="triggering-garbage-collections"></a>Déclenchement de garbage collection  
 Ce scénario implique un profileur qui s’exécute à l’intérieur d’une méthode de rappel (par exemple, l’une des méthodes `ICorProfilerCallback`) qui interdit garbage collection. Si le profileur essaie d’appeler une méthode d’information (par exemple, une méthode sur l’interface `ICorProfilerInfo`) qui peut déclencher un garbage collection, la méthode d’information échoue avec un CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT.  
  
 Le tableau suivant présente les méthodes de rappel qui interdisent les garbage collections et les méthodes d’information qui peuvent déclencher des garbage collection. Si le profileur s’exécute à l’intérieur de l’une des méthodes de rappel listées et appelle l’une des méthodes d’information listées, cette méthode d’information échoue avec un CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT.  
  
|Méthodes de rappel qui interdisent les garbage collection|Méthodes d’information qui déclenchent des garbage collection|  
|------------------------------------------------------|------------------------------------------------------------|  
|[ThreadAssignedToOSThread](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadassignedtoosthread-method.md)<br /><br /> [ExceptionUnwindFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)<br /><br /> [ExceptionUnwindFunctionLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionleave-method.md)<br /><br /> [ExceptionUnwindFinallyEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)<br /><br /> [ExceptionUnwindFinallyLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)<br /><br /> [ExceptionCatcherEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)<br /><br /> [RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)<br /><br /> [RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)<br /><br /> [RuntimeSuspendAborted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)<br /><br /> [RuntimeThreadSuspended](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)<br /><br /> [RuntimeThreadResumed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)<br /><br /> [MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)<br /><br /> [ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)<br /><br /> [ObjectsAllocatedByClass](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectsallocatedbyclass-method.md)<br /><br /> [RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)<br /><br /> [HandleCreated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handlecreated-method.md)<br /><br /> [HandleDestroyed,](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handledestroyed-method.md)<br /><br /> [GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)<br /><br /> [GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)|[GetILFunctionBodyAllocator](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md)<br /><br /> [SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)<br /><br /> [SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)<br /><br /> [ForceGC](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md)<br /><br /> [GetClassFromToken](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassfromtoken-method.md)<br /><br /> [GetClassFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)<br /><br /> [GetFunctionFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)<br /><br /> [GetAppDomainInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getappdomaininfo-method.md)<br /><br /> [EnumModules](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)<br /><br /> [RequestProfilerDetach](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-requestprofilerdetach-method.md)<br /><br /> [GetAppDomainsContainingModule](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getappdomainscontainingmodule-method.md)|  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback2, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [ICorProfilerCallback3, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)
- [ICorProfilerInfo, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [ICorProfilerInfo3, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Interfaces de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilage](../../../../docs/framework/unmanaged-api/profiling/index.md)
