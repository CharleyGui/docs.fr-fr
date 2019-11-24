---
title: FunctionLeave3WithInfo, fonction
ms.date: 03/30/2017
api_name:
- FunctionLeave3WithInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave3WithInfo
helpviewer_keywords:
- FunctionLeave3WithInfo function [.NET Framework profiling]
ms.assetid: 5fa68a67-ced6-41c6-a2c0-467060fd0692
topic_type:
- apiref
ms.openlocfilehash: a62f402fbfae6188ab0423ea7a55a4dfc6cb4112
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427404"
---
# <a name="functionleave3withinfo-function"></a><span data-ttu-id="54f2e-102">FunctionLeave3WithInfo, fonction</span><span class="sxs-lookup"><span data-stu-id="54f2e-102">FunctionLeave3WithInfo Function</span></span>
<span data-ttu-id="54f2e-103">Notifies the profiler that control is being returned from a function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionLeave3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) to retrieve the stack frame and the return value.</span><span class="sxs-lookup"><span data-stu-id="54f2e-103">Notifies the profiler that control is being returned from a function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionLeave3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) to retrieve the stack frame and the return value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54f2e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="54f2e-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="54f2e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="54f2e-105">Parameters</span></span>  
 `functionIDOrClientID`  
 <span data-ttu-id="54f2e-106">[in] The identifier of the function from which control is returned.</span><span class="sxs-lookup"><span data-stu-id="54f2e-106">[in] The identifier of the function from which control is returned.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="54f2e-107">[in] Handle opaque qui représente des informations sur un frame de pile donné.</span><span class="sxs-lookup"><span data-stu-id="54f2e-107">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="54f2e-108">This handle is valid only during the callback to which it is passed.</span><span class="sxs-lookup"><span data-stu-id="54f2e-108">This handle is valid only during the callback to which it is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="54f2e-109">Notes</span><span class="sxs-lookup"><span data-stu-id="54f2e-109">Remarks</span></span>  
 <span data-ttu-id="54f2e-110">The `FunctionLeave3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionLeave3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) to inspect the return value.</span><span class="sxs-lookup"><span data-stu-id="54f2e-110">The `FunctionLeave3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionLeave3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) to inspect the return value.</span></span> <span data-ttu-id="54f2e-111">To access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag has to be set.</span><span class="sxs-lookup"><span data-stu-id="54f2e-111">To access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag has to be set.</span></span> <span data-ttu-id="54f2e-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span><span class="sxs-lookup"><span data-stu-id="54f2e-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="54f2e-113">The `FunctionLeave3WithInfo` function is a callback; you must implement it.</span><span class="sxs-lookup"><span data-stu-id="54f2e-113">The `FunctionLeave3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="54f2e-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span><span class="sxs-lookup"><span data-stu-id="54f2e-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="54f2e-115">The execution engine does not save any registers before calling this function.</span><span class="sxs-lookup"><span data-stu-id="54f2e-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="54f2e-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span><span class="sxs-lookup"><span data-stu-id="54f2e-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="54f2e-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span><span class="sxs-lookup"><span data-stu-id="54f2e-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="54f2e-118">The implementation of `FunctionLeave3WithInfo` should not block, because it will delay garbage collection.</span><span class="sxs-lookup"><span data-stu-id="54f2e-118">The implementation of `FunctionLeave3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="54f2e-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span><span class="sxs-lookup"><span data-stu-id="54f2e-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="54f2e-120">If a garbage collection is attempted, the runtime will block until `FunctionLeave3WithInfo` returns.</span><span class="sxs-lookup"><span data-stu-id="54f2e-120">If a garbage collection is attempted, the runtime will block until `FunctionLeave3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="54f2e-121">The `FunctionLeave3WithInfo` function must not call into managed code or cause a managed memory allocation in any way.</span><span class="sxs-lookup"><span data-stu-id="54f2e-121">The `FunctionLeave3WithInfo` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54f2e-122">spécifications</span><span class="sxs-lookup"><span data-stu-id="54f2e-122">Requirements</span></span>  
 <span data-ttu-id="54f2e-123">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54f2e-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54f2e-124">**Header:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="54f2e-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="54f2e-125">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="54f2e-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="54f2e-126">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54f2e-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54f2e-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="54f2e-127">See also</span></span>

- [<span data-ttu-id="54f2e-128">GetFunctionLeave3Info</span><span class="sxs-lookup"><span data-stu-id="54f2e-128">GetFunctionLeave3Info</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md)
- [<span data-ttu-id="54f2e-129">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="54f2e-129">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="54f2e-130">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="54f2e-130">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="54f2e-131">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="54f2e-131">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="54f2e-132">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="54f2e-132">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="54f2e-133">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="54f2e-133">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="54f2e-134">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="54f2e-134">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="54f2e-135">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="54f2e-135">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="54f2e-136">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="54f2e-136">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="54f2e-137">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="54f2e-137">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="54f2e-138">Fonctions statiques globales de profilage</span><span class="sxs-lookup"><span data-stu-id="54f2e-138">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
