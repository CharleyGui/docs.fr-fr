---
title: ICorProfilerCallback3, interface
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3
helpviewer_keywords:
- ICorProfilerCallback3 interface [.NET Framework profiling]
ms.assetid: be83af41-3dec-4c77-8529-9dd6b8042af6
topic_type:
- apiref
ms.openlocfilehash: 25d674a143019ac5d724e36f03f36c79602b1e11
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439508"
---
# <a name="icorprofilercallback3-interface"></a><span data-ttu-id="ab922-102">ICorProfilerCallback3, interface</span><span class="sxs-lookup"><span data-stu-id="ab922-102">ICorProfilerCallback3 Interface</span></span>
<span data-ttu-id="ab922-103">Provides callback methods that the common language runtime (CLR) uses to communicate attach and detach state information to the profiler.</span><span class="sxs-lookup"><span data-stu-id="ab922-103">Provides callback methods that the common language runtime (CLR) uses to communicate attach and detach state information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ab922-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="ab922-104">Methods</span></span>  
  
|<span data-ttu-id="ab922-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="ab922-105">Method</span></span>|<span data-ttu-id="ab922-106">Description</span><span class="sxs-lookup"><span data-stu-id="ab922-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ab922-107">InitializeForAttach, méthode</span><span class="sxs-lookup"><span data-stu-id="ab922-107">InitializeForAttach Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md)|<span data-ttu-id="ab922-108">Called by the CLR to give the profiler an opportunity to initialize its state after an attach operation.</span><span class="sxs-lookup"><span data-stu-id="ab922-108">Called by the CLR to give the profiler an opportunity to initialize its state after an attach operation.</span></span>|  
|[<span data-ttu-id="ab922-109">ProfilerAttachComplete, méthode</span><span class="sxs-lookup"><span data-stu-id="ab922-109">ProfilerAttachComplete Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-profilerattachcomplete-method.md)|<span data-ttu-id="ab922-110">Called by the CLR to indicate that the profiler can now call the catch-up methods.</span><span class="sxs-lookup"><span data-stu-id="ab922-110">Called by the CLR to indicate that the profiler can now call the catch-up methods.</span></span>|  
|[<span data-ttu-id="ab922-111">ProfilerDetachSucceeded, méthode</span><span class="sxs-lookup"><span data-stu-id="ab922-111">ProfilerDetachSucceeded Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-profilerdetachsucceeded-method.md)|<span data-ttu-id="ab922-112">Indique au profileur que le Common Language Runtime (CLR) est sur le point de décharger sa DLL.</span><span class="sxs-lookup"><span data-stu-id="ab922-112">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab922-113">Notes</span><span class="sxs-lookup"><span data-stu-id="ab922-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab922-114">spécifications</span><span class="sxs-lookup"><span data-stu-id="ab922-114">Requirements</span></span>  
 <span data-ttu-id="ab922-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab922-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab922-116">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ab922-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ab922-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab922-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab922-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab922-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab922-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab922-119">See also</span></span>

- [<span data-ttu-id="ab922-120">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="ab922-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="ab922-121">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="ab922-121">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="ab922-122">ICorProfilerCallback2, interface</span><span class="sxs-lookup"><span data-stu-id="ab922-122">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [<span data-ttu-id="ab922-123">ICorProfilerCallback4, interface</span><span class="sxs-lookup"><span data-stu-id="ab922-123">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
