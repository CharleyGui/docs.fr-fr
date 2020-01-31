---
title: CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT
ms.date: 03/30/2017
f1_keywords:
- CORPROF_E_UNSUPPORTED_CALL_SEQUENCE
helpviewer_keywords:
- CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT [.NET Framework profiling]
ms.assetid: f2fc441f-d62e-4f72-a011-354ea13c8c59
ms.openlocfilehash: b4ab5c8f7cdca1303cb4fbbc4fa39db3c5977c15
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867007"
---
# <a name="corprof_e_unsupported_call_sequence-hresult"></a>CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT

La CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT a été introduite dans .NET Framework version 2,0. .NET Framework 4 retourne ce HRESULT dans deux scénarios :  
  
- Lorsqu’un profileur de piratage réinitialise de force le contexte de registre d’un thread à un moment arbitraire afin que le thread tente d’accéder à des structures qui sont dans un état incohérent.  
  
- Lorsqu’un profileur essaie d’appeler une méthode d’information qui déclenche des garbage collection à partir d’une méthode de rappel qui interdit garbage collection.  
  
Ces deux scénarios sont présentés dans les sections suivantes.  
  
## <a name="hijacking-profilers"></a>Profileurs de détournement  

  (Ce scénario est principalement un problème avec les profileurs de détournement, bien que dans certains cas, les profileurs non détournés puissent voir ce HRESULT).  
  
 Dans ce scénario, un profileur de piratage réinitialise de force le contexte de registre d’un thread à un moment arbitraire afin que le thread puisse entrer le code du profileur ou entrer à nouveau le common language runtime (CLR) par le biais d’une méthode [ICorProfilerInfo](icorprofilerinfo-interface.md) .  
  
 La plupart des ID que l’API de profilage fournit pointent vers des structures de données dans le CLR. De nombreux `ICorProfilerInfo` appels lisent simplement les informations de ces structures de données et les transmettent. Toutefois, le CLR peut modifier des éléments dans ces structures à mesure qu’il s’exécute, et il peut utiliser des verrous pour le faire. Supposons que le CLR détient déjà (ou tente d’acquérir) un verrou au moment où le profileur a détourné le thread. Si le thread réintroduit le CLR et tente de prendre plus de verrous ou d’inspecter les structures qui étaient en cours de modification, ces structures peuvent être dans un état incohérent. Les interblocages et les violations d’accès peuvent facilement se produire dans de telles situations.  
  
 En général, lorsqu’un profileur de non-piratage exécute du code à l’intérieur d’une méthode [ICorProfilerCallback](icorprofilercallback-interface.md) et appelle une méthode `ICorProfilerInfo` avec des paramètres valides, il ne doit pas se bloquer ou recevoir une violation d’accès. Par exemple, le code du profileur qui s’exécute à l’intérieur de la méthode [ICorProfilerCallback :: ClassLoadFinished](icorprofilercallback-classloadfinished-method.md) peut demander des informations sur la classe en appelant la méthode [ICorProfilerInfo2 :: GetClassIDInfo2,](icorprofilerinfo2-getclassidinfo2-method.md) . Le code peut recevoir un CORPROF_E_DATAINCOMPLETE HRESULT pour indiquer que les informations ne sont pas disponibles. Toutefois, il ne peut pas se bloquer ou recevoir une violation d’accès. Ces appels dans `ICorProfilerInfo` sont considérés comme synchrones, car ils sont effectués à partir d’une méthode `ICorProfilerCallback`.  
  
 Toutefois, un thread managé qui exécute du code qui ne se trouve pas dans une méthode `ICorProfilerCallback` est considéré comme effectuant un appel asynchrone. Dans .NET Framework version 1, il était difficile de déterminer ce qui peut se produire dans un appel asynchrone. L’appel peut se bloquer, se bloquer ou fournir une réponse non valide. .NET Framework version 2,0 a introduit quelques vérifications simples pour vous aider à éviter ce problème. Dans .NET Framework 2,0, si vous appelez une fonction de `ICorProfilerInfo` potentiellement dangereuse de manière asynchrone, elle échoue avec un CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT.  
  
 En général, les appels asynchrones ne sont pas sécurisés. Toutefois, les méthodes suivantes sont sûres et prennent en charge spécifiquement les appels asynchrones :  
  
- [GetEventMask](icorprofilerinfo-geteventmask-method.md)  
  
- [SetEventMask](icorprofilerinfo-seteventmask-method.md)  
  
- [GetCurrentThreadID](icorprofilerinfo-getcurrentthreadid-method.md)  
  
- [GetThreadContext](icorprofilerinfo-getthreadcontext-method.md)  
  
- [GetThreadAppDomain](icorprofilerinfo2-getthreadappdomain-method.md)  
  
- [GetFunctionFromIP](icorprofilerinfo-getfunctionfromip-method.md)  
  
- [GetFunctionInfo](icorprofilerinfo-getfunctioninfo-method.md)  
  
- [Getfunctioninfo2,](icorprofilerinfo2-getfunctioninfo2-method.md)  
  
- [GetCodeInfo](icorprofilerinfo-getcodeinfo-method.md)  
  
- [GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md)  
  
- [GetModuleInfo](icorprofilerinfo-getmoduleinfo-method.md)  
  
- [GetClassIDInfo](icorprofilerinfo-getclassidinfo-method.md)  
  
- [GetClassIDInfo2](icorprofilerinfo2-getclassidinfo2-method.md)  
  
- [IsArrayClass,](icorprofilerinfo-isarrayclass-method.md)  
  
- [SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md)  
  
- [DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md)  
  
 Pour plus d’informations, consultez l’entrée « [pourquoi nous avons CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](https://docs.microsoft.com/archive/blogs/davbr/why-we-have-corprof_e_unsupported_call_sequence) dans le blog de l’API de profilage CLR.  
  
## <a name="triggering-garbage-collections"></a>Déclenchement de garbage collection  
 Ce scénario implique un profileur qui s’exécute à l’intérieur d’une méthode de rappel (par exemple, l’une des méthodes `ICorProfilerCallback`) qui interdit garbage collection. Si le profileur essaie d’appeler une méthode d’information (par exemple, une méthode sur l’interface `ICorProfilerInfo`) qui peut déclencher un garbage collection, la méthode d’information échoue avec un CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT.  
  
 Le tableau suivant présente les méthodes de rappel qui interdisent les garbage collections et les méthodes d’information qui peuvent déclencher des garbage collection. Si le profileur s’exécute à l’intérieur de l’une des méthodes de rappel listées et appelle l’une des méthodes d’information listées, cette méthode d’information échoue avec un CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT.  
  
|Méthodes de rappel qui interdisent les garbage collection|Méthodes d’information qui déclenchent des garbage collection|  
|------------------------------------------------------|------------------------------------------------------------|  
|[ThreadAssignedToOSThread](icorprofilercallback-threadassignedtoosthread-method.md)<br /><br /> [ExceptionUnwindFunctionEnter](icorprofilercallback-exceptionunwindfunctionenter-method.md)<br /><br /> [ExceptionUnwindFunctionLeave](icorprofilercallback-exceptionunwindfunctionleave-method.md)<br /><br /> [ExceptionUnwindFinallyEnter](icorprofilercallback-exceptionunwindfinallyenter-method.md)<br /><br /> [ExceptionUnwindFinallyLeave](icorprofilercallback-exceptionunwindfinallyleave-method.md)<br /><br /> [ExceptionCatcherEnter](icorprofilercallback-exceptioncatcherenter-method.md)<br /><br /> [RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md)<br /><br /> [RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md)<br /><br /> [RuntimeSuspendAborted](icorprofilercallback-runtimesuspendaborted-method.md)<br /><br /> [RuntimeThreadSuspended](icorprofilercallback-runtimethreadsuspended-method.md)<br /><br /> [RuntimeThreadResumed](icorprofilercallback-runtimethreadresumed-method.md)<br /><br /> [MovedReferences](icorprofilercallback-movedreferences-method.md)<br /><br /> [ObjectReferences](icorprofilercallback-objectreferences-method.md)<br /><br /> [ObjectsAllocatedByClass](icorprofilercallback-objectsallocatedbyclass-method.md)<br /><br /> [RootReferences2](icorprofilercallback-rootreferences-method.md)<br /><br /> [HandleCreated](icorprofilercallback2-handlecreated-method.md)<br /><br /> [HandleDestroyed,](icorprofilercallback2-handledestroyed-method.md)<br /><br /> [GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md)<br /><br /> [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)|[GetILFunctionBodyAllocator](icorprofilerinfo-getilfunctionbodyallocator-method.md)<br /><br /> [SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md)<br /><br /> [SetILInstrumentedCodeMap](icorprofilerinfo-setilinstrumentedcodemap-method.md)<br /><br /> [ForceGC](icorprofilerinfo-forcegc-method.md)<br /><br /> [GetClassFromToken](icorprofilerinfo-getclassfromtoken-method.md)<br /><br /> [GetClassFromTokenAndTypeArgs](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)<br /><br /> [GetFunctionFromTokenAndTypeArgs](icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)<br /><br /> [GetAppDomainInfo](icorprofilerinfo-getappdomaininfo-method.md)<br /><br /> [EnumModules](icorprofilerinfo3-enummodules-method.md)<br /><br /> [RequestProfilerDetach](icorprofilerinfo3-requestprofilerdetach-method.md)<br /><br /> [GetAppDomainsContainingModule](icorprofilerinfo3-getappdomainscontainingmodule-method.md)|  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](icorprofilercallback-interface.md)
- [ICorProfilerCallback2, interface](icorprofilercallback2-interface.md)
- [ICorProfilerCallback3, interface](icorprofilercallback3-interface.md)
- [ICorProfilerInfo, interface](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interface](icorprofilerinfo2-interface.md)
- [ICorProfilerInfo3, interface](icorprofilerinfo3-interface.md)
- [Interfaces de profilage](profiling-interfaces.md)
- [Profilage](index.md)
