---
title: COR_PRF_MODULE_FLAGS, énumération
ms.date: 04/10/2018
ms.assetid: 3ba543d8-15e5-4322-b6e7-1ebfc92ed7dd
ms.openlocfilehash: 72324fd434f3f37f723988345514c8aaada07ca9
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867150"
---
# <a name="cor_prf_high_monitor-enumeration"></a><span data-ttu-id="de794-102">COR_PRF_MODULE_FLAGS, énumération</span><span class="sxs-lookup"><span data-stu-id="de794-102">COR_PRF_HIGH_MONITOR Enumeration</span></span>

<span data-ttu-id="de794-103">[Pris en charge dans .NET Framework 4.5.2 et ultérieur]</span><span class="sxs-lookup"><span data-stu-id="de794-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
<span data-ttu-id="de794-104">Fournit des indicateurs en plus de ceux figurant dans l’énumération [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) que le profileur peut spécifier à la méthode [ICorProfilerInfo5 :: SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) lors du chargement.</span><span class="sxs-lookup"><span data-stu-id="de794-104">Provides flags in addition to those found in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration that the profiler can specify to the [ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method when it is loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de794-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de794-105">Syntax</span></span>  
  
```cpp
typedef enum {  
    COR_PRF_HIGH_MONITOR_NONE                     = 0x00000000,  
    COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES          = 0x00000001,  
    COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED        = 0x00000002,
    COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS = 0x00000004,
    COR_PRF_HIGH_DISABLE_TIERED_COMPILATION       = 0x00000008,
    COR_PRF_HIGH_BASIC_GC                         = 0x00000010,
    COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS         = 0x00000020,
    COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED    = 0x00000040,
    COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE            = 0,  
    COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH           = COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | 
                                                    COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS |
                                                    COR_PRF_HIGH_BASIC_GC |
                                                    COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS |
                                                    COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED,  
    COR_PRF_HIGH_MONITOR_IMMUTABLE                = COR_PRF_HIGH_DISABLE_TIERED_COMPILATION  
} COR_PRF_HIGH_MONITOR;  
```  
  
## <a name="members"></a><span data-ttu-id="de794-106">Members</span><span class="sxs-lookup"><span data-stu-id="de794-106">Members</span></span>  
  
|<span data-ttu-id="de794-107">Member</span><span class="sxs-lookup"><span data-stu-id="de794-107">Member</span></span>|<span data-ttu-id="de794-108">Description</span><span class="sxs-lookup"><span data-stu-id="de794-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|<span data-ttu-id="de794-109">Aucun indicateur n'est défini.</span><span class="sxs-lookup"><span data-stu-id="de794-109">No flags are set.</span></span>|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|<span data-ttu-id="de794-110">Contrôle le rappel [ICorProfilerCallback6 :: GetAssemblyReference](icorprofilercallback6-getassemblyreferences-method.md) pour l’ajout de références d’assembly pendant le parcours de fermeture de référence de l’assembly CLR.</span><span class="sxs-lookup"><span data-stu-id="de794-110">Controls the [ICorProfilerCallback6::GetAssemblyReference](icorprofilercallback6-getassemblyreferences-method.md) callback for adding assembly references during the CLR assembly reference closure walk.</span></span>|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|<span data-ttu-id="de794-111">Contrôle le rappel [ICorProfilerCallback7 :: ModuleInMemorySymbolsUpdated](icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) pour les mises à jour du flux de symboles associé à un module en mémoire.</span><span class="sxs-lookup"><span data-stu-id="de794-111">Controls the [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) callback for updates to the symbol stream associated with an in-memory module.</span></span>|  
|`COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`|<span data-ttu-id="de794-112">Contrôle le rappel [ICorProfilerCallback9 ::D ynamicmethodunloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) pour indiquer quand une méthode dynamique a été récupérée par le garbage collector et déchargée.</span><span class="sxs-lookup"><span data-stu-id="de794-112">Controls the [ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) callback for indicating when a dynamic method has been garbage collected and unloaded.</span></span> <br/> [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]|
|`COR_PRF_HIGH_DISABLE_TIERED_COMPILATION`|<span data-ttu-id="de794-113">.NET Core 3,0 et versions ultérieures uniquement : désactive la [compilation à plusieurs niveaux](../../../core/whats-new/dotnet-core-3-0.md) pour les profileurs.</span><span class="sxs-lookup"><span data-stu-id="de794-113">.NET Core 3.0 and later versions only: Disables [tiered compilation](../../../core/whats-new/dotnet-core-3-0.md) for profilers.</span></span>|
|`COR_PRF_HIGH_BASIC_GC`|<span data-ttu-id="de794-114">.NET Core 3,0 et versions ultérieures uniquement : fournit une option de profilage GC légère comparée à [`COR_PRF_MONITOR_GC`](cor-prf-monitor-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="de794-114">.NET Core 3.0 and later versions only: Provides a lightweight GC profiling option compared to [`COR_PRF_MONITOR_GC`](cor-prf-monitor-enumeration.md).</span></span> <span data-ttu-id="de794-115">Contrôle uniquement les rappels [GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)et [GetGenerationBounds,](icorprofilerinfo2-getgenerationbounds-method.md) .</span><span class="sxs-lookup"><span data-stu-id="de794-115">Controls only the  [GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md), and [GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md) callbacks.</span></span> <span data-ttu-id="de794-116">Contrairement à l’indicateur `COR_PRF_MONITOR_GC`, `COR_PRF_HIGH_BASIC_GC` ne désactive pas les garbage collection simultanés.</span><span class="sxs-lookup"><span data-stu-id="de794-116">Unlike the `COR_PRF_MONITOR_GC` flag, `COR_PRF_HIGH_BASIC_GC` does not disable concurrent garbage collection.</span></span>|
|`COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS`|<span data-ttu-id="de794-117">.NET Core 3,0 et versions ultérieures uniquement : active les rappels [MovedReferences](icorprofilercallback-movedreferences-method.md) et [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) pour compacter les GC uniquement.</span><span class="sxs-lookup"><span data-stu-id="de794-117">.NET Core 3.0 and later versions only: Enables the [MovedReferences](icorprofilercallback-movedreferences-method.md) and [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) callbacks for compacting GCs only.</span></span>|
|`COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED`|<span data-ttu-id="de794-118">.NET Core 3,0 et versions ultérieures uniquement : comme [`COR_PRF_MONITOR_OBJECT_ALLOCATED`](cor-prf-monitor-enumeration.md), mais fournit des informations sur les allocations d’objets pour le tas d’objets volumineux (LOH) uniquement.</span><span class="sxs-lookup"><span data-stu-id="de794-118">.NET Core 3.0 and later versions only: Similar to [`COR_PRF_MONITOR_OBJECT_ALLOCATED`](cor-prf-monitor-enumeration.md), but provides information on object allocations for the large object heap (LOH) only.</span></span>|
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|<span data-ttu-id="de794-119">Représente tous les indicateurs `COR_PRF_HIGH_MONITOR` qui requièrent des images à profil optimisé.</span><span class="sxs-lookup"><span data-stu-id="de794-119">Represents all `COR_PRF_HIGH_MONITOR` flags that require profile-enhanced images.</span></span> <span data-ttu-id="de794-120">Elle correspond à l’indicateur `COR_PRF_REQUIRE_PROFILE_IMAGE` dans l’énumération [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="de794-120">It corresponds to the `COR_PRF_REQUIRE_PROFILE_IMAGE` flag in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|<span data-ttu-id="de794-121">Représente tous les indicateurs `COR_PRF_HIGH_MONITOR` qui peuvent être définis une fois que le profileur est attaché à une application en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="de794-121">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set after the profiler is attached to a running app.</span></span>|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|<span data-ttu-id="de794-122">Représente tous les indicateurs `COR_PRF_HIGH_MONITOR` qui peuvent être définis uniquement lors de l'initialisation.</span><span class="sxs-lookup"><span data-stu-id="de794-122">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set only during initialization.</span></span> <span data-ttu-id="de794-123">Les tentatives de modification d'un ou plusieurs de ces indicateurs autre part génèrent une valeur `HRESULT`, qui indique un échec.</span><span class="sxs-lookup"><span data-stu-id="de794-123">Trying to change any of these flags elsewhere results in an `HRESULT` value that indicates failure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de794-124">Notes</span><span class="sxs-lookup"><span data-stu-id="de794-124">Remarks</span></span>

<span data-ttu-id="de794-125">Les indicateurs `COR_PRF_HIGH_MONITOR` sont utilisés avec le paramètre `pdwEventsHigh` des méthodes [ICorProfilerInfo5 :: GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) et [ICorProfilerInfo5 :: SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="de794-125">The `COR_PRF_HIGH_MONITOR` flags are used with the `pdwEventsHigh` parameter of the [ICorProfilerInfo5::GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) and [ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) methods.</span></span>  
  
<span data-ttu-id="de794-126">À partir du .NET Framework 4.6.1, la valeur de la `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` est passée de 0 à `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002).</span><span class="sxs-lookup"><span data-stu-id="de794-126">Starting with the .NET Framework 4.6.1, the value of the `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` changed from 0 to `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002).</span></span> <span data-ttu-id="de794-127">À partir de la .NET Framework 4.7.2, sa valeur est passée de `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` à `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`.</span><span class="sxs-lookup"><span data-stu-id="de794-127">Starting with the .NET Framework 4.7.2, its value changed from `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` to `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`.</span></span>   

<span data-ttu-id="de794-128">`COR_PRF_HIGH_MONITOR_IMMUTABLE` est un masque de masque qui représente tous les indicateurs qui peuvent être définis uniquement pendant l’initialisation.</span><span class="sxs-lookup"><span data-stu-id="de794-128">`COR_PRF_HIGH_MONITOR_IMMUTABLE` is intended to be a bitmask that represents all flags that can only be set during initialization.</span></span> <span data-ttu-id="de794-129">Toute tentative de modification d’un de ces indicateurs ailleurs entraîne l’échec d’un `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="de794-129">Trying to change any of these flags elsewhere results in a failed `HRESULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="de794-130">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="de794-130">Requirements</span></span>

<span data-ttu-id="de794-131">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de794-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
<span data-ttu-id="de794-132">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="de794-132">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="de794-133">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="de794-133">**Library:** CorGuids.lib</span></span>  
  
<span data-ttu-id="de794-134">**Versions du .NET Framework :** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de794-134">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de794-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="de794-135">See also</span></span>

- [<span data-ttu-id="de794-136">Énumérations de profilage</span><span class="sxs-lookup"><span data-stu-id="de794-136">Profiling Enumerations</span></span>](profiling-enumerations.md)
- [<span data-ttu-id="de794-137">COR_PRF_MONITOR, énumération</span><span class="sxs-lookup"><span data-stu-id="de794-137">COR_PRF_MONITOR Enumeration</span></span>](cor-prf-monitor-enumeration.md)
- [<span data-ttu-id="de794-138">ICorProfilerInfo5, interface</span><span class="sxs-lookup"><span data-stu-id="de794-138">ICorProfilerInfo5 Interface</span></span>](icorprofilerinfo5-interface.md)
