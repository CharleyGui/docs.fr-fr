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
ms.openlocfilehash: 4c5b8f18424ba54d9e8e14ba0a518a89e0d54796
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439465"
---
# <a name="icorprofilercallback3profilerattachcomplete-method"></a><span data-ttu-id="ea117-102">ICorProfilerCallback3::ProfilerAttachComplete, méthode</span><span class="sxs-lookup"><span data-stu-id="ea117-102">ICorProfilerCallback3::ProfilerAttachComplete Method</span></span>
<span data-ttu-id="ea117-103">Appelée par le common language runtime (CLR) pour indiquer que le profileur peut désormais appeler les méthodes de rattrapage [ICorProfilerInfo3 :: EnumJITedFunctions,](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) et [Icorprofilerinfo3 :: EnumModules](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ea117-103">Called by the common language runtime (CLR) to indicate that the profiler can now call the [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) and [ICorProfilerInfo3::EnumModules](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md) catch-up methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea117-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ea117-104">Syntax</span></span>  
  
```cpp  
HRESULT ProfilerAttachComplete ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="ea117-105">Notes</span><span class="sxs-lookup"><span data-stu-id="ea117-105">Remarks</span></span>  
 <span data-ttu-id="ea117-106">Le rappel `ProfilerAttachComplete` est émis après l’appel de la méthode [ICorProfilerCallback3 :: InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ea117-106">The `ProfilerAttachComplete` callback is issued after the [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) method is called.</span></span> <span data-ttu-id="ea117-107">Il indique ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="ea117-107">It indicates the following:</span></span>  
  
- <span data-ttu-id="ea117-108">Les rappels demandés par le profileur dans `InitializeForAttach` ont été activés.</span><span class="sxs-lookup"><span data-stu-id="ea117-108">The callbacks that were requested by the profiler in `InitializeForAttach` have been activated.</span></span>  
  
- <span data-ttu-id="ea117-109">Le profileur peut désormais exécuter un rattrapage sur les ID associés sans risquer de manquer des notifications.</span><span class="sxs-lookup"><span data-stu-id="ea117-109">The profiler can now perform catch-up on the associated IDs without being concerned about missing notifications.</span></span>  
  
 <span data-ttu-id="ea117-110">Le CLR ignore la valeur de retour de ce rappel.</span><span class="sxs-lookup"><span data-stu-id="ea117-110">The CLR ignores the return value from this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea117-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ea117-111">Requirements</span></span>  
 <span data-ttu-id="ea117-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea117-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea117-113">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ea117-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ea117-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ea117-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea117-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea117-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea117-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ea117-116">See also</span></span>

- [<span data-ttu-id="ea117-117">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="ea117-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="ea117-118">ICorProfilerInfo3, interface</span><span class="sxs-lookup"><span data-stu-id="ea117-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="ea117-119">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="ea117-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="ea117-120">Profilage</span><span class="sxs-lookup"><span data-stu-id="ea117-120">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
