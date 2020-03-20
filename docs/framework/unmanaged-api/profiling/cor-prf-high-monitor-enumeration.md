---
title: COR_PRF_MODULE_FLAGS, énumération
ms.date: 04/10/2018
ms.assetid: 3ba543d8-15e5-4322-b6e7-1ebfc92ed7dd
ms.openlocfilehash: 5c6e34746368a7658c43fe0e2472000c29292569
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175211"
---
# <a name="cor_prf_high_monitor-enumeration"></a><span data-ttu-id="73250-102">COR_PRF_MODULE_FLAGS, énumération</span><span class="sxs-lookup"><span data-stu-id="73250-102">COR_PRF_HIGH_MONITOR Enumeration</span></span>

<span data-ttu-id="73250-103">[Pris en charge dans .NET Framework 4.5.2 et ultérieur]</span><span class="sxs-lookup"><span data-stu-id="73250-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
<span data-ttu-id="73250-104">Fournit des drapeaux en plus de ceux trouvés dans le [recensement COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) que le profileur peut spécifier à [l’ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) méthode quand il est de chargement.</span><span class="sxs-lookup"><span data-stu-id="73250-104">Provides flags in addition to those found in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration that the profiler can specify to the [ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method when it is loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73250-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73250-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="73250-106">Membres</span><span class="sxs-lookup"><span data-stu-id="73250-106">Members</span></span>  
  
|<span data-ttu-id="73250-107">Membre</span><span class="sxs-lookup"><span data-stu-id="73250-107">Member</span></span>|<span data-ttu-id="73250-108">Description</span><span class="sxs-lookup"><span data-stu-id="73250-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|<span data-ttu-id="73250-109">Aucun indicateur n'est défini.</span><span class="sxs-lookup"><span data-stu-id="73250-109">No flags are set.</span></span>|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|<span data-ttu-id="73250-110">Contrôle le [ICorProfilerCallback6::GetAssemblyReference](icorprofilercallback6-getassemblyreferences-method.md) callback pour l’ajout de références d’assemblage au cours de la marche de fermeture de référence d’assemblage CLR.</span><span class="sxs-lookup"><span data-stu-id="73250-110">Controls the [ICorProfilerCallback6::GetAssemblyReference](icorprofilercallback6-getassemblyreferences-method.md) callback for adding assembly references during the CLR assembly reference closure walk.</span></span>|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|<span data-ttu-id="73250-111">Contrôle [l’ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) callback pour les mises à jour du flux de symboles associés à un module en mémoire.</span><span class="sxs-lookup"><span data-stu-id="73250-111">Controls the [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) callback for updates to the symbol stream associated with an in-memory module.</span></span>|  
|`COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`|<span data-ttu-id="73250-112">Contrôle le rappel [ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) pour indiquer quand une méthode dynamique a été recueillie et déchargée.</span><span class="sxs-lookup"><span data-stu-id="73250-112">Controls the [ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) callback for indicating when a dynamic method has been garbage collected and unloaded.</span></span> <br/> [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]|
|`COR_PRF_HIGH_DISABLE_TIERED_COMPILATION`|<span data-ttu-id="73250-113">.NET Core 3.0 et versions ultérieures seulement: Disables [compilation à plusieurs niveaux](../../../core/whats-new/dotnet-core-3-0.md) pour les profileurs.</span><span class="sxs-lookup"><span data-stu-id="73250-113">.NET Core 3.0 and later versions only: Disables [tiered compilation](../../../core/whats-new/dotnet-core-3-0.md) for profilers.</span></span>|
|`COR_PRF_HIGH_BASIC_GC`|<span data-ttu-id="73250-114">.NET Core 3.0 et versions ultérieures seulement: Fournit [`COR_PRF_MONITOR_GC`](cor-prf-monitor-enumeration.md)une option légère de profilage GC par rapport à .</span><span class="sxs-lookup"><span data-stu-id="73250-114">.NET Core 3.0 and later versions only: Provides a lightweight GC profiling option compared to [`COR_PRF_MONITOR_GC`](cor-prf-monitor-enumeration.md).</span></span> <span data-ttu-id="73250-115">Contrôle seulement les [déchetsCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md), et [GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md) rappels.</span><span class="sxs-lookup"><span data-stu-id="73250-115">Controls only the  [GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md), and [GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md) callbacks.</span></span> <span data-ttu-id="73250-116">Contrairement `COR_PRF_MONITOR_GC` au `COR_PRF_HIGH_BASIC_GC` drapeau, ne désactive pas la collecte simultanée des ordures.</span><span class="sxs-lookup"><span data-stu-id="73250-116">Unlike the `COR_PRF_MONITOR_GC` flag, `COR_PRF_HIGH_BASIC_GC` does not disable concurrent garbage collection.</span></span>|
|`COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS`|<span data-ttu-id="73250-117">.NET Core 3.0 et versions ultérieures seulement: Permet les [recoupements MovedReferences](icorprofilercallback-movedreferences-method.md) et [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) pour compacter les CGC seulement.</span><span class="sxs-lookup"><span data-stu-id="73250-117">.NET Core 3.0 and later versions only: Enables the [MovedReferences](icorprofilercallback-movedreferences-method.md) and [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) callbacks for compacting GCs only.</span></span>|
|`COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED`|<span data-ttu-id="73250-118">.NET Core 3.0 et versions [`COR_PRF_MONITOR_OBJECT_ALLOCATED`](cor-prf-monitor-enumeration.md)ultérieures seulement: Similaire à , mais fournit des informations sur les allocations d’objets pour le tas grand objet (LOH) seulement.</span><span class="sxs-lookup"><span data-stu-id="73250-118">.NET Core 3.0 and later versions only: Similar to [`COR_PRF_MONITOR_OBJECT_ALLOCATED`](cor-prf-monitor-enumeration.md), but provides information on object allocations for the large object heap (LOH) only.</span></span>|
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|<span data-ttu-id="73250-119">Représente tous les indicateurs `COR_PRF_HIGH_MONITOR` qui requièrent des images à profil optimisé.</span><span class="sxs-lookup"><span data-stu-id="73250-119">Represents all `COR_PRF_HIGH_MONITOR` flags that require profile-enhanced images.</span></span> <span data-ttu-id="73250-120">Il correspond au `COR_PRF_REQUIRE_PROFILE_IMAGE` drapeau dans le [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) énumération.</span><span class="sxs-lookup"><span data-stu-id="73250-120">It corresponds to the `COR_PRF_REQUIRE_PROFILE_IMAGE` flag in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|<span data-ttu-id="73250-121">Représente tous les indicateurs `COR_PRF_HIGH_MONITOR` qui peuvent être définis une fois que le profileur est attaché à une application en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="73250-121">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set after the profiler is attached to a running app.</span></span>|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|<span data-ttu-id="73250-122">Représente tous les indicateurs `COR_PRF_HIGH_MONITOR` qui peuvent être définis uniquement lors de l'initialisation.</span><span class="sxs-lookup"><span data-stu-id="73250-122">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set only during initialization.</span></span> <span data-ttu-id="73250-123">Les tentatives de modification d'un ou plusieurs de ces indicateurs autre part génèrent une valeur `HRESULT`, qui indique un échec.</span><span class="sxs-lookup"><span data-stu-id="73250-123">Trying to change any of these flags elsewhere results in an `HRESULT` value that indicates failure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73250-124">Notes </span><span class="sxs-lookup"><span data-stu-id="73250-124">Remarks</span></span>

<span data-ttu-id="73250-125">Les `COR_PRF_HIGH_MONITOR` drapeaux sont `pdwEventsHigh` utilisés avec le paramètre de [l’ICorProfilerInfo5::GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) et [ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) méthodes.</span><span class="sxs-lookup"><span data-stu-id="73250-125">The `COR_PRF_HIGH_MONITOR` flags are used with the `pdwEventsHigh` parameter of the [ICorProfilerInfo5::GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) and [ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) methods.</span></span>  
  
<span data-ttu-id="73250-126">À partir du cadre .NET 4.6.1, la valeur du `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` changement de 0 à `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002).</span><span class="sxs-lookup"><span data-stu-id="73250-126">Starting with the .NET Framework 4.6.1, the value of the `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` changed from 0 to `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002).</span></span> <span data-ttu-id="73250-127">À partir du cadre .NET 4.7.2, sa valeur est passée de `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`.</span><span class="sxs-lookup"><span data-stu-id="73250-127">Starting with the .NET Framework 4.7.2, its value changed from `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` to `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`.</span></span>

<span data-ttu-id="73250-128">`COR_PRF_HIGH_MONITOR_IMMUTABLE`est destiné à être un bitmask qui représente tous les drapeaux qui ne peuvent être fixés pendant l’initialisation.</span><span class="sxs-lookup"><span data-stu-id="73250-128">`COR_PRF_HIGH_MONITOR_IMMUTABLE` is intended to be a bitmask that represents all flags that can only be set during initialization.</span></span> <span data-ttu-id="73250-129">Essayer de changer l’un de `HRESULT`ces drapeaux ailleurs se traduit par un échec .</span><span class="sxs-lookup"><span data-stu-id="73250-129">Trying to change any of these flags elsewhere results in a failed `HRESULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="73250-130">Spécifications</span><span class="sxs-lookup"><span data-stu-id="73250-130">Requirements</span></span>

<span data-ttu-id="73250-131">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73250-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
<span data-ttu-id="73250-132">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="73250-132">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="73250-133">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73250-133">**Library:** CorGuids.lib</span></span>  
  
<span data-ttu-id="73250-134">**.NET Versions-cadre:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73250-134">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73250-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="73250-135">See also</span></span>

- [<span data-ttu-id="73250-136">Énumérations de profilage</span><span class="sxs-lookup"><span data-stu-id="73250-136">Profiling Enumerations</span></span>](profiling-enumerations.md)
- [<span data-ttu-id="73250-137">COR_PRF_MONITOR, énumération</span><span class="sxs-lookup"><span data-stu-id="73250-137">COR_PRF_MONITOR Enumeration</span></span>](cor-prf-monitor-enumeration.md)
- [<span data-ttu-id="73250-138">ICorProfilerInfo5, interface</span><span class="sxs-lookup"><span data-stu-id="73250-138">ICorProfilerInfo5 Interface</span></span>](icorprofilerinfo5-interface.md)
