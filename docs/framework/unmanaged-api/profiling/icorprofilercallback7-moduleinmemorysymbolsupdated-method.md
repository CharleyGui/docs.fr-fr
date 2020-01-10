---
title: 'ICorProfilerCallback7 :: ModuleInMemorySymbolsUpdated, méthode'
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback7.ModuleInMemorySymbolsUpdated
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: f362a896-3247-4894-9727-e48dbbcd2c78
ms.openlocfilehash: b9e404de96fa42509144904f5b2ff58e341578a9
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740441"
---
# <a name="icorprofilercallback7moduleinmemorysymbolsupdated-method"></a><span data-ttu-id="ee86b-102">ICorProfilerCallback7 :: ModuleInMemorySymbolsUpdated, méthode</span><span class="sxs-lookup"><span data-stu-id="ee86b-102">ICorProfilerCallback7::ModuleInMemorySymbolsUpdated Method</span></span>
<span data-ttu-id="ee86b-103">[Prise en charge dans le .NET Framework 4.6.1 et versions ultérieures]</span><span class="sxs-lookup"><span data-stu-id="ee86b-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="ee86b-104">Notifie le profileur chaque fois que le flux de symboles associé à un module en mémoire est mis à jour.</span><span class="sxs-lookup"><span data-stu-id="ee86b-104">Notifies the profiler whenever the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee86b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ee86b-105">Syntax</span></span>  
  
```cpp  
HRESULT ModuleInMemorySymbolsUpdated(  
     ModuleID moduleId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ee86b-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="ee86b-106">Parameters</span></span>  
 <span data-ttu-id="ee86b-107">[in] `moduleId`</span><span class="sxs-lookup"><span data-stu-id="ee86b-107">[in] `moduleId`</span></span>  
 <span data-ttu-id="ee86b-108">Identificateur du module en mémoire dont le flux de symboles est mis à jour.</span><span class="sxs-lookup"><span data-stu-id="ee86b-108">The identifier of the in-memory module whose symbol stream is updated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ee86b-109">Notes</span><span class="sxs-lookup"><span data-stu-id="ee86b-109">Remarks</span></span>  
 <span data-ttu-id="ee86b-110">Ce rappel est contrôlé en définissant l’indicateur de masque d’événement [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) lors de l’appel de la méthode [ICorProfilerCallback5 :: SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ee86b-110">This callback is controlled by setting the [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) event mask flag when calling the [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ee86b-111">Cet événement n’est pas actuellement déclenché pour les symboles créés ou modifiés implicitement via des API <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="ee86b-111">This event is not currently raised for symbols implicitly created or modified via <xref:System.Reflection.Emit> APIs.</span></span>  
  
 <span data-ttu-id="ee86b-112">Même lorsque les symboles sont fournis au début d’un appel à l’une des surcharges des méthodes de <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> managées qui incluent un argument `rawSymbolStore` pour spécifier les symboles de l’assembly, le runtime peut ne pas associer les données symboliques au module tant que le rappel de [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) n’a pas eu lieu.</span><span class="sxs-lookup"><span data-stu-id="ee86b-112">Even when symbols are provided up front in a call to one of the overloads of the managed <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> methods that includes a `rawSymbolStore` argument to specify the symbols for the assembly, the runtime may not actually associate the symbolic data with the module until after the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback has occurred.</span></span> <span data-ttu-id="ee86b-113">Cet événement permet ensuite de collecter des symboles pour ces modules.</span><span class="sxs-lookup"><span data-stu-id="ee86b-113">This event provides a later opportunity to collect symbols for such modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee86b-114">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="ee86b-114">Requirements</span></span>  
 <span data-ttu-id="ee86b-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee86b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee86b-116">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ee86b-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ee86b-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ee86b-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee86b-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee86b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee86b-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ee86b-119">See also</span></span>

- [<span data-ttu-id="ee86b-120">ModuleLoadFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="ee86b-120">ModuleLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
- [<span data-ttu-id="ee86b-121">SetEventMask2, méthode</span><span class="sxs-lookup"><span data-stu-id="ee86b-121">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
- [<span data-ttu-id="ee86b-122">ICorProfilerCallback7, interface</span><span class="sxs-lookup"><span data-stu-id="ee86b-122">ICorProfilerCallback7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)
