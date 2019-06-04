---
title: CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT
ms.date: 03/30/2017
f1_keywords:
- CORPROF_E_UNSUPPORTED_CALL_SEQUENCE
helpviewer_keywords:
- CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT [.NET Framework profiling]
ms.assetid: f2fc441f-d62e-4f72-a011-354ea13c8c59
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a8eb622b974de350f86a586a0f07b887bffdbd61
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66483068"
---
# <a name="corprofeunsupportedcallsequence-hresult"></a>CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT
CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT a été introduit dans le .NET Framework version 2.0. Le .NET Framework 4 retourne ce HRESULT dans deux scénarios :  
  
- Lorsqu’un profileur réinitialise forcée d’un thread inscrire le contexte à un moment arbitraire afin que le thread tente d’accéder aux structures qui sont dans un état incohérent.  
  
- Lorsqu’un profileur essaie d’appeler une méthode à caractère informatif qui déclenche le garbage collection à partir d’une méthode de rappel qui interdit le garbage collection.  
  
 Ces deux scénarios sont présentés dans les sections suivantes.  
  
## <a name="hijacking-profilers"></a>Profileurs d’attaques  
 (Ce scénario est principalement un problème de détournement des profileurs bien qu’il existe des cas où des profileurs non détournés peuvent consulter ce HRESULT.)  
  
 Dans ce scénario, un profileur réinitialise de force le contexte de Registre d’un thread à un moment arbitraire afin que le thread peut entrer le code du profileur ou entrer de nouveau le common language runtime (CLR) via une [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) (méthode).  
  
 La plupart des ID que l’API de profilage fournit point aux structures de données dans le CLR. Nombreux `ICorProfilerInfo` appelle simplement lire les informations de ces structures de données et les transmettre. Toutefois, le CLR peut modifier des éléments dans ces structures comme il s’exécute, et peut utiliser des verrous au pour faire. Supposons que le CLR a été déjà maintenant (ou une tentative d’acquisition) un verrou au moment où le profileur a détourné le thread. Si le thread entre à nouveau le CLR et essaie de prendre plus de verrous ou d’inspecter des structures qui étaient en cours de modification, ces structures peuvent être dans un état incohérent. Blocages et les violations d’accès peuvent se produire facilement dans de telles situations.  
  
 En règle générale, quand un profileur non malveillant exécute le code à l’intérieur d’un [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) (méthode) et des appels dans un `ICorProfilerInfo` méthode avec des paramètres valides, il le ne devrait pas se bloquer ou une violation d’accès. Par exemple, profileur de code qui s’exécute à l’intérieur de la [ICorProfilerCallback::ClassLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md) méthode peut demander des informations sur la classe en appelant le [ICorProfilerInfo2::GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md) méthode. Le code peut recevoir un résultat CORPROF_E_DATAINCOMPLETE HRESULT pour indiquer que les informations sont indisponibles ; Toutefois, n’interblocage ni recevoir une violation d’accès. Cette classe d’appels dans `ICorProfilerInfo` est appelée synchrone, car elles ont été effectuées à partir d’un `ICorProfilerCallback` (méthode).  
  
 Toutefois, un thread managé qui exécute le code qui n’est pas dans un `ICorProfilerCallback` méthode est considérée comme à être un appel asynchrone. Dans le .NET Framework version 1, il était difficile de déterminer ce qui peut se produire dans un appel asynchrone. L’appel peut se bloquer, se bloquer ou fournissent une réponse non valide. Le .NET Framework version 2.0 a introduit des contrôles simples pour vous aider à éviter ce problème. Dans le .NET Framework 2.0, si vous appelez un unsafe `ICorProfilerInfo` fonctionner de façon asynchrone, elle échoue avec un CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT.  
  
 En règle générale, les appels asynchrones ne sont pas sécurisés. Toutefois, les méthodes suivantes sont sécurisées et prennent en charge les appels asynchrones :  
  
- [GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)  
  
- [SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)  
  
- [GetCurrentThreadID](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcurrentthreadid-method.md)  
  
- [GetThreadContext](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getthreadcontext-method.md)  
  
- [GetThreadAppDomain](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadappdomain-method.md)  
  
- [GetFunctionFromIP](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md)  
  
- [GetFunctionInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctioninfo-method.md)  
  
- [GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)  
  
- [GetCodeInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcodeinfo-method.md)  
  
- [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)  
  
- [GetModuleInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md)  
  
- [GetClassIDInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md)  
  
- [GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md)  
  
- [IsArrayClass](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-isarrayclass-method.md)  
  
- [SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
  
- [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)  
  
 Pour plus d’informations, consultez l’entrée [pourquoi nous avons CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](https://go.microsoft.com/fwlink/?LinkId=169156) dans le blog de l’API de profilage CLR.  
  
## <a name="triggering-garbage-collections"></a>Déclenchement de Garbage Collections  
 Ce scénario implique un profileur est en cours d’exécution à l’intérieur d’une méthode de rappel (par exemple, un de le `ICorProfilerCallback` méthodes) qui interdit le garbage collection. Si le profileur tente d’appeler une méthode à caractère informatif (par exemple, une méthode sur le `ICorProfilerInfo` interface) qui peut déclencher une garbage collection, la méthode à caractère informatif échoue avec un CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT.  
  
 Le tableau suivant affiche les méthodes de rappel qui interdisent les garbage collections et des méthodes d’information qui peuvent déclencher un garbage collection. Si le profileur s’exécute à l’intérieur d’une des méthodes de rappel répertoriées et appelle l’une des méthodes répertoriées d’information, cette méthode à caractère informatif échoue avec un CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT.  
  
|Méthodes de rappel qui interdisent les garbage collections|Méthodes d’information qui déclenchent les garbage collection|  
|------------------------------------------------------|------------------------------------------------------------|  
|[ThreadAssignedToOSThread](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadassignedtoosthread-method.md)<br /><br /> [ExceptionUnwindFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)<br /><br /> [ExceptionUnwindFunctionLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionleave-method.md)<br /><br /> [ExceptionUnwindFinallyEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)<br /><br /> [ExceptionUnwindFinallyLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)<br /><br /> [ExceptionCatcherEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)<br /><br /> [RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)<br /><br /> [RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)<br /><br /> [RuntimeSuspendAborted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)<br /><br /> [RuntimeThreadSuspended](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)<br /><br /> [RuntimeThreadResumed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)<br /><br /> [MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)<br /><br /> [ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)<br /><br /> [ObjectsAllocatedByClass](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectsallocatedbyclass-method.md)<br /><br /> [RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)<br /><br /> [HandleCreated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handlecreated-method.md)<br /><br /> [HandleDestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handledestroyed-method.md)<br /><br /> [GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)<br /><br /> [GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)|[GetILFunctionBodyAllocator](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md)<br /><br /> [SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)<br /><br /> [SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)<br /><br /> [ForceGC](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md)<br /><br /> [GetClassFromToken](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassfromtoken-method.md)<br /><br /> [GetClassFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)<br /><br /> [GetFunctionFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)<br /><br /> [GetAppDomainInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getappdomaininfo-method.md)<br /><br /> [EnumModules](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)<br /><br /> [RequestProfilerDetach](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-requestprofilerdetach-method.md)<br /><br /> [GetAppDomainsContainingModule](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getappdomainscontainingmodule-method.md)|  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback2, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [ICorProfilerCallback3, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)
- [ICorProfilerInfo, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [ICorProfilerInfo3, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Interfaces de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilage](../../../../docs/framework/unmanaged-api/profiling/index.md)
