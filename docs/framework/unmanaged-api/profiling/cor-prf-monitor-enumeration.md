---
title: COR_PRF_MONITOR, énumération
ms.date: 03/30/2017
api_name:
- COR_PRF_MONITOR
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_MONITOR
helpviewer_keywords:
- COR_PRF_MONITOR enumeration [.NET Framework profiling]
ms.assetid: 9294d702-b4e5-441c-a930-e63d27b86bfd
topic_type:
- apiref
ms.openlocfilehash: 321ad53ca5f773191c5b5d1084b36caa6aeae4dc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137050"
---
# <a name="cor_prf_monitor-enumeration"></a>COR_PRF_MONITOR, énumération
Contient des valeurs utilisées pour spécifier un comportement, des fonctionnalités ou des événements auxquels le profileur veut s'abonner.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    COR_PRF_MONITOR_NONE                = 0x00000000,  
    COR_PRF_MONITOR_FUNCTION_UNLOADS    = 0x00000001,  
    COR_PRF_MONITOR_CLASS_LOADS         = 0x00000002,  
    COR_PRF_MONITOR_MODULE_LOADS        = 0x00000004,  
    COR_PRF_MONITOR_ASSEMBLY_LOADS      = 0x00000008,  
    COR_PRF_MONITOR_APPDOMAIN_LOADS     = 0x00000010,  
    COR_PRF_MONITOR_JIT_COMPILATION     = 0x00000020,  
    COR_PRF_MONITOR_EXCEPTIONS          = 0x00000040,  
    COR_PRF_MONITOR_GC                  = 0x00000080,  
    COR_PRF_MONITOR_OBJECT_ALLOCATED    = 0x00000100,  
    COR_PRF_MONITOR_THREADS             = 0x00000200,  
    COR_PRF_MONITOR_REMOTING            = 0x00000400,  
    COR_PRF_MONITOR_CODE_TRANSITIONS    = 0x00000800,  
    COR_PRF_MONITOR_ENTERLEAVE          = 0x00001000,  
    COR_PRF_MONITOR_CCW                 = 0x00002000,  
    COR_PRF_MONITOR_REMOTING_COOKIE     = 0x00004000 |   
                                          COR_PRF_MONITOR_REMOTING,  
    COR_PRF_MONITOR_REMOTING_ASYNC      = 0x00008000 |   
                                          COR_PRF_MONITOR_REMOTING,  
    COR_PRF_MONITOR_SUSPENDS            = 0x00010000,  
    COR_PRF_MONITOR_CACHE_SEARCHES      = 0x00020000,  
    COR_PRF_ENABLE_REJIT                = 0x00040000,  
    COR_PRF_ENABLE_INPROC_DEBUGGING     = 0x00080000,  
    COR_PRF_ENABLE_JIT_MAPS             = 0x00100000,  
    COR_PRF_DISABLE_INLINING            = 0x00200000,  
    COR_PRF_DISABLE_OPTIMIZATIONS       = 0x00400000,  
    COR_PRF_ENABLE_OBJECT_ALLOCATED     = 0x00800000,  
    COR_PRF_MONITOR_CLR_EXCEPTIONS      = 0x01000000,  
    COR_PRF_MONITOR_ALL                 = 0x0107FFFF,  
    COR_PRF_ENABLE_FUNCTION_ARGS        = 0X02000000,  
    COR_PRF_ENABLE_FUNCTION_RETVAL      = 0X04000000,  
    COR_PRF_ENABLE_FRAME_INFO           = 0X08000000,  
    COR_PRF_ENABLE_STACK_SNAPSHOT       = 0X10000000,  
    COR_PRF_USE_PROFILE_IMAGES          = 0x20000000,  
    COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST  
                                        = 0x40000000,  
    COR_PRF_DISABLE_ALL_NGEN_IMAGES     = 0x80000000,  
    COR_PRF_ALL                         = 0x8FFFFFFF,  
    COR_PRF_REQUIRE_PROFILE_IMAGE       = COR_PRF_USE_PROFILE_IMAGES |   
                                          COR_PRF_MONITOR_CODE_TRANSITIONS |   
                                          COR_PRF_MONITOR_ENTERLEAVE,  
    COR_PRF_ALLOWABLE_AFTER_ATTACH      = COR_PRF_MONITOR_THREADS |  
                                          COR_PRF_MONITOR_MODULE_LOADS |  
                                          COR_PRF_MONITOR_ASSEMBLY_LOADS |  
                                          COR_PRF_MONITOR_APPDOMAIN_LOADS |  
                                          COR_PRF_ENABLE_STACK_SNAPSHOT |  
                                          COR_PRF_MONITOR_GC |  
                                          COR_PRF_MONITOR_SUSPENDS |  
                                          COR_PRF_MONITOR_CLASS_LOADS |  
                                          COR_PRF_MONITOR_JIT_COMPILATION,  
    COR_PRF_MONITOR_IMMUTABLE           = COR_PRF_MONITOR_CODE_TRANSITIONS |  
                                          COR_PRF_MONITOR_REMOTING |  
                                          COR_PRF_MONITOR_REMOTING_COOKIE |  
                                          COR_PRF_MONITOR_REMOTING_ASYNC |  
                                          COR_PRF_ENABLE_REJIT |  
                                          COR_PRF_ENABLE_INPROC_DEBUGGING |  
                                          COR_PRF_ENABLE_JIT_MAPS |  
                                          COR_PRF_DISABLE_OPTIMIZATIONS |  
                                          COR_PRF_DISABLE_INLINING |  
                                          COR_PRF_ENABLE_OBJECT_ALLOCATED |  
                                          COR_PRF_ENABLE_FUNCTION_ARGS |  
                                          COR_PRF_ENABLE_FUNCTION_RETVAL |  
                                          COR_PRF_ENABLE_FRAME_INFO |  
                                          COR_PRF_USE_PROFILE_IMAGES |  
                     COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST |  
                                          COR_PRF_DISABLE_ALL_NGEN_IMAGES  
} COR_PRF_MONITOR;  
```  
  
## <a name="members"></a>Membres  
 Les sections suivantes répertorient `COR_PRF_MONITOR` membres de l’énumération par catégorie. Les catégories sont les suivantes :  
  
- [Aucun indicateur défini](#None)  
  
- [Indicateurs de rappel](#Callback)  
  
- [Indicateurs d’activation des fonctionnalités](#Feature)  
  
- [Indicateurs de configuration](#Config)  
  
- [Indicateurs composites](#Composite)  
  
<a name="None"></a>   
### <a name="no-flags-set"></a>Aucun indicateur défini  
  
|Membre|Description|  
|------------|-----------------|  
|`COR_PRF_MONITOR_NONE`|Aucun indicateur n'est défini.|  
  
<a name="Callback"></a>   
### <a name="callback-flags"></a>Indicateurs de rappel  
  
|Membre|Description|  
|------------|-----------------|  
|`COR_PRF_MONITOR_ALL`|Active tous les événements de rappel.|  
|`COR_PRF_MONITOR_APPDOMAIN_LOADS`|Contrôle les rappels `AppDomainCreation*` et `AppDomainShutdown*` dans l'interface [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md).|  
|`COR_PRF_MONITOR_ASSEMBLY_LOADS`|Contrôle les rappels `AssemblyLoad*` et `AssemblyUnload*` dans l'interface [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md).|  
|`COR_PRF_MONITOR_CACHE_SEARCHES`|Contrôle les rappels `JITCachedFunctionSearch*` dans l'interface [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md).<br /><br /> Le comportement de cet indicateur est changé dans .NET Framework version 2.0.|  
|`COR_PRF_MONITOR_CCW`|Contrôle les rappels `COMClassicVTable*` dans l'interface [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md).|  
|`COR_PRF_MONITOR_CLASS_LOADS`|Contrôle les rappels `ClassLoad*` et `ClassUnload*` dans l'interface [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md).|  
|`COR_PRF_MONITOR_CLR_EXCEPTIONS`|Contrôle les rappels `ExceptionCLRCatcher*` dans l'interface [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md).|  
|`COR_PRF_MONITOR_CODE_TRANSITIONS`|Contrôle les rappels [UnmanagedToManagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md) et [ManagedToUnmanagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md) dans l'interface [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md).|  
|`COR_PRF_MONITOR_ENTERLEAVE`|Contrôle les `FunctionEnter*`fonctions statiques globales de profilage`FunctionLeave*``FunctionTailCall*`, [ et ](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md).|  
|`COR_PRF_MONITOR_EXCEPTIONS`|Contrôle le rappel de [ExceptionThrown](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionthrown-method.md) et les rappels `ExceptionSearch*`, `ExceptionOSHandler*`, `ExceptionUnwind*` et `ExceptionCatcher*` dans l'interface [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md).|  
|`COR_PRF_MONITOR_FUNCTION_UNLOADS`|Contrôle le rappel de [FunctionUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-functionunloadstarted-method.md) dans l'interface [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md).|  
|`COR_PRF_MONITOR_GC`|Contrôle les rappels [GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md), [MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md), [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md), [SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md), [SurvivingReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md), [ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md), [ObjectsAllocatedByClass](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectsallocatedbyclass-method.md), [RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md), [RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md), [HandleCreated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handlecreated-method.md), [HandleDestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handledestroyed-method.md) et [FinalizeableObjectQueued](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md) dans les interfaces `ICorProfilerCallback*`. Lorsque `COR_PRF_MONITOR_GC` est alloué, la garbage collection simultanée est désactivée.|  
|`COR_PRF_MONITOR_JIT_COMPILATION`|Contrôle les rappels `JITCompilation*`, [JITFunctionPitched](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitfunctionpitched-method.md) et [JITInlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) dans l'interface [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md).|  
|`COR_PRF_MONITOR_MODULE_LOADS`|Contrôle les rappels `ModuleLoad*`, `ModuleUnload*` et [ModuleAttachedToAssembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) dans l'interface [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md).|  
|`COR_PRF_MONITOR_OBJECT_ALLOCATED`|Contrôle le rappel de [ObjectAllocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md) dans l'interface [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md).|  
|`COR_PRF_MONITOR_REMOTING`|Contrôle les rappels `Remoting*` dans l'interface [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md).|  
|`COR_PRF_MONITOR_REMOTING_ASYNC`|Contrôle si les rappels `Remoting*` surveillent les événements asynchrones.|  
|`COR_PRF_MONITOR_REMOTING_COOKIE`|Contrôle si un cookie est passé aux rappels `Remoting*`.|  
|`COR_PRF_MONITOR_SUSPENDS`|Contrôle les rappels `RuntimeSuspend*`, `RuntimeResume*`, [RuntimeThreadSuspended](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md) et [RuntimeThreadResumed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md) dans l'interface [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md).|  
|`COR_PRF_MONITOR_THREADS`|Contrôle les rappels [ThreadCreated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadcreated-method.md), [ThreadDestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md), [ThreadAssignedToOSThread](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadassignedtoosthread-method.md) et [ThreadNameChanged](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-threadnamechanged-method.md) dans les interfaces [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) et [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md).|  
  
<a name="Feature"></a>   
### <a name="feature-enabling-flags"></a>Indicateurs d’activation de fonctionnalité  
  
|Membre|Description|  
|------------|-----------------|  
|`COR_PRF_ENABLE_FRAME_INFO`|Active la récupération d'un `ClassID` exact pour une fonction générique en appelant la méthode [GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) avec une valeur `COR_PRF_FRAME_INFO` retournée par le rappel de [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md).|  
|`COR_PRF_ENABLE_FUNCTION_ARGS`|Active le suivi d'argument à l'aide du rappel de [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) ou du rappel de [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) et de la méthode [GetFunctionEnter3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md).|  
|`COR_PRF_ENABLE_FUNCTION_RETVAL`|Active le suivi des valeurs de retour à l'aide du rappel de [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) ou du rappel de [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) et de la méthode [GetFunctionLeave3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md).|  
|`COR_PRF_ENABLE_INPROC_DEBUGGING`|Obsolète.<br /><br /> Le débogage in-process n'est pas pris en charge. Cet indicateur est sans effet.|  
|`COR_PRF_ENABLE_JIT_MAPS`|Obsolète.<br /><br /> Permet au profileur d'obtenir des mappes Langage intermédiaire – Natif en utilisant [GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md). Depuis .NET Framework 2.0, le runtime fait toujours le suivi des mappes Langage intermédiaire – Natif. Cet indicateur est donc toujours considéré comme étant défini.|  
|`COR_PRF_ENABLE_OBJECT_ALLOCATED`|Informe le runtime que le profileur est susceptible de demander l'allocation d'objets. Cet indicateur doit être défini lors de l'initialisation. Il permet au profileur d'utiliser ensuite l'indicateur `COR_PRF_MONITOR_OBJECT_ALLOCATED` pour recevoir des rappels [ObjectAllocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md).|  
|`COR_PRF_ENABLE_REJIT`|Active les appels aux méthodes [RequestReJIT](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md) et [RequestRevert](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md). Le profileur doit définir cet indicateur au démarrage.  Si le profileur spécifie cet indicateur, il doit aussi spécifier `COR_PRF_DISABLE_ALL_NGEN_IMAGES`.|  
|`COR_PRF_ENABLE_STACK_SNAPSHOT`|Active les appels à la méthode [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md).|  
  
<a name="Config"></a>   
### <a name="configuration-flags"></a>Indicateurs de configuration  
  
|Membre|Description|  
|------------|-----------------|  
|`COR_PRF_DISABLE_ALL_NGEN_IMAGES`|Empêche le chargement de toutes les images natives (y compris les images optimisées par le profileur).  Si cet indicateur et l'indicateur `COR_PRF_USE_PROFILE_IMAGES` sont tous deux spécifiés, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` est utilisé.|  
|`COR_PRF_DISABLE_INLINING`|Désactive toutes les incorporations.|  
|`COR_PRF_DISABLE_OPTIMIZATIONS`|Désactive toutes les optimisations du code.|  
|`COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST`|Désactive les vérifications de transparence de sécurité qui sont normalement effectuées lors de la compilation juste-à-temps et le chargement des classes pour les assemblys de confiance totale. Ceci peut rendre certaines instrumentations plus faciles à effectuer.|  
|`COR_PRF_USE_PROFILE_IMAGES`|Fait que la recherche d'images natives s'effectue dans les images optimisées par le profileur. Si aucune image optimisée par le profileur n'est trouvée pour un assembly donné, le CLR (Common Language Runtime) passe au juste-à-temps pour cet assembly. Si cet indicateur et l'indicateur `COR_PRF_DISABLE_ALL_NGEN_IMAGES` sont tous deux spécifiés, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` est utilisé.|  
  
<a name="Composite"></a>   
### <a name="composite-flags"></a>Indicateurs composites  
  
|Membre|Description|  
|------------|-----------------|  
|`COR_PRF_ALL`|Représente toutes valeurs de l'indicateur `COR_PRF_MONITOR`.|  
|`COR_PRF_ALLOWABLE_AFTER_ATTACH`|Représente tous les indicateurs `COR_PRF_MONITOR` qui peuvent être définis une fois que le profileur est attaché à une application en cours d'exécution. La section Syntaxe indique les indicateurs individuels qui sont présents dans ce masque de bits.|  
|`COR_PRF_MONITOR_ALL`|Active tous les événements de rappel.|  
|`COR_PRF_MONITOR_IMMUTABLE`|Représente tous les indicateurs `COR_PRF_MONITOR` qui peuvent être définis uniquement lors de l'initialisation. Les tentatives de modification d'un ou plusieurs de ces indicateurs après l'initialisation retournent une valeur `HRESULT`, qui indique un échec.|  
|`COR_PRF_REQUIRE_PROFILE_IMAGE`|Représente tous les indicateurs `COR_PRF_MONITOR` qui requièrent des images à profil optimisé.|  
  
## <a name="remarks"></a>Notes  
 Une valeur `COR_PRF_MONITOR` est utilisée avec les méthodes [ICorProfilerInfo::GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) et [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) pour définir les notifications d'événements faites par le CLR (Common Language Runtime) au profileur.  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
- [GetEventMask, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)
- [SetEventMask, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)
