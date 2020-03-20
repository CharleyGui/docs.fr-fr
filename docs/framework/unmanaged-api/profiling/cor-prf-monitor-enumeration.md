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
ms.openlocfilehash: b6c3dc78b9c503747c7a2d404706eb797790b931
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175198"
---
# <a name="cor_prf_monitor-enumeration"></a><span data-ttu-id="9ef6f-102">COR_PRF_MONITOR, énumération</span><span class="sxs-lookup"><span data-stu-id="9ef6f-102">COR_PRF_MONITOR Enumeration</span></span>
<span data-ttu-id="9ef6f-103">Contient des valeurs utilisées pour spécifier un comportement, des fonctionnalités ou des événements auxquels le profileur veut s'abonner.</span><span class="sxs-lookup"><span data-stu-id="9ef6f-103">Contains values that are used to specify behavior, capabilities, or events to which the profiler wishes to subscribe.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ef6f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ef6f-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="9ef6f-105">Membres</span><span class="sxs-lookup"><span data-stu-id="9ef6f-105">Members</span></span>  
 <span data-ttu-id="9ef6f-106">Les sections `COR_PRF_MONITOR` suivantes énumèrent les membres par catégorie.</span><span class="sxs-lookup"><span data-stu-id="9ef6f-106">The following sections list `COR_PRF_MONITOR` enumeration members by category.</span></span> <span data-ttu-id="9ef6f-107">Les catégories sont les :</span><span class="sxs-lookup"><span data-stu-id="9ef6f-107">The categories are:</span></span>  
  
- [<span data-ttu-id="9ef6f-108">Pas de drapeaux fixés</span><span class="sxs-lookup"><span data-stu-id="9ef6f-108">No flags set</span></span>](#None)  
  
- [<span data-ttu-id="9ef6f-109">Indicateurs de rappel</span><span class="sxs-lookup"><span data-stu-id="9ef6f-109">Callback flags</span></span>](#Callback)  
  
- [<span data-ttu-id="9ef6f-110">Indicateurs d’activation de fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="9ef6f-110">Feature-enabling flags</span></span>](#Feature)  
  
- [<span data-ttu-id="9ef6f-111">Indicateurs de configuration</span><span class="sxs-lookup"><span data-stu-id="9ef6f-111">Configuration flags</span></span>](#Config)  
  
- [<span data-ttu-id="9ef6f-112">Indicateurs composites</span><span class="sxs-lookup"><span data-stu-id="9ef6f-112">Composite flags</span></span>](#Composite)  
  
<a name="None"></a>
### <a name="no-flags-set"></a><span data-ttu-id="9ef6f-113">Pas de drapeaux fixés</span><span class="sxs-lookup"><span data-stu-id="9ef6f-113">No flags set</span></span>  
  
|<span data-ttu-id="9ef6f-114">Membre</span><span class="sxs-lookup"><span data-stu-id="9ef6f-114">Member</span></span>|<span data-ttu-id="9ef6f-115">Description</span><span class="sxs-lookup"><span data-stu-id="9ef6f-115">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_MONITOR_NONE`|<span data-ttu-id="9ef6f-116">Aucun indicateur n'est défini.</span><span class="sxs-lookup"><span data-stu-id="9ef6f-116">No flags are set.</span></span>|  
  
<a name="Callback"></a>
### <a name="callback-flags"></a><span data-ttu-id="9ef6f-117">Indicateurs de rappel</span><span class="sxs-lookup"><span data-stu-id="9ef6f-117">Callback flags</span></span>  
  
|<span data-ttu-id="9ef6f-118">Membre</span><span class="sxs-lookup"><span data-stu-id="9ef6f-118">Member</span></span>|<span data-ttu-id="9ef6f-119">Description</span><span class="sxs-lookup"><span data-stu-id="9ef6f-119">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_MONITOR_ALL`|<span data-ttu-id="9ef6f-120">Active tous les événements de rappel.</span><span class="sxs-lookup"><span data-stu-id="9ef6f-120">Enables all callback events.</span></span>|  
|`COR_PRF_MONITOR_APPDOMAIN_LOADS`|<span data-ttu-id="9ef6f-121">Contrôle `AppDomainCreation*` le `AppDomainShutdown*` et les rappels dans l’interface [ICorProfilerCallback.](icorprofilercallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9ef6f-121">Controls the `AppDomainCreation*` and `AppDomainShutdown*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_ASSEMBLY_LOADS`|<span data-ttu-id="9ef6f-122">Contrôle `AssemblyLoad*` le `AssemblyUnload*` et les rappels dans l’interface [ICorProfilerCallback.](icorprofilercallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9ef6f-122">Controls the `AssemblyLoad*` and `AssemblyUnload*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_CACHE_SEARCHES`|<span data-ttu-id="9ef6f-123">Contrôle `JITCachedFunctionSearch*` les rappels dans l’interface [ICorProfilerCallback.](icorprofilercallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9ef6f-123">Controls the `JITCachedFunctionSearch*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span><br /><br /> <span data-ttu-id="9ef6f-124">Le comportement de cet indicateur est changé dans .NET Framework version 2.0.</span><span class="sxs-lookup"><span data-stu-id="9ef6f-124">The behavior of this flag is changed in the .NET Framework version 2.0.</span></span>|  
|`COR_PRF_MONITOR_CCW`|<span data-ttu-id="9ef6f-125">Contrôle `COMClassicVTable*` les rappels dans l’interface [ICorProfilerCallback.](icorprofilercallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9ef6f-125">Controls the `COMClassicVTable*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_CLASS_LOADS`|<span data-ttu-id="9ef6f-126">Contrôle `ClassLoad*` le `ClassUnload*` et les rappels dans l’interface [ICorProfilerCallback.](icorprofilercallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9ef6f-126">Controls the `ClassLoad*` and `ClassUnload*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_CLR_EXCEPTIONS`|<span data-ttu-id="9ef6f-127">Contrôle `ExceptionCLRCatcher*` les rappels dans l’interface [ICorProfilerCallback.](icorprofilercallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9ef6f-127">Controls the `ExceptionCLRCatcher*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_CODE_TRANSITIONS`|<span data-ttu-id="9ef6f-128">Contrôle les [rappels De LaTransition et](icorprofilercallback-unmanagedtomanagedtransition-method.md) [ManagedToUnmanagedTransition](icorprofilercallback-managedtounmanagedtransition-method.md) dans l’interface [ICorProfilerCallback](icorprofilercallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9ef6f-128">Controls the [UnmanagedToManagedTransition](icorprofilercallback-unmanagedtomanagedtransition-method.md) and [ManagedToUnmanagedTransition](icorprofilercallback-managedtounmanagedtransition-method.md) callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface</span></span>|  
|`COR_PRF_MONITOR_ENTERLEAVE`|<span data-ttu-id="9ef6f-129">Contrôle `FunctionEnter*`le `FunctionLeave*`, `FunctionTailCall*`, et [le profilage des fonctions statiques globales](profiling-global-static-functions.md).</span><span class="sxs-lookup"><span data-stu-id="9ef6f-129">Controls the `FunctionEnter*`,  `FunctionLeave*`, and `FunctionTailCall*`[profiling global static functions](profiling-global-static-functions.md).</span></span>|  
|`COR_PRF_MONITOR_EXCEPTIONS`|<span data-ttu-id="9ef6f-130">Contrôle le rappel [ExceptionThrown](icorprofilercallback-exceptionthrown-method.md) `ExceptionSearch*` `ExceptionOSHandler*`et `ExceptionUnwind*`le `ExceptionCatcher*` , , et les rappels dans [l’interface ICorProfilerCallback.](icorprofilercallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9ef6f-130">Controls the [ExceptionThrown](icorprofilercallback-exceptionthrown-method.md) callback and the `ExceptionSearch*`, `ExceptionOSHandler*`, `ExceptionUnwind*`, and `ExceptionCatcher*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_FUNCTION_UNLOADS`|<span data-ttu-id="9ef6f-131">Contrôle le rappel [FunctionUnloadStarted](icorprofilercallback-functionunloadstarted-method.md) dans l’interface [ICorProfilerCallback.](icorprofilercallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9ef6f-131">Controls the [FunctionUnloadStarted](icorprofilercallback-functionunloadstarted-method.md) callback in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_GC`|<span data-ttu-id="9ef6f-132">Contrôles de la [GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md), [MovedReferences](icorprofilercallback-movedreferences-method.md), [MovedReferences2](icorprofilercallback4-movedreferences2-method.md), [SurvivingReferences](icorprofilercallback2-survivingreferences-method.md), [SurvivingReferences2](icorprofilercallback4-survivingreferences2-method.md), [ObjectReferences](icorprofilercallback-objectreferences-method.md), [ObjectsAllocatedByClass](icorprofilercallback-objectsallocatedbyclass-method.md), [RootReferences](icorprofilercallback-rootreferences-method.md), [RootReferences2](icorprofilercallback2-rootreferences2-method.md), `ICorProfilerCallback*` [HandleCreated](icorprofilercallback2-handlecreated-method.md), [HandleDestroyed](icorprofilercallback2-handledestroyed-method.md), et [FinalizeableObjectQueued](icorprofilercallback2-finalizeableobjectqueued-method.md) rappels dans les interfaces.</span><span class="sxs-lookup"><span data-stu-id="9ef6f-132">Controls the [GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md),   [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md),  [MovedReferences](icorprofilercallback-movedreferences-method.md), [MovedReferences2](icorprofilercallback4-movedreferences2-method.md),    [SurvivingReferences](icorprofilercallback2-survivingreferences-method.md),  [SurvivingReferences2](icorprofilercallback4-survivingreferences2-method.md), [ObjectReferences](icorprofilercallback-objectreferences-method.md),   [ObjectsAllocatedByClass](icorprofilercallback-objectsallocatedbyclass-method.md),  [RootReferences](icorprofilercallback-rootreferences-method.md), [RootReferences2](icorprofilercallback2-rootreferences2-method.md), [HandleCreated](icorprofilercallback2-handlecreated-method.md),  [HandleDestroyed](icorprofilercallback2-handledestroyed-method.md), and [FinalizeableObjectQueued](icorprofilercallback2-finalizeableobjectqueued-method.md) callbacks in the `ICorProfilerCallback*` interfaces.</span></span> <span data-ttu-id="9ef6f-133">Lorsqu’elle `COR_PRF_MONITOR_GC` est allouée, la collecte simultanée des ordures est désactivée.</span><span class="sxs-lookup"><span data-stu-id="9ef6f-133">When `COR_PRF_MONITOR_GC` is allocated, concurrent garbage collection is turned off.</span></span>|  
|`COR_PRF_MONITOR_JIT_COMPILATION`|<span data-ttu-id="9ef6f-134">Contrôle `JITCompilation*`le , [JITFunctionPitched](icorprofilercallback-jitfunctionpitched-method.md), et [JITInlining](icorprofilercallback-jitinlining-method.md) rappels dans [l’interface ICorProfilerCallback.](icorprofilercallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9ef6f-134">Controls the `JITCompilation*`, [JITFunctionPitched](icorprofilercallback-jitfunctionpitched-method.md), and [JITInlining](icorprofilercallback-jitinlining-method.md) callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_MODULE_LOADS`|<span data-ttu-id="9ef6f-135">Contrôle `ModuleLoad*`les `ModuleUnload*`rappels , et [ModuleAttachedToAssembly](icorprofilercallback-moduleattachedtoassembly-method.md) dans l’interface [ICorProfilerCallback.](icorprofilercallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9ef6f-135">Controls the `ModuleLoad*`,  `ModuleUnload*`, and [ModuleAttachedToAssembly](icorprofilercallback-moduleattachedtoassembly-method.md) callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_OBJECT_ALLOCATED`|<span data-ttu-id="9ef6f-136">Contrôle le rappel [objectallocé](icorprofilercallback-objectallocated-method.md) dans l’interface [ICorProfilerCallback.](icorprofilercallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9ef6f-136">Controls the [ObjectAllocated](icorprofilercallback-objectallocated-method.md) callback in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_REMOTING`|<span data-ttu-id="9ef6f-137">Contrôle `Remoting*` les rappels dans l’interface [ICorProfilerCallback.](icorprofilercallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9ef6f-137">Controls the `Remoting*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_REMOTING_ASYNC`|<span data-ttu-id="9ef6f-138">Contrôle si les rappels `Remoting*` surveillent les événements asynchrones.</span><span class="sxs-lookup"><span data-stu-id="9ef6f-138">Controls whether the `Remoting*` callbacks will monitor asynchronous events.</span></span>|  
|`COR_PRF_MONITOR_REMOTING_COOKIE`|<span data-ttu-id="9ef6f-139">Contrôle si un cookie est passé aux rappels `Remoting*`.</span><span class="sxs-lookup"><span data-stu-id="9ef6f-139">Controls whether a cookie is passed to the `Remoting*` callbacks.</span></span>|  
|`COR_PRF_MONITOR_SUSPENDS`|<span data-ttu-id="9ef6f-140">Contrôles `RuntimeSuspend*`de `RuntimeResume*`la , , [RuntimeThreadSuspended](icorprofilercallback-runtimethreadsuspended-method.md), et [RuntimeThreadResumed](icorprofilercallback-runtimethreadresumed-method.md) callbacks dans [l’interface ICorProfilerCallback.](icorprofilercallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9ef6f-140">Controls the `RuntimeSuspend*`, `RuntimeResume*`, [RuntimeThreadSuspended](icorprofilercallback-runtimethreadsuspended-method.md), and [RuntimeThreadResumed](icorprofilercallback-runtimethreadresumed-method.md) callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_THREADS`|<span data-ttu-id="9ef6f-141">Contrôle les rappels [ThreadCreated](icorprofilercallback-threadcreated-method.md), [ThreadDestroyed](icorprofilercallback-threaddestroyed-method.md), [ThreadAssignedToOSThread](icorprofilercallback-threadassignedtoosthread-method.md), et [ThreadNameChanged](icorprofilercallback2-threadnamechanged-method.md) callbacks dans les interfaces [ICorProfilerCallback](icorprofilercallback-interface.md) et [ICorProfilerCallback2.](icorprofilercallback2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9ef6f-141">Controls the [ThreadCreated](icorprofilercallback-threadcreated-method.md),  [ThreadDestroyed](icorprofilercallback-threaddestroyed-method.md),  [ThreadAssignedToOSThread](icorprofilercallback-threadassignedtoosthread-method.md), and [ThreadNameChanged](icorprofilercallback2-threadnamechanged-method.md) callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) and [ICorProfilerCallback2](icorprofilercallback2-interface.md) interfaces.</span></span>|  
  
<a name="Feature"></a>
### <a name="feature-enabling-flags"></a><span data-ttu-id="9ef6f-142">Indicateurs d’activation de fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="9ef6f-142">Feature-enabling flags</span></span>  
  
|<span data-ttu-id="9ef6f-143">Membre</span><span class="sxs-lookup"><span data-stu-id="9ef6f-143">Member</span></span>|<span data-ttu-id="9ef6f-144">Description</span><span class="sxs-lookup"><span data-stu-id="9ef6f-144">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_ENABLE_FRAME_INFO`|<span data-ttu-id="9ef6f-145">Permet la récupération d’une `ClassID` fonction générique exacte en appelant la méthode [GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) avec une `COR_PRF_FRAME_INFO` valeur retournée par le rappel [FunctionEnter2.](functionenter2-function.md)</span><span class="sxs-lookup"><span data-stu-id="9ef6f-145">Enables the retrieval of an exact `ClassID` for a generic function by calling the [GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) method with a `COR_PRF_FRAME_INFO` value returned by the [FunctionEnter2](functionenter2-function.md) callback.</span></span>|  
|`COR_PRF_ENABLE_FUNCTION_ARGS`|<span data-ttu-id="9ef6f-146">Permet le traçage d’argumentation à l’aide du rappel [FunctionEnter2](functionenter2-function.md) ou du rappel [FunctionEnter3WithInfo](functionenter3withinfo-function.md) et de la méthode [GetFunctionEnter3Info.](icorprofilerinfo3-getfunctionenter3info-method.md)</span><span class="sxs-lookup"><span data-stu-id="9ef6f-146">Enables argument tracing using the [FunctionEnter2](functionenter2-function.md) callback or the [FunctionEnter3WithInfo](functionenter3withinfo-function.md) callback and the [GetFunctionEnter3Info](icorprofilerinfo3-getfunctionenter3info-method.md) method.</span></span>|  
|`COR_PRF_ENABLE_FUNCTION_RETVAL`|<span data-ttu-id="9ef6f-147">Permet le traçage des valeurs de retour en utilisant le rappel [FunctionLeave2](functionleave2-function.md) ou la méthode [FunctionLeave3WithInfo](functionleave3withinfo-function.md) et [GetFunctionLeave3Info.](icorprofilerinfo3-getfunctionleave3info-method.md)</span><span class="sxs-lookup"><span data-stu-id="9ef6f-147">Enables tracing of return values by using the [FunctionLeave2](functionleave2-function.md) callback or the [FunctionLeave3WithInfo](functionleave3withinfo-function.md) callback and [GetFunctionLeave3Info](icorprofilerinfo3-getfunctionleave3info-method.md) method.</span></span>|  
|`COR_PRF_ENABLE_INPROC_DEBUGGING`|<span data-ttu-id="9ef6f-148">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="9ef6f-148">Deprecated.</span></span><br /><br /> <span data-ttu-id="9ef6f-149">Le débogage in-process n'est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="9ef6f-149">In process debugging is not supported.</span></span> <span data-ttu-id="9ef6f-150">Cet indicateur est sans effet.</span><span class="sxs-lookup"><span data-stu-id="9ef6f-150">This flag has no effect.</span></span>|  
|`COR_PRF_ENABLE_JIT_MAPS`|<span data-ttu-id="9ef6f-151">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="9ef6f-151">Deprecated.</span></span><br /><br /> <span data-ttu-id="9ef6f-152">Permet au profileur d’obtenir des cartes IL-à-native en utilisant [GetILToNativeMapping](icorprofilerinfo-getiltonativemapping-method.md).</span><span class="sxs-lookup"><span data-stu-id="9ef6f-152">Allows the profiler to obtain IL-to-native maps by using [GetILToNativeMapping](icorprofilerinfo-getiltonativemapping-method.md).</span></span> <span data-ttu-id="9ef6f-153">Depuis .NET Framework 2.0, le runtime fait toujours le suivi des mappes Langage intermédiaire – Natif. Cet indicateur est donc toujours considéré comme étant défini.</span><span class="sxs-lookup"><span data-stu-id="9ef6f-153">Starting with the .NET Framework 2.0, the runtime always tracks IL-to-native maps; therefore, this flag is always considered to be set.</span></span>|  
|`COR_PRF_ENABLE_OBJECT_ALLOCATED`|<span data-ttu-id="9ef6f-154">Informe le runtime que le profileur est susceptible de demander l'allocation d'objets.</span><span class="sxs-lookup"><span data-stu-id="9ef6f-154">Informs the runtime that the profiler may want object allocation notifications.</span></span> <span data-ttu-id="9ef6f-155">Cet indicateur doit être défini lors de l'initialisation.</span><span class="sxs-lookup"><span data-stu-id="9ef6f-155">This flag must be set during initialization.</span></span> <span data-ttu-id="9ef6f-156">Il permet au profileur `COR_PRF_MONITOR_OBJECT_ALLOCATED` d’utiliser par la suite le drapeau pour recevoir des rappels [objectallocés.](icorprofilercallback-objectallocated-method.md)</span><span class="sxs-lookup"><span data-stu-id="9ef6f-156">It allows the profiler to subsequently use the `COR_PRF_MONITOR_OBJECT_ALLOCATED` flag to receive [ObjectAllocated](icorprofilercallback-objectallocated-method.md) callbacks.</span></span>|  
|`COR_PRF_ENABLE_REJIT`|<span data-ttu-id="9ef6f-157">Permet les appels vers les méthodes [RequestReJIT](icorprofilerinfo4-requestrejit-method.md) et [RequestRevert.](icorprofilerinfo4-requestrevert-method.md)</span><span class="sxs-lookup"><span data-stu-id="9ef6f-157">Enables calls to the [RequestReJIT](icorprofilerinfo4-requestrejit-method.md) and [RequestRevert](icorprofilerinfo4-requestrevert-method.md) methods.</span></span> <span data-ttu-id="9ef6f-158">Le profileur doit définir cet indicateur au démarrage.</span><span class="sxs-lookup"><span data-stu-id="9ef6f-158">The profiler must set this flag on startup.</span></span>  <span data-ttu-id="9ef6f-159">Si le profileur spécifie cet indicateur, il doit aussi spécifier `COR_PRF_DISABLE_ALL_NGEN_IMAGES`.</span><span class="sxs-lookup"><span data-stu-id="9ef6f-159">If the profiler specifies this flag, it must also specify `COR_PRF_DISABLE_ALL_NGEN_IMAGES`.</span></span>|  
|`COR_PRF_ENABLE_STACK_SNAPSHOT`|<span data-ttu-id="9ef6f-160">Permet les appels vers la méthode [DoStackSnapshot.](icorprofilerinfo2-dostacksnapshot-method.md)</span><span class="sxs-lookup"><span data-stu-id="9ef6f-160">Enables calls to the [DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>|  
  
<a name="Config"></a>
### <a name="configuration-flags"></a><span data-ttu-id="9ef6f-161">Indicateurs de configuration</span><span class="sxs-lookup"><span data-stu-id="9ef6f-161">Configuration flags</span></span>  
  
|<span data-ttu-id="9ef6f-162">Membre</span><span class="sxs-lookup"><span data-stu-id="9ef6f-162">Member</span></span>|<span data-ttu-id="9ef6f-163">Description</span><span class="sxs-lookup"><span data-stu-id="9ef6f-163">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_DISABLE_ALL_NGEN_IMAGES`|<span data-ttu-id="9ef6f-164">Empêche le chargement de toutes les images natives (y compris les images optimisées par le profileur).</span><span class="sxs-lookup"><span data-stu-id="9ef6f-164">Prevents all native images (including profiler-enhanced images) from loading.</span></span>  <span data-ttu-id="9ef6f-165">Si cet indicateur et l'indicateur `COR_PRF_USE_PROFILE_IMAGES` sont tous deux spécifiés, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="9ef6f-165">If this flag and the `COR_PRF_USE_PROFILE_IMAGES` flag are both specified, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` is used.</span></span>|  
|`COR_PRF_DISABLE_INLINING`|<span data-ttu-id="9ef6f-166">Désactive toutes les incorporations.</span><span class="sxs-lookup"><span data-stu-id="9ef6f-166">Disables all inlining.</span></span>|  
|`COR_PRF_DISABLE_OPTIMIZATIONS`|<span data-ttu-id="9ef6f-167">Désactive toutes les optimisations du code.</span><span class="sxs-lookup"><span data-stu-id="9ef6f-167">Disables all code optimizations.</span></span>|  
|`COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST`|<span data-ttu-id="9ef6f-168">Désactive les vérifications de transparence de sécurité qui sont normalement effectuées lors de la compilation juste-à-temps et le chargement des classes pour les assemblys de confiance totale.</span><span class="sxs-lookup"><span data-stu-id="9ef6f-168">Disables security transparency checks that are normally done during just-in-time (JIT) compilation and class loading for full-trust assemblies.</span></span> <span data-ttu-id="9ef6f-169">Ceci peut rendre certaines instrumentations plus faciles à effectuer.</span><span class="sxs-lookup"><span data-stu-id="9ef6f-169">This can make some instrumentation easier to perform.</span></span>|  
|`COR_PRF_USE_PROFILE_IMAGES`|<span data-ttu-id="9ef6f-170">Fait que la recherche d'images natives s'effectue dans les images optimisées par le profileur.</span><span class="sxs-lookup"><span data-stu-id="9ef6f-170">Causes the native image search to look for profiler-enhanced images.</span></span> <span data-ttu-id="9ef6f-171">Si aucune image optimisée par le profileur n'est trouvée pour un assembly donné, le CLR (Common Language Runtime) passe au juste-à-temps pour cet assembly.</span><span class="sxs-lookup"><span data-stu-id="9ef6f-171">If no profiler-enhanced image is found for a given assembly, the common language runtime falls back to JIT for that assembly.</span></span> <span data-ttu-id="9ef6f-172">Si cet indicateur et l'indicateur `COR_PRF_DISABLE_ALL_NGEN_IMAGES` sont tous deux spécifiés, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="9ef6f-172">If this flag and the `COR_PRF_DISABLE_ALL_NGEN_IMAGES` flag are both specified, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` is used.</span></span>|  
  
<a name="Composite"></a>
### <a name="composite-flags"></a><span data-ttu-id="9ef6f-173">Indicateurs composites</span><span class="sxs-lookup"><span data-stu-id="9ef6f-173">Composite flags</span></span>  
  
|<span data-ttu-id="9ef6f-174">Membre</span><span class="sxs-lookup"><span data-stu-id="9ef6f-174">Member</span></span>|<span data-ttu-id="9ef6f-175">Description</span><span class="sxs-lookup"><span data-stu-id="9ef6f-175">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_ALL`|<span data-ttu-id="9ef6f-176">Représente toutes valeurs de l'indicateur `COR_PRF_MONITOR`.</span><span class="sxs-lookup"><span data-stu-id="9ef6f-176">Represents all `COR_PRF_MONITOR` flag values.</span></span>|  
|`COR_PRF_ALLOWABLE_AFTER_ATTACH`|<span data-ttu-id="9ef6f-177">Représente tous les indicateurs `COR_PRF_MONITOR` qui peuvent être définis une fois que le profileur est attaché à une application en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="9ef6f-177">Represents all `COR_PRF_MONITOR` flags that can be set after the profiler is attached to a running app.</span></span> <span data-ttu-id="9ef6f-178">La section Syntaxe indique les indicateurs individuels qui sont présents dans ce masque de bits.</span><span class="sxs-lookup"><span data-stu-id="9ef6f-178">The syntax section indicates the individual flags that are present in this bitmask.</span></span>|  
|`COR_PRF_MONITOR_ALL`|<span data-ttu-id="9ef6f-179">Active tous les événements de rappel.</span><span class="sxs-lookup"><span data-stu-id="9ef6f-179">Enables all callback events.</span></span>|  
|`COR_PRF_MONITOR_IMMUTABLE`|<span data-ttu-id="9ef6f-180">Représente tous les indicateurs `COR_PRF_MONITOR` qui peuvent être définis uniquement lors de l'initialisation.</span><span class="sxs-lookup"><span data-stu-id="9ef6f-180">Represents all `COR_PRF_MONITOR` flags that can be set only during initialization.</span></span> <span data-ttu-id="9ef6f-181">Les tentatives de modification d'un ou plusieurs de ces indicateurs après l'initialisation retournent une valeur `HRESULT`, qui indique un échec.</span><span class="sxs-lookup"><span data-stu-id="9ef6f-181">Trying to change any of these flags after initialization returns an `HRESULT` value that indicates failure.</span></span>|  
|`COR_PRF_REQUIRE_PROFILE_IMAGE`|<span data-ttu-id="9ef6f-182">Représente tous les indicateurs `COR_PRF_MONITOR` qui requièrent des images à profil optimisé.</span><span class="sxs-lookup"><span data-stu-id="9ef6f-182">Represents all `COR_PRF_MONITOR` flags that require profile-enhanced images.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ef6f-183">Notes </span><span class="sxs-lookup"><span data-stu-id="9ef6f-183">Remarks</span></span>  
 <span data-ttu-id="9ef6f-184">Une `COR_PRF_MONITOR` valeur est utilisée avec [l’ICorProfilerInfo::GetEventMask](icorprofilerinfo-geteventmask-method.md) et [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) méthodes pour définir les notifications d’événements que le temps de course de langue commune fait au profileur.</span><span class="sxs-lookup"><span data-stu-id="9ef6f-184">A `COR_PRF_MONITOR` value is used with the [ICorProfilerInfo::GetEventMask](icorprofilerinfo-geteventmask-method.md) and [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) methods to define the event notifications that the common language runtime makes to the profiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ef6f-185">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9ef6f-185">Requirements</span></span>  
 <span data-ttu-id="9ef6f-186">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ef6f-186">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ef6f-187">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9ef6f-187">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9ef6f-188">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ef6f-188">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ef6f-189">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ef6f-189">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ef6f-190">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9ef6f-190">See also</span></span>

- [<span data-ttu-id="9ef6f-191">Énumérations de profilage</span><span class="sxs-lookup"><span data-stu-id="9ef6f-191">Profiling Enumerations</span></span>](profiling-enumerations.md)
- [<span data-ttu-id="9ef6f-192">GetEventMask, méthode</span><span class="sxs-lookup"><span data-stu-id="9ef6f-192">GetEventMask Method</span></span>](icorprofilerinfo-geteventmask-method.md)
- [<span data-ttu-id="9ef6f-193">SetEventMask, méthode</span><span class="sxs-lookup"><span data-stu-id="9ef6f-193">SetEventMask Method</span></span>](icorprofilerinfo-seteventmask-method.md)
