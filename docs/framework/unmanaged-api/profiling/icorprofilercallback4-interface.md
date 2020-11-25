---
title: ICorProfilerCallback4, interface
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4
helpviewer_keywords:
- ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 665f3cfc-cd6f-4880-906c-ea65ad384783
topic_type:
- apiref
ms.openlocfilehash: 942ee8234b79c6579acc009960f4571801fc3185
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730290"
---
# <a name="icorprofilercallback4-interface"></a><span data-ttu-id="f7e55-102">ICorProfilerCallback4, interface</span><span class="sxs-lookup"><span data-stu-id="f7e55-102">ICorProfilerCallback4 Interface</span></span>

<span data-ttu-id="f7e55-103">Fournit des méthodes de rappel que le common language runtime (CLR) utilise pour communiquer des informations au profileur.</span><span class="sxs-lookup"><span data-stu-id="f7e55-103">Provides callback methods that the common language runtime (CLR) uses to communicate information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f7e55-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="f7e55-104">Methods</span></span>  
  
|<span data-ttu-id="f7e55-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="f7e55-105">Method</span></span>|<span data-ttu-id="f7e55-106">Description</span><span class="sxs-lookup"><span data-stu-id="f7e55-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f7e55-107">GetReJITParameters, méthode</span><span class="sxs-lookup"><span data-stu-id="f7e55-107">GetReJITParameters Method</span></span>](icorprofilercallback4-getrejitparameters-method.md)|<span data-ttu-id="f7e55-108">Permet au profileur de code de définir d’autres indicateurs de génération de code pour un nouveau corps de méthode recompilée.</span><span class="sxs-lookup"><span data-stu-id="f7e55-108">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>|  
|[<span data-ttu-id="f7e55-109">MovedReferences2, méthode</span><span class="sxs-lookup"><span data-stu-id="f7e55-109">MovedReferences2 Method</span></span>](icorprofilercallback4-movedreferences2-method.md)|<span data-ttu-id="f7e55-110">Signale la nouvelle disposition d’objets dans le tas à la suite d’un compactage garbage collection.</span><span class="sxs-lookup"><span data-stu-id="f7e55-110">Reports the new layout of objects in the heap as a result of a compacting garbage collection.</span></span>|  
|[<span data-ttu-id="f7e55-111">ReJITCompilationFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="f7e55-111">ReJITCompilationFinished Method</span></span>](icorprofilercallback4-rejitcompilationfinished-method.md)|<span data-ttu-id="f7e55-112">Notifie le profileur que le compilateur juste-à-temps (JIT) a terminé la recompilation d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="f7e55-112">Notifies the profiler that the just-in-time (JIT) compiler has finished the recompilation of a function.</span></span>|  
|[<span data-ttu-id="f7e55-113">ReJITCompilationStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="f7e55-113">ReJITCompilationStarted Method</span></span>](icorprofilercallback4-rejitcompilationstarted-method.md)|<span data-ttu-id="f7e55-114">Notifie le profileur que le compilateur juste-à-temps (JIT) a commencé à recompiler une fonction.</span><span class="sxs-lookup"><span data-stu-id="f7e55-114">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>|  
|[<span data-ttu-id="f7e55-115">ReJITError, méthode</span><span class="sxs-lookup"><span data-stu-id="f7e55-115">ReJITError Method</span></span>](icorprofilercallback4-rejiterror-method.md)|<span data-ttu-id="f7e55-116">Signale une erreur rencontrée lors du traitement d’une demande de recompilation.</span><span class="sxs-lookup"><span data-stu-id="f7e55-116">Reports an error encountered while processing a recompile request.</span></span>|  
|[<span data-ttu-id="f7e55-117">SurvivingReferences2, méthode</span><span class="sxs-lookup"><span data-stu-id="f7e55-117">SurvivingReferences2 Method</span></span>](icorprofilercallback4-survivingreferences2-method.md)|<span data-ttu-id="f7e55-118">Signale la disposition d'objets dans le tas suite à un garbage collection de non-compactage.</span><span class="sxs-lookup"><span data-stu-id="f7e55-118">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7e55-119">Notes</span><span class="sxs-lookup"><span data-stu-id="f7e55-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7e55-120">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f7e55-120">Requirements</span></span>  

 <span data-ttu-id="f7e55-121">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7e55-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7e55-122">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f7e55-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f7e55-123">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7e55-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7e55-124">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7e55-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7e55-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7e55-125">See also</span></span>

- [<span data-ttu-id="f7e55-126">ICorProfilerCallback2, interface</span><span class="sxs-lookup"><span data-stu-id="f7e55-126">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
- [<span data-ttu-id="f7e55-127">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="f7e55-127">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="f7e55-128">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="f7e55-128">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
