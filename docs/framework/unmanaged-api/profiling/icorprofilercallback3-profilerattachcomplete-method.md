---
title: ICorProfilerCallback3::ProfilerAttachComplete, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.ProfilerAttachComplete Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::ProfilerAttachComplete
helpviewer_keywords:
- ProfilerAttachComplete method [.NET Framework profiling]
- ICorProfilerCallback3::ProfilerAttachComplete method [.NET Framework profiling]
ms.assetid: 257d6076-06e0-4d93-bb33-651fbb2b92d7
topic_type:
- apiref
ms.openlocfilehash: 8168f6f1079ec34b9fb53a485da0f32175446719
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865426"
---
# <a name="icorprofilercallback3profilerattachcomplete-method"></a><span data-ttu-id="ce056-102">ICorProfilerCallback3::ProfilerAttachComplete, méthode</span><span class="sxs-lookup"><span data-stu-id="ce056-102">ICorProfilerCallback3::ProfilerAttachComplete Method</span></span>
<span data-ttu-id="ce056-103">Appelée par le common language runtime (CLR) pour indiquer que le profileur peut désormais appeler les méthodes de rattrapage [ICorProfilerInfo3 :: EnumJITedFunctions,](icorprofilerinfo3-enumjitedfunctions-method.md) et [Icorprofilerinfo3 :: EnumModules](icorprofilerinfo3-enummodules-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ce056-103">Called by the common language runtime (CLR) to indicate that the profiler can now call the [ICorProfilerInfo3::EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) and [ICorProfilerInfo3::EnumModules](icorprofilerinfo3-enummodules-method.md) catch-up methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce056-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ce056-104">Syntax</span></span>  
  
```cpp  
HRESULT ProfilerAttachComplete ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="ce056-105">Notes</span><span class="sxs-lookup"><span data-stu-id="ce056-105">Remarks</span></span>  
 <span data-ttu-id="ce056-106">Le rappel `ProfilerAttachComplete` est émis après l’appel de la méthode [ICorProfilerCallback3 :: InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ce056-106">The `ProfilerAttachComplete` callback is issued after the [ICorProfilerCallback3::InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) method is called.</span></span> <span data-ttu-id="ce056-107">Il indique ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="ce056-107">It indicates the following:</span></span>  
  
- <span data-ttu-id="ce056-108">Les rappels demandés par le profileur dans `InitializeForAttach` ont été activés.</span><span class="sxs-lookup"><span data-stu-id="ce056-108">The callbacks that were requested by the profiler in `InitializeForAttach` have been activated.</span></span>  
  
- <span data-ttu-id="ce056-109">Le profileur peut désormais exécuter un rattrapage sur les ID associés sans risquer de manquer des notifications.</span><span class="sxs-lookup"><span data-stu-id="ce056-109">The profiler can now perform catch-up on the associated IDs without being concerned about missing notifications.</span></span>  
  
 <span data-ttu-id="ce056-110">Le CLR ignore la valeur de retour de ce rappel.</span><span class="sxs-lookup"><span data-stu-id="ce056-110">The CLR ignores the return value from this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce056-111">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="ce056-111">Requirements</span></span>  
 <span data-ttu-id="ce056-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce056-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce056-113">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ce056-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ce056-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ce056-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce056-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce056-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce056-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce056-116">See also</span></span>

- [<span data-ttu-id="ce056-117">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="ce056-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="ce056-118">ICorProfilerInfo3, interface</span><span class="sxs-lookup"><span data-stu-id="ce056-118">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="ce056-119">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="ce056-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="ce056-120">Profilage</span><span class="sxs-lookup"><span data-stu-id="ce056-120">Profiling</span></span>](index.md)
