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
ms.openlocfilehash: ad9c5445cbef0be7919570db64b027556d923752
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865569"
---
# <a name="icorprofilercallback3-interface"></a><span data-ttu-id="84293-102">ICorProfilerCallback3, interface</span><span class="sxs-lookup"><span data-stu-id="84293-102">ICorProfilerCallback3 Interface</span></span>
<span data-ttu-id="84293-103">Fournit des méthodes de rappel que le common language runtime (CLR) utilise pour communiquer les informations d’état d’attachement et de détachement au profileur.</span><span class="sxs-lookup"><span data-stu-id="84293-103">Provides callback methods that the common language runtime (CLR) uses to communicate attach and detach state information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="84293-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="84293-104">Methods</span></span>  
  
|<span data-ttu-id="84293-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="84293-105">Method</span></span>|<span data-ttu-id="84293-106">Description</span><span class="sxs-lookup"><span data-stu-id="84293-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="84293-107">InitializeForAttach, méthode</span><span class="sxs-lookup"><span data-stu-id="84293-107">InitializeForAttach Method</span></span>](icorprofilercallback3-initializeforattach-method.md)|<span data-ttu-id="84293-108">Appelée par le CLR pour permettre au profileur d’initialiser son état après une opération d’attachement.</span><span class="sxs-lookup"><span data-stu-id="84293-108">Called by the CLR to give the profiler an opportunity to initialize its state after an attach operation.</span></span>|  
|[<span data-ttu-id="84293-109">ProfilerAttachComplete, méthode</span><span class="sxs-lookup"><span data-stu-id="84293-109">ProfilerAttachComplete Method</span></span>](icorprofilercallback3-profilerattachcomplete-method.md)|<span data-ttu-id="84293-110">Appelée par le CLR pour indiquer que le profileur peut maintenant appeler les méthodes de rattrapage.</span><span class="sxs-lookup"><span data-stu-id="84293-110">Called by the CLR to indicate that the profiler can now call the catch-up methods.</span></span>|  
|[<span data-ttu-id="84293-111">ProfilerDetachSucceeded, méthode</span><span class="sxs-lookup"><span data-stu-id="84293-111">ProfilerDetachSucceeded Method</span></span>](icorprofilercallback3-profilerdetachsucceeded-method.md)|<span data-ttu-id="84293-112">Indique au profileur que le Common Language Runtime (CLR) est sur le point de décharger sa DLL.</span><span class="sxs-lookup"><span data-stu-id="84293-112">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84293-113">Notes</span><span class="sxs-lookup"><span data-stu-id="84293-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84293-114">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="84293-114">Requirements</span></span>  
 <span data-ttu-id="84293-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84293-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84293-116">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="84293-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="84293-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="84293-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84293-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84293-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84293-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="84293-119">See also</span></span>

- [<span data-ttu-id="84293-120">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="84293-120">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="84293-121">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="84293-121">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="84293-122">ICorProfilerCallback2, interface</span><span class="sxs-lookup"><span data-stu-id="84293-122">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
- [<span data-ttu-id="84293-123">ICorProfilerCallback4, interface</span><span class="sxs-lookup"><span data-stu-id="84293-123">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
