---
title: FunctionLeave3, fonction
ms.date: 03/30/2017
api_name:
- FunctionLeave3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave3
helpviewer_keywords:
- FunctionLeave3 function [.NET Framework profiling]
ms.assetid: 5d798088-7992-48a0-ae55-d2a7ee31913f
topic_type:
- apiref
ms.openlocfilehash: 104a6c3c42c310513040cb45db7f51ffe729c19d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427437"
---
# <a name="functionleave3-function"></a><span data-ttu-id="d427c-102">FunctionLeave3, fonction</span><span class="sxs-lookup"><span data-stu-id="d427c-102">FunctionLeave3 Function</span></span>
<span data-ttu-id="d427c-103">Notifies the profiler that control is being returned from a function.</span><span class="sxs-lookup"><span data-stu-id="d427c-103">Notifies the profiler that control is being returned from a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d427c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d427c-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d427c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d427c-105">Parameters</span></span>  
 `functionOrRemappedID`  
 <span data-ttu-id="d427c-106">[in] The identifier of the function from which control is returned.</span><span class="sxs-lookup"><span data-stu-id="d427c-106">[in] The identifier of the function from which control is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d427c-107">Notes</span><span class="sxs-lookup"><span data-stu-id="d427c-107">Remarks</span></span>  
 <span data-ttu-id="d427c-108">The `FunctionLeave3` callback function notifies the profiler as functions are being called, but does not support return value inspection.</span><span class="sxs-lookup"><span data-stu-id="d427c-108">The `FunctionLeave3` callback function notifies the profiler as functions are being called, but does not support return value inspection.</span></span> <span data-ttu-id="d427c-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span><span class="sxs-lookup"><span data-stu-id="d427c-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="d427c-110">The `FunctionLeave3` function is a callback; you must implement it.</span><span class="sxs-lookup"><span data-stu-id="d427c-110">The `FunctionLeave3` function is a callback; you must implement it.</span></span> <span data-ttu-id="d427c-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span><span class="sxs-lookup"><span data-stu-id="d427c-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="d427c-112">The execution engine does not save any registers before calling this function.</span><span class="sxs-lookup"><span data-stu-id="d427c-112">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="d427c-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span><span class="sxs-lookup"><span data-stu-id="d427c-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="d427c-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span><span class="sxs-lookup"><span data-stu-id="d427c-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="d427c-115">The implementation of `FunctionLeave3` should not block, because it will delay garbage collection.</span><span class="sxs-lookup"><span data-stu-id="d427c-115">The implementation of `FunctionLeave3` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="d427c-116">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span><span class="sxs-lookup"><span data-stu-id="d427c-116">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="d427c-117">If a garbage collection is attempted, the runtime will block until `FunctionLeave3` returns.</span><span class="sxs-lookup"><span data-stu-id="d427c-117">If a garbage collection is attempted, the runtime will block until `FunctionLeave3` returns.</span></span>  
  
 <span data-ttu-id="d427c-118">The `FunctionLeave3` function must not call into managed code or cause a managed memory allocation in any way.</span><span class="sxs-lookup"><span data-stu-id="d427c-118">The `FunctionLeave3` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d427c-119">spécifications</span><span class="sxs-lookup"><span data-stu-id="d427c-119">Requirements</span></span>  
 <span data-ttu-id="d427c-120">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d427c-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d427c-121">**Header:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="d427c-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="d427c-122">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d427c-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d427c-123">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d427c-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d427c-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d427c-124">See also</span></span>

- [<span data-ttu-id="d427c-125">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="d427c-125">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="d427c-126">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="d427c-126">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="d427c-127">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="d427c-127">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="d427c-128">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="d427c-128">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="d427c-129">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="d427c-129">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="d427c-130">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="d427c-130">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="d427c-131">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="d427c-131">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="d427c-132">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="d427c-132">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="d427c-133">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="d427c-133">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="d427c-134">Fonctions statiques globales de profilage</span><span class="sxs-lookup"><span data-stu-id="d427c-134">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
