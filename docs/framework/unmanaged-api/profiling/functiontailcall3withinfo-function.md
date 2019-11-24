---
title: FunctionTailcall3WithInfo, fonction
ms.date: 03/30/2017
api_name:
- FunctionTailcall3WithInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall3WithInfo
helpviewer_keywords:
- FunctionTailcall3WithInfo function [.NET Framework profiling]
ms.assetid: 46380fcc-0198-43ae-a1f5-2d4939425886
topic_type:
- apiref
ms.openlocfilehash: 202aed64de78675c79f998afb4483e0d19b811de
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445967"
---
# <a name="functiontailcall3withinfo-function"></a><span data-ttu-id="91cbb-102">FunctionTailcall3WithInfo, fonction</span><span class="sxs-lookup"><span data-stu-id="91cbb-102">FunctionTailcall3WithInfo Function</span></span>
<span data-ttu-id="91cbb-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionTailcall3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) to retrieve the stack frame.</span><span class="sxs-lookup"><span data-stu-id="91cbb-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionTailcall3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) to retrieve the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91cbb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="91cbb-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionTailcall3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91cbb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="91cbb-105">Parameters</span></span>  
 `functionIDOrClientID`  
 <span data-ttu-id="91cbb-106">[in] The identifier of the currently executing function that is about to make a tail call.</span><span class="sxs-lookup"><span data-stu-id="91cbb-106">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="91cbb-107">[in] Handle opaque qui représente des informations sur un frame de pile donné.</span><span class="sxs-lookup"><span data-stu-id="91cbb-107">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="91cbb-108">This handle is valid only during the callback to which it is passed.</span><span class="sxs-lookup"><span data-stu-id="91cbb-108">This handle is valid only during the callback to which it is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91cbb-109">Notes</span><span class="sxs-lookup"><span data-stu-id="91cbb-109">Remarks</span></span>  
 <span data-ttu-id="91cbb-110">The `FunctionTailcall3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionTailcall3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) to inspect the stack frame.</span><span class="sxs-lookup"><span data-stu-id="91cbb-110">The `FunctionTailcall3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionTailcall3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) to inspect the stack frame.</span></span> <span data-ttu-id="91cbb-111">To access stack frame information, the `COR_PRF_ENABLE_FRAME_INFO` flag has to be set.</span><span class="sxs-lookup"><span data-stu-id="91cbb-111">To access stack frame information, the `COR_PRF_ENABLE_FRAME_INFO` flag has to be set.</span></span> <span data-ttu-id="91cbb-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span><span class="sxs-lookup"><span data-stu-id="91cbb-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="91cbb-113">The `FunctionTailcall3WithInfo` function is a callback; you must implement it.</span><span class="sxs-lookup"><span data-stu-id="91cbb-113">The `FunctionTailcall3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="91cbb-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span><span class="sxs-lookup"><span data-stu-id="91cbb-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="91cbb-115">The execution engine does not save any registers before calling this function.</span><span class="sxs-lookup"><span data-stu-id="91cbb-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="91cbb-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span><span class="sxs-lookup"><span data-stu-id="91cbb-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="91cbb-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span><span class="sxs-lookup"><span data-stu-id="91cbb-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="91cbb-118">The implementation of `FunctionTailcall3WithInfo` should not block, because it will delay garbage collection.</span><span class="sxs-lookup"><span data-stu-id="91cbb-118">The implementation of `FunctionTailcall3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="91cbb-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span><span class="sxs-lookup"><span data-stu-id="91cbb-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="91cbb-120">If a garbage collection is attempted, the runtime will block until `FunctionTailcall3WithInfo` returns.</span><span class="sxs-lookup"><span data-stu-id="91cbb-120">If a garbage collection is attempted, the runtime will block until `FunctionTailcall3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="91cbb-121">Also, the FunctionTailcall3WithInfo function must not call into managed code or cause a managed memory allocation in any way.</span><span class="sxs-lookup"><span data-stu-id="91cbb-121">Also, the FunctionTailcall3WithInfo function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91cbb-122">spécifications</span><span class="sxs-lookup"><span data-stu-id="91cbb-122">Requirements</span></span>  
 <span data-ttu-id="91cbb-123">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91cbb-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91cbb-124">**Header:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="91cbb-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="91cbb-125">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91cbb-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91cbb-126">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91cbb-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91cbb-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="91cbb-127">See also</span></span>

- [<span data-ttu-id="91cbb-128">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="91cbb-128">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="91cbb-129">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="91cbb-129">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="91cbb-130">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="91cbb-130">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="91cbb-131">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="91cbb-131">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="91cbb-132">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="91cbb-132">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="91cbb-133">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="91cbb-133">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="91cbb-134">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="91cbb-134">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="91cbb-135">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="91cbb-135">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="91cbb-136">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="91cbb-136">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="91cbb-137">Fonctions statiques globales de profilage</span><span class="sxs-lookup"><span data-stu-id="91cbb-137">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
