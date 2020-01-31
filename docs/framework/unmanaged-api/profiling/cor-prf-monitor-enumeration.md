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
ms.openlocfilehash: 2d7984ce109fb2bac5a36ab5e4c83f386de5a488
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867098"
---
# <a name="cor_prf_monitor-enumeration"></a><span data-ttu-id="c9d75-102">COR_PRF_MONITOR, énumération</span><span class="sxs-lookup"><span data-stu-id="c9d75-102">COR_PRF_MONITOR Enumeration</span></span>
<span data-ttu-id="c9d75-103">Contient des valeurs utilisées pour spécifier un comportement, des fonctionnalités ou des événements auxquels le profileur veut s'abonner.</span><span class="sxs-lookup"><span data-stu-id="c9d75-103">Contains values that are used to specify behavior, capabilities, or events to which the profiler wishes to subscribe.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9d75-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9d75-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="c9d75-105">Members</span><span class="sxs-lookup"><span data-stu-id="c9d75-105">Members</span></span>  
 <span data-ttu-id="c9d75-106">Les sections suivantes répertorient `COR_PRF_MONITOR` membres de l’énumération par catégorie.</span><span class="sxs-lookup"><span data-stu-id="c9d75-106">The following sections list `COR_PRF_MONITOR` enumeration members by category.</span></span> <span data-ttu-id="c9d75-107">Les catégories sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="c9d75-107">The categories are:</span></span>  
  
- [<span data-ttu-id="c9d75-108">Aucun indicateur défini</span><span class="sxs-lookup"><span data-stu-id="c9d75-108">No flags set</span></span>](#None)  
  
- [<span data-ttu-id="c9d75-109">Indicateurs de rappel</span><span class="sxs-lookup"><span data-stu-id="c9d75-109">Callback flags</span></span>](#Callback)  
  
- [<span data-ttu-id="c9d75-110">Indicateurs d’activation des fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="c9d75-110">Feature-enabling flags</span></span>](#Feature)  
  
- [<span data-ttu-id="c9d75-111">Indicateurs de configuration</span><span class="sxs-lookup"><span data-stu-id="c9d75-111">Configuration flags</span></span>](#Config)  
  
- [<span data-ttu-id="c9d75-112">Indicateurs composites</span><span class="sxs-lookup"><span data-stu-id="c9d75-112">Composite flags</span></span>](#Composite)  
  
<a name="None"></a>   
### <a name="no-flags-set"></a><span data-ttu-id="c9d75-113">Aucun indicateur défini</span><span class="sxs-lookup"><span data-stu-id="c9d75-113">No flags set</span></span>  
  
|<span data-ttu-id="c9d75-114">Member</span><span class="sxs-lookup"><span data-stu-id="c9d75-114">Member</span></span>|<span data-ttu-id="c9d75-115">Description</span><span class="sxs-lookup"><span data-stu-id="c9d75-115">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_MONITOR_NONE`|<span data-ttu-id="c9d75-116">Aucun indicateur n'est défini.</span><span class="sxs-lookup"><span data-stu-id="c9d75-116">No flags are set.</span></span>|  
  
<a name="Callback"></a>   
### <a name="callback-flags"></a><span data-ttu-id="c9d75-117">Indicateurs de rappel</span><span class="sxs-lookup"><span data-stu-id="c9d75-117">Callback flags</span></span>  
  
|<span data-ttu-id="c9d75-118">Member</span><span class="sxs-lookup"><span data-stu-id="c9d75-118">Member</span></span>|<span data-ttu-id="c9d75-119">Description</span><span class="sxs-lookup"><span data-stu-id="c9d75-119">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_MONITOR_ALL`|<span data-ttu-id="c9d75-120">Active tous les événements de rappel.</span><span class="sxs-lookup"><span data-stu-id="c9d75-120">Enables all callback events.</span></span>|  
|`COR_PRF_MONITOR_APPDOMAIN_LOADS`|<span data-ttu-id="c9d75-121">Contrôle la `AppDomainCreation*` et les rappels de `AppDomainShutdown*` dans l’interface [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="c9d75-121">Controls the `AppDomainCreation*` and `AppDomainShutdown*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_ASSEMBLY_LOADS`|<span data-ttu-id="c9d75-122">Contrôle la `AssemblyLoad*` et les rappels de `AssemblyUnload*` dans l’interface [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="c9d75-122">Controls the `AssemblyLoad*` and `AssemblyUnload*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_CACHE_SEARCHES`|<span data-ttu-id="c9d75-123">Contrôle le `JITCachedFunctionSearch*` les rappels dans l’interface [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="c9d75-123">Controls the `JITCachedFunctionSearch*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span><br /><br /> <span data-ttu-id="c9d75-124">Le comportement de cet indicateur est changé dans .NET Framework version 2.0.</span><span class="sxs-lookup"><span data-stu-id="c9d75-124">The behavior of this flag is changed in the .NET Framework version 2.0.</span></span>|  
|`COR_PRF_MONITOR_CCW`|<span data-ttu-id="c9d75-125">Contrôle le `COMClassicVTable*` les rappels dans l’interface [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="c9d75-125">Controls the `COMClassicVTable*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_CLASS_LOADS`|<span data-ttu-id="c9d75-126">Contrôle la `ClassLoad*` et les rappels de `ClassUnload*` dans l’interface [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="c9d75-126">Controls the `ClassLoad*` and `ClassUnload*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_CLR_EXCEPTIONS`|<span data-ttu-id="c9d75-127">Contrôle le `ExceptionCLRCatcher*` les rappels dans l’interface [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="c9d75-127">Controls the `ExceptionCLRCatcher*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_CODE_TRANSITIONS`|<span data-ttu-id="c9d75-128">Contrôle les rappels [UnmanagedToManagedTransition](icorprofilercallback-unmanagedtomanagedtransition-method.md) et [ManagedToUnmanagedTransition,](icorprofilercallback-managedtounmanagedtransition-method.md) dans l’interface [ICorProfilerCallback](icorprofilercallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="c9d75-128">Controls the [UnmanagedToManagedTransition](icorprofilercallback-unmanagedtomanagedtransition-method.md) and [ManagedToUnmanagedTransition](icorprofilercallback-managedtounmanagedtransition-method.md) callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface</span></span>|  
|`COR_PRF_MONITOR_ENTERLEAVE`|<span data-ttu-id="c9d75-129">Contrôle les [fonctions statiques globales de profilage](profiling-global-static-functions.md)`FunctionEnter*`, `FunctionLeave*`et `FunctionTailCall*`.</span><span class="sxs-lookup"><span data-stu-id="c9d75-129">Controls the `FunctionEnter*`,  `FunctionLeave*`, and `FunctionTailCall*`[profiling global static functions](profiling-global-static-functions.md).</span></span>|  
|`COR_PRF_MONITOR_EXCEPTIONS`|<span data-ttu-id="c9d75-130">Contrôle le rappel [ExceptionThrown,](icorprofilercallback-exceptionthrown-method.md) et les rappels `ExceptionSearch*`, `ExceptionOSHandler*`, `ExceptionUnwind*`et `ExceptionCatcher*` dans l’interface [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="c9d75-130">Controls the [ExceptionThrown](icorprofilercallback-exceptionthrown-method.md) callback and the `ExceptionSearch*`, `ExceptionOSHandler*`, `ExceptionUnwind*`, and `ExceptionCatcher*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_FUNCTION_UNLOADS`|<span data-ttu-id="c9d75-131">Contrôle le rappel [FunctionUnloadStarted,](icorprofilercallback-functionunloadstarted-method.md) dans l’interface [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="c9d75-131">Controls the [FunctionUnloadStarted](icorprofilercallback-functionunloadstarted-method.md) callback in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_GC`|<span data-ttu-id="c9d75-132">Contrôle les rappels [GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md), [MovedReferences](icorprofilercallback-movedreferences-method.md), [MovedReferences2](icorprofilercallback4-movedreferences2-method.md), [SurvivingReferences](icorprofilercallback2-survivingreferences-method.md), [survivingreferences2,](icorprofilercallback4-survivingreferences2-method.md), [ObjectReferences](icorprofilercallback-objectreferences-method.md), [ObjectsAllocatedByClass,](icorprofilercallback-objectsallocatedbyclass-method.md), [RootReferences](icorprofilercallback-rootreferences-method.md), [RootReferences2](icorprofilercallback2-rootreferences2-method.md), [HandleCreated](icorprofilercallback2-handlecreated-method.md), [HandleDestroyed,](icorprofilercallback2-handledestroyed-method.md)et [FinalizeableObjectQueued,](icorprofilercallback2-finalizeableobjectqueued-method.md) dans les interfaces `ICorProfilerCallback*`.</span><span class="sxs-lookup"><span data-stu-id="c9d75-132">Controls the [GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md),   [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md),  [MovedReferences](icorprofilercallback-movedreferences-method.md), [MovedReferences2](icorprofilercallback4-movedreferences2-method.md),    [SurvivingReferences](icorprofilercallback2-survivingreferences-method.md),  [SurvivingReferences2](icorprofilercallback4-survivingreferences2-method.md), [ObjectReferences](icorprofilercallback-objectreferences-method.md),   [ObjectsAllocatedByClass](icorprofilercallback-objectsallocatedbyclass-method.md),  [RootReferences](icorprofilercallback-rootreferences-method.md), [RootReferences2](icorprofilercallback2-rootreferences2-method.md), [HandleCreated](icorprofilercallback2-handlecreated-method.md),  [HandleDestroyed](icorprofilercallback2-handledestroyed-method.md), and [FinalizeableObjectQueued](icorprofilercallback2-finalizeableobjectqueued-method.md) callbacks in the `ICorProfilerCallback*` interfaces.</span></span> <span data-ttu-id="c9d75-133">Lorsque `COR_PRF_MONITOR_GC` est alloué, la garbage collection simultanée est désactivée.</span><span class="sxs-lookup"><span data-stu-id="c9d75-133">When `COR_PRF_MONITOR_GC` is allocated, concurrent garbage collection is turned off.</span></span>|  
|`COR_PRF_MONITOR_JIT_COMPILATION`|<span data-ttu-id="c9d75-134">Contrôle les rappels `JITCompilation*`, [JITFunctionPitched,](icorprofilercallback-jitfunctionpitched-method.md)et [JITInlining,](icorprofilercallback-jitinlining-method.md) dans l’interface [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="c9d75-134">Controls the `JITCompilation*`, [JITFunctionPitched](icorprofilercallback-jitfunctionpitched-method.md), and [JITInlining](icorprofilercallback-jitinlining-method.md) callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_MODULE_LOADS`|<span data-ttu-id="c9d75-135">Contrôle les rappels `ModuleLoad*`, `ModuleUnload*`et [ModuleAttachedToAssembly,](icorprofilercallback-moduleattachedtoassembly-method.md) dans l’interface [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="c9d75-135">Controls the `ModuleLoad*`,  `ModuleUnload*`, and [ModuleAttachedToAssembly](icorprofilercallback-moduleattachedtoassembly-method.md) callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_OBJECT_ALLOCATED`|<span data-ttu-id="c9d75-136">Contrôle le rappel [ObjectAllocated](icorprofilercallback-objectallocated-method.md) dans l’interface [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="c9d75-136">Controls the [ObjectAllocated](icorprofilercallback-objectallocated-method.md) callback in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_REMOTING`|<span data-ttu-id="c9d75-137">Contrôle le `Remoting*` les rappels dans l’interface [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="c9d75-137">Controls the `Remoting*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_REMOTING_ASYNC`|<span data-ttu-id="c9d75-138">Contrôle si les rappels `Remoting*` surveillent les événements asynchrones.</span><span class="sxs-lookup"><span data-stu-id="c9d75-138">Controls whether the `Remoting*` callbacks will monitor asynchronous events.</span></span>|  
|`COR_PRF_MONITOR_REMOTING_COOKIE`|<span data-ttu-id="c9d75-139">Contrôle si un cookie est passé aux rappels `Remoting*`.</span><span class="sxs-lookup"><span data-stu-id="c9d75-139">Controls whether a cookie is passed to the `Remoting*` callbacks.</span></span>|  
|`COR_PRF_MONITOR_SUSPENDS`|<span data-ttu-id="c9d75-140">Contrôle les rappels `RuntimeSuspend*`, `RuntimeResume*`, [RuntimeThreadSuspended,](icorprofilercallback-runtimethreadsuspended-method.md)et [RuntimeThreadResumed,](icorprofilercallback-runtimethreadresumed-method.md) dans l’interface [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="c9d75-140">Controls the `RuntimeSuspend*`, `RuntimeResume*`, [RuntimeThreadSuspended](icorprofilercallback-runtimethreadsuspended-method.md), and [RuntimeThreadResumed](icorprofilercallback-runtimethreadresumed-method.md) callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_THREADS`|<span data-ttu-id="c9d75-141">Contrôle les rappels [ThreadCreated](icorprofilercallback-threadcreated-method.md), [ThreadDestroyed](icorprofilercallback-threaddestroyed-method.md), [ThreadAssignedToOSThread,](icorprofilercallback-threadassignedtoosthread-method.md)et [ThreadNameChanged,](icorprofilercallback2-threadnamechanged-method.md) dans les interfaces [ICorProfilerCallback](icorprofilercallback-interface.md) et [ICorProfilerCallback2](icorprofilercallback2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="c9d75-141">Controls the [ThreadCreated](icorprofilercallback-threadcreated-method.md),  [ThreadDestroyed](icorprofilercallback-threaddestroyed-method.md),  [ThreadAssignedToOSThread](icorprofilercallback-threadassignedtoosthread-method.md), and [ThreadNameChanged](icorprofilercallback2-threadnamechanged-method.md) callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) and [ICorProfilerCallback2](icorprofilercallback2-interface.md) interfaces.</span></span>|  
  
<a name="Feature"></a>   
### <a name="feature-enabling-flags"></a><span data-ttu-id="c9d75-142">Indicateurs d’activation de fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="c9d75-142">Feature-enabling flags</span></span>  
  
|<span data-ttu-id="c9d75-143">Member</span><span class="sxs-lookup"><span data-stu-id="c9d75-143">Member</span></span>|<span data-ttu-id="c9d75-144">Description</span><span class="sxs-lookup"><span data-stu-id="c9d75-144">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_ENABLE_FRAME_INFO`|<span data-ttu-id="c9d75-145">Permet la récupération d’un `ClassID` exact pour une fonction générique en appelant la méthode [GetFunctionInfo2,](icorprofilerinfo2-getfunctioninfo2-method.md) avec une valeur `COR_PRF_FRAME_INFO` retournée par le rappel [FunctionEnter2](functionenter2-function.md) .</span><span class="sxs-lookup"><span data-stu-id="c9d75-145">Enables the retrieval of an exact `ClassID` for a generic function by calling the [GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) method with a `COR_PRF_FRAME_INFO` value returned by the [FunctionEnter2](functionenter2-function.md) callback.</span></span>|  
|`COR_PRF_ENABLE_FUNCTION_ARGS`|<span data-ttu-id="c9d75-146">Active le suivi d’argument à l’aide du rappel de [FunctionEnter2](functionenter2-function.md) ou du rappel de [FunctionEnter3WithInfo](functionenter3withinfo-function.md) et de la méthode [GetFunctionEnter3Info,](icorprofilerinfo3-getfunctionenter3info-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c9d75-146">Enables argument tracing using the [FunctionEnter2](functionenter2-function.md) callback or the [FunctionEnter3WithInfo](functionenter3withinfo-function.md) callback and the [GetFunctionEnter3Info](icorprofilerinfo3-getfunctionenter3info-method.md) method.</span></span>|  
|`COR_PRF_ENABLE_FUNCTION_RETVAL`|<span data-ttu-id="c9d75-147">Active le traçage des valeurs de retour à l’aide du rappel [FunctionLeave2](functionleave2-function.md) ou du rappel [FunctionLeave3WithInfo](functionleave3withinfo-function.md) et de la méthode [GetFunctionLeave3Info,](icorprofilerinfo3-getfunctionleave3info-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c9d75-147">Enables tracing of return values by using the [FunctionLeave2](functionleave2-function.md) callback or the [FunctionLeave3WithInfo](functionleave3withinfo-function.md) callback and [GetFunctionLeave3Info](icorprofilerinfo3-getfunctionleave3info-method.md) method.</span></span>|  
|`COR_PRF_ENABLE_INPROC_DEBUGGING`|<span data-ttu-id="c9d75-148">Option déconseillée.</span><span class="sxs-lookup"><span data-stu-id="c9d75-148">Deprecated.</span></span><br /><br /> <span data-ttu-id="c9d75-149">Le débogage in-process n'est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="c9d75-149">In process debugging is not supported.</span></span> <span data-ttu-id="c9d75-150">Cet indicateur est sans effet.</span><span class="sxs-lookup"><span data-stu-id="c9d75-150">This flag has no effect.</span></span>|  
|`COR_PRF_ENABLE_JIT_MAPS`|<span data-ttu-id="c9d75-151">Option déconseillée.</span><span class="sxs-lookup"><span data-stu-id="c9d75-151">Deprecated.</span></span><br /><br /> <span data-ttu-id="c9d75-152">Permet au profileur d’obtenir des mappages IL-natif à l’aide de [GetILToNativeMapping](icorprofilerinfo-getiltonativemapping-method.md).</span><span class="sxs-lookup"><span data-stu-id="c9d75-152">Allows the profiler to obtain IL-to-native maps by using [GetILToNativeMapping](icorprofilerinfo-getiltonativemapping-method.md).</span></span> <span data-ttu-id="c9d75-153">Depuis .NET Framework 2.0, le runtime fait toujours le suivi des mappes Langage intermédiaire – Natif. Cet indicateur est donc toujours considéré comme étant défini.</span><span class="sxs-lookup"><span data-stu-id="c9d75-153">Starting with the .NET Framework 2.0, the runtime always tracks IL-to-native maps; therefore, this flag is always considered to be set.</span></span>|  
|`COR_PRF_ENABLE_OBJECT_ALLOCATED`|<span data-ttu-id="c9d75-154">Informe le runtime que le profileur est susceptible de demander l'allocation d'objets.</span><span class="sxs-lookup"><span data-stu-id="c9d75-154">Informs the runtime that the profiler may want object allocation notifications.</span></span> <span data-ttu-id="c9d75-155">Cet indicateur doit être défini lors de l'initialisation.</span><span class="sxs-lookup"><span data-stu-id="c9d75-155">This flag must be set during initialization.</span></span> <span data-ttu-id="c9d75-156">Elle permet au profileur d’utiliser par la suite l’indicateur `COR_PRF_MONITOR_OBJECT_ALLOCATED` pour recevoir des rappels [ObjectAllocated](icorprofilercallback-objectallocated-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c9d75-156">It allows the profiler to subsequently use the `COR_PRF_MONITOR_OBJECT_ALLOCATED` flag to receive [ObjectAllocated](icorprofilercallback-objectallocated-method.md) callbacks.</span></span>|  
|`COR_PRF_ENABLE_REJIT`|<span data-ttu-id="c9d75-157">Active les appels aux méthodes [requestrejit,](icorprofilerinfo4-requestrejit-method.md) et [requestrevert,](icorprofilerinfo4-requestrevert-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c9d75-157">Enables calls to the [RequestReJIT](icorprofilerinfo4-requestrejit-method.md) and [RequestRevert](icorprofilerinfo4-requestrevert-method.md) methods.</span></span> <span data-ttu-id="c9d75-158">Le profileur doit définir cet indicateur au démarrage.</span><span class="sxs-lookup"><span data-stu-id="c9d75-158">The profiler must set this flag on startup.</span></span>  <span data-ttu-id="c9d75-159">Si le profileur spécifie cet indicateur, il doit aussi spécifier `COR_PRF_DISABLE_ALL_NGEN_IMAGES`.</span><span class="sxs-lookup"><span data-stu-id="c9d75-159">If the profiler specifies this flag, it must also specify `COR_PRF_DISABLE_ALL_NGEN_IMAGES`.</span></span>|  
|`COR_PRF_ENABLE_STACK_SNAPSHOT`|<span data-ttu-id="c9d75-160">Active les appels à la méthode [DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c9d75-160">Enables calls to the [DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>|  
  
<a name="Config"></a>   
### <a name="configuration-flags"></a><span data-ttu-id="c9d75-161">Indicateurs de configuration</span><span class="sxs-lookup"><span data-stu-id="c9d75-161">Configuration flags</span></span>  
  
|<span data-ttu-id="c9d75-162">Member</span><span class="sxs-lookup"><span data-stu-id="c9d75-162">Member</span></span>|<span data-ttu-id="c9d75-163">Description</span><span class="sxs-lookup"><span data-stu-id="c9d75-163">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_DISABLE_ALL_NGEN_IMAGES`|<span data-ttu-id="c9d75-164">Empêche le chargement de toutes les images natives (y compris les images optimisées par le profileur).</span><span class="sxs-lookup"><span data-stu-id="c9d75-164">Prevents all native images (including profiler-enhanced images) from loading.</span></span>  <span data-ttu-id="c9d75-165">Si cet indicateur et l'indicateur `COR_PRF_USE_PROFILE_IMAGES` sont tous deux spécifiés, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="c9d75-165">If this flag and the `COR_PRF_USE_PROFILE_IMAGES` flag are both specified, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` is used.</span></span>|  
|`COR_PRF_DISABLE_INLINING`|<span data-ttu-id="c9d75-166">Désactive toutes les incorporations.</span><span class="sxs-lookup"><span data-stu-id="c9d75-166">Disables all inlining.</span></span>|  
|`COR_PRF_DISABLE_OPTIMIZATIONS`|<span data-ttu-id="c9d75-167">Désactive toutes les optimisations du code.</span><span class="sxs-lookup"><span data-stu-id="c9d75-167">Disables all code optimizations.</span></span>|  
|`COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST`|<span data-ttu-id="c9d75-168">Désactive les vérifications de transparence de sécurité qui sont normalement effectuées lors de la compilation juste-à-temps et le chargement des classes pour les assemblys de confiance totale.</span><span class="sxs-lookup"><span data-stu-id="c9d75-168">Disables security transparency checks that are normally done during just-in-time (JIT) compilation and class loading for full-trust assemblies.</span></span> <span data-ttu-id="c9d75-169">Ceci peut rendre certaines instrumentations plus faciles à effectuer.</span><span class="sxs-lookup"><span data-stu-id="c9d75-169">This can make some instrumentation easier to perform.</span></span>|  
|`COR_PRF_USE_PROFILE_IMAGES`|<span data-ttu-id="c9d75-170">Fait que la recherche d'images natives s'effectue dans les images optimisées par le profileur.</span><span class="sxs-lookup"><span data-stu-id="c9d75-170">Causes the native image search to look for profiler-enhanced images.</span></span> <span data-ttu-id="c9d75-171">Si aucune image optimisée par le profileur n'est trouvée pour un assembly donné, le CLR (Common Language Runtime) passe au juste-à-temps pour cet assembly.</span><span class="sxs-lookup"><span data-stu-id="c9d75-171">If no profiler-enhanced image is found for a given assembly, the common language runtime falls back to JIT for that assembly.</span></span> <span data-ttu-id="c9d75-172">Si cet indicateur et l'indicateur `COR_PRF_DISABLE_ALL_NGEN_IMAGES` sont tous deux spécifiés, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="c9d75-172">If this flag and the `COR_PRF_DISABLE_ALL_NGEN_IMAGES` flag are both specified, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` is used.</span></span>|  
  
<a name="Composite"></a>   
### <a name="composite-flags"></a><span data-ttu-id="c9d75-173">Indicateurs composites</span><span class="sxs-lookup"><span data-stu-id="c9d75-173">Composite flags</span></span>  
  
|<span data-ttu-id="c9d75-174">Member</span><span class="sxs-lookup"><span data-stu-id="c9d75-174">Member</span></span>|<span data-ttu-id="c9d75-175">Description</span><span class="sxs-lookup"><span data-stu-id="c9d75-175">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_ALL`|<span data-ttu-id="c9d75-176">Représente toutes valeurs de l'indicateur `COR_PRF_MONITOR`.</span><span class="sxs-lookup"><span data-stu-id="c9d75-176">Represents all `COR_PRF_MONITOR` flag values.</span></span>|  
|`COR_PRF_ALLOWABLE_AFTER_ATTACH`|<span data-ttu-id="c9d75-177">Représente tous les indicateurs `COR_PRF_MONITOR` qui peuvent être définis une fois que le profileur est attaché à une application en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="c9d75-177">Represents all `COR_PRF_MONITOR` flags that can be set after the profiler is attached to a running app.</span></span> <span data-ttu-id="c9d75-178">La section Syntaxe indique les indicateurs individuels qui sont présents dans ce masque de bits.</span><span class="sxs-lookup"><span data-stu-id="c9d75-178">The syntax section indicates the individual flags that are present in this bitmask.</span></span>|  
|`COR_PRF_MONITOR_ALL`|<span data-ttu-id="c9d75-179">Active tous les événements de rappel.</span><span class="sxs-lookup"><span data-stu-id="c9d75-179">Enables all callback events.</span></span>|  
|`COR_PRF_MONITOR_IMMUTABLE`|<span data-ttu-id="c9d75-180">Représente tous les indicateurs `COR_PRF_MONITOR` qui peuvent être définis uniquement lors de l'initialisation.</span><span class="sxs-lookup"><span data-stu-id="c9d75-180">Represents all `COR_PRF_MONITOR` flags that can be set only during initialization.</span></span> <span data-ttu-id="c9d75-181">Les tentatives de modification d'un ou plusieurs de ces indicateurs après l'initialisation retournent une valeur `HRESULT`, qui indique un échec.</span><span class="sxs-lookup"><span data-stu-id="c9d75-181">Trying to change any of these flags after initialization returns an `HRESULT` value that indicates failure.</span></span>|  
|`COR_PRF_REQUIRE_PROFILE_IMAGE`|<span data-ttu-id="c9d75-182">Représente tous les indicateurs `COR_PRF_MONITOR` qui requièrent des images à profil optimisé.</span><span class="sxs-lookup"><span data-stu-id="c9d75-182">Represents all `COR_PRF_MONITOR` flags that require profile-enhanced images.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9d75-183">Notes</span><span class="sxs-lookup"><span data-stu-id="c9d75-183">Remarks</span></span>  
 <span data-ttu-id="c9d75-184">Une valeur `COR_PRF_MONITOR` est utilisée avec les méthodes [ICorProfilerInfo :: GetEventMask](icorprofilerinfo-geteventmask-method.md) et [ICorProfilerInfo :: SetEventMask](icorprofilerinfo-seteventmask-method.md) pour définir les notifications d’événements que l’Common Language Runtime apporte au profileur.</span><span class="sxs-lookup"><span data-stu-id="c9d75-184">A `COR_PRF_MONITOR` value is used with the [ICorProfilerInfo::GetEventMask](icorprofilerinfo-geteventmask-method.md) and [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) methods to define the event notifications that the common language runtime makes to the profiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9d75-185">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="c9d75-185">Requirements</span></span>  
 <span data-ttu-id="c9d75-186">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9d75-186">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9d75-187">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c9d75-187">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c9d75-188">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c9d75-188">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9d75-189">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9d75-189">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9d75-190">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c9d75-190">See also</span></span>

- [<span data-ttu-id="c9d75-191">Énumérations de profilage</span><span class="sxs-lookup"><span data-stu-id="c9d75-191">Profiling Enumerations</span></span>](profiling-enumerations.md)
- [<span data-ttu-id="c9d75-192">GetEventMask, méthode</span><span class="sxs-lookup"><span data-stu-id="c9d75-192">GetEventMask Method</span></span>](icorprofilerinfo-geteventmask-method.md)
- [<span data-ttu-id="c9d75-193">SetEventMask, méthode</span><span class="sxs-lookup"><span data-stu-id="c9d75-193">SetEventMask Method</span></span>](icorprofilerinfo-seteventmask-method.md)
