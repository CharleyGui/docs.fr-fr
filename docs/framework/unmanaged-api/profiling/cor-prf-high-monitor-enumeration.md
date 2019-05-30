---
title: COR_PRF_MODULE_FLAGS, énumération
ms.date: 04/10/2018
ms.assetid: 3ba543d8-15e5-4322-b6e7-1ebfc92ed7dd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e365dff7c56ddca1d05f2e16605078ef46e4e2af
ms.sourcegitcommit: 26f4a7697c32978f6a328c89dc4ea87034065989
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66251155"
---
# <a name="corprfhighmonitor-enumeration"></a><span data-ttu-id="5cf8c-102">COR_PRF_MODULE_FLAGS, énumération</span><span class="sxs-lookup"><span data-stu-id="5cf8c-102">COR_PRF_HIGH_MONITOR Enumeration</span></span>
<span data-ttu-id="5cf8c-103">[Pris en charge dans .NET Framework 4.5.2 et ultérieur]</span><span class="sxs-lookup"><span data-stu-id="5cf8c-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="5cf8c-104">Fournit des indicateurs en plus de celles disponibles dans le [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) énumération le profileur peut spécifier à la [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) méthode lors de son chargement.</span><span class="sxs-lookup"><span data-stu-id="5cf8c-104">Provides flags in addition to those found in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration that the profiler can specify to the [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method when it is loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cf8c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5cf8c-105">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_HIGH_MONITOR_NONE                     = 0x00000000,  
    COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES          = 0x00000001,  
    COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED        = 0x00000002,     
    COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS = 0x00000004,    
    COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE            = 0,  
    COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH           = COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | 
                                                    COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS,  
    COR_PRF_HIGH_MONITOR_IMMUTABLE                = 0  
} COR_PRF_HIGH_MONITOR;  
```  
  
## <a name="members"></a><span data-ttu-id="5cf8c-106">Membres</span><span class="sxs-lookup"><span data-stu-id="5cf8c-106">Members</span></span>  
  
|<span data-ttu-id="5cf8c-107">Membre</span><span class="sxs-lookup"><span data-stu-id="5cf8c-107">Member</span></span>|<span data-ttu-id="5cf8c-108">Description</span><span class="sxs-lookup"><span data-stu-id="5cf8c-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|<span data-ttu-id="5cf8c-109">Aucun indicateur n'est défini.</span><span class="sxs-lookup"><span data-stu-id="5cf8c-109">No flags are set.</span></span>|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|<span data-ttu-id="5cf8c-110">Contrôles le [ICorProfilerCallback6::GetAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) rappel pour l’ajout de références d’assembly pendant le parcours de fermeture de référence assembly CLR.</span><span class="sxs-lookup"><span data-stu-id="5cf8c-110">Controls the [ICorProfilerCallback6::GetAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback for adding assembly references during the CLR assembly reference closure walk.</span></span>|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|<span data-ttu-id="5cf8c-111">Contrôles le [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) rappel des mises à jour dans le flux de symbole associé à un module en mémoire.</span><span class="sxs-lookup"><span data-stu-id="5cf8c-111">Controls the [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) callback for updates to the symbol stream associated with an in-memory module.</span></span>|  
|`COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`|<span data-ttu-id="5cf8c-112">Contrôles le [ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) rappel pour indiquer qu’une méthode dynamique a été garbage collectées et déchargé.</span><span class="sxs-lookup"><span data-stu-id="5cf8c-112">Controls the [ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) callback for indicating when a dynamic method has been garbage collected and unloaded.</span></span> <br/> [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]|   
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|<span data-ttu-id="5cf8c-113">Représente tous les indicateurs `COR_PRF_HIGH_MONITOR` qui requièrent des images à profil optimisé.</span><span class="sxs-lookup"><span data-stu-id="5cf8c-113">Represents all `COR_PRF_HIGH_MONITOR` flags that require profile-enhanced images.</span></span> <span data-ttu-id="5cf8c-114">Il correspond à la `COR_PRF_REQUIRE_PROFILE_IMAGE` indicateur dans le [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) énumération.</span><span class="sxs-lookup"><span data-stu-id="5cf8c-114">It corresponds to the `COR_PRF_REQUIRE_PROFILE_IMAGE` flag in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|<span data-ttu-id="5cf8c-115">Représente tous les indicateurs `COR_PRF_HIGH_MONITOR` qui peuvent être définis une fois que le profileur est attaché à une application en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="5cf8c-115">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set after the profiler is attached to a running app.</span></span>|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|<span data-ttu-id="5cf8c-116">Représente tous les indicateurs `COR_PRF_HIGH_MONITOR` qui peuvent être définis uniquement lors de l'initialisation.</span><span class="sxs-lookup"><span data-stu-id="5cf8c-116">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set only during initialization.</span></span> <span data-ttu-id="5cf8c-117">Les tentatives de modification d'un ou plusieurs de ces indicateurs autre part génèrent une valeur `HRESULT`, qui indique un échec.</span><span class="sxs-lookup"><span data-stu-id="5cf8c-117">Trying to change any of these flags elsewhere results in an `HRESULT` value that indicates failure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5cf8c-118">Notes</span><span class="sxs-lookup"><span data-stu-id="5cf8c-118">Remarks</span></span>  
 <span data-ttu-id="5cf8c-119">Le `COR_PRF_HIGH_MONITOR` indicateurs sont utilisés avec la `pdwEventsHigh` paramètre de la [ICorProfilerInfo5::GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) et [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) méthodes.</span><span class="sxs-lookup"><span data-stu-id="5cf8c-119">The `COR_PRF_HIGH_MONITOR` flags are used with the `pdwEventsHigh` parameter of the [ICorProfilerInfo5::GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) and [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) methods.</span></span>  
  
<span data-ttu-id="5cf8c-120">En commençant par le .NET Framework 4.6.1, la valeur de la `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` est passée de 0 à `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0 x 00000002).</span><span class="sxs-lookup"><span data-stu-id="5cf8c-120">Starting with the .NET Framework 4.6.1, the value of the `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` changed from 0 to `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002).</span></span> <span data-ttu-id="5cf8c-121">À compter de .NET Framework 4.7.2, sa valeur a été remplacée par `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` à `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`.</span><span class="sxs-lookup"><span data-stu-id="5cf8c-121">Starting with the .NET Framework 4.7.2, its value changed from `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` to `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`.</span></span>   

<span data-ttu-id="5cf8c-122">`COR_PRF_HIGH_MONITOR_IMMUTABLE` est destiné à être un masque de bits qui représente tous les indicateurs qui peuvent uniquement être définies lors de l’initialisation.</span><span class="sxs-lookup"><span data-stu-id="5cf8c-122">`COR_PRF_HIGH_MONITOR_IMMUTABLE` is intended to be a bitmask that represents all flags that can only be set during initialization.</span></span> <span data-ttu-id="5cf8c-123">Essayez de modifier un de ces indicateurs autre part génèrent un échec `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="5cf8c-123">Trying to change any of these flags elsewhere results in a failed `HRESULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="5cf8c-124">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5cf8c-124">Requirements</span></span>  
 <span data-ttu-id="5cf8c-125">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5cf8c-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cf8c-126">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5cf8c-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5cf8c-127">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5cf8c-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5cf8c-128">**Versions du .NET Framework :** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5cf8c-128">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cf8c-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5cf8c-129">See also</span></span>

- [<span data-ttu-id="5cf8c-130">Énumérations de profilage</span><span class="sxs-lookup"><span data-stu-id="5cf8c-130">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
- [<span data-ttu-id="5cf8c-131">COR_PRF_MONITOR, énumération</span><span class="sxs-lookup"><span data-stu-id="5cf8c-131">COR_PRF_MONITOR Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)
- [<span data-ttu-id="5cf8c-132">ICorProfilerInfo5, interface</span><span class="sxs-lookup"><span data-stu-id="5cf8c-132">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
