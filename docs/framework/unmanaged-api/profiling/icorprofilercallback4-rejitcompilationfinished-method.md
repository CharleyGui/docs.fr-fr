---
title: ICorProfilerCallback4::ReJITCompilationFinished, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITCompilationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITCompilationFinished
helpviewer_keywords:
- ICorProfilerCallback4::ReJITCompilationFinished method [.NET Framework profiling]
- ReJITCompilationFinished method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 3b5cff02-2005-44eb-a2bc-50214c4b0e1d
topic_type:
- apiref
ms.openlocfilehash: 9a42198b1c89dbc47c6659564cf32738b683697b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439304"
---
# <a name="icorprofilercallback4rejitcompilationfinished-method"></a><span data-ttu-id="70873-102">ICorProfilerCallback4::ReJITCompilationFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="70873-102">ICorProfilerCallback4::ReJITCompilationFinished Method</span></span>
<span data-ttu-id="70873-103">Notifies the profiler that the just-in-time (JIT) compiler has finished recompiling a function.</span><span class="sxs-lookup"><span data-stu-id="70873-103">Notifies the profiler that the just-in-time (JIT) compiler has finished recompiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70873-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70873-104">Syntax</span></span>  
  
```cpp  
HRESULT ReJITCompilationFinished(  
    [in] FunctionID functionId,    [in] ReJITID rejitId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="70873-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="70873-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="70873-106">[in] The ID of the function that was recompiled.</span><span class="sxs-lookup"><span data-stu-id="70873-106">[in] The ID of the function that was recompiled.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="70873-107">[in] Identité de la fonction recompilée juste-à-temps.</span><span class="sxs-lookup"><span data-stu-id="70873-107">[in] The identity of the JIT-recompiled function.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="70873-108">[in] A value that indicates whether the JIT recompilation was successful.</span><span class="sxs-lookup"><span data-stu-id="70873-108">[in] A value that indicates whether the JIT recompilation was successful.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="70873-109">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span><span class="sxs-lookup"><span data-stu-id="70873-109">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  
  
 <span data-ttu-id="70873-110">A value of `true` does not harm the runtime, but can affect the profiling results.</span><span class="sxs-lookup"><span data-stu-id="70873-110">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70873-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="70873-111">Requirements</span></span>  
 <span data-ttu-id="70873-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70873-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70873-113">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="70873-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="70873-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="70873-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="70873-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70873-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70873-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="70873-116">See also</span></span>

- [<span data-ttu-id="70873-117">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="70873-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="70873-118">ICorProfilerCallback4, interface</span><span class="sxs-lookup"><span data-stu-id="70873-118">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [<span data-ttu-id="70873-119">JITCompilationStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="70873-119">JITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)
- [<span data-ttu-id="70873-120">ReJITCompilationStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="70873-120">ReJITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)
