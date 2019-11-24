---
title: FunctionEnter3, fonction
ms.date: 03/30/2017
api_name:
- FunctionEnter3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter3
helpviewer_keywords:
- FunctionEnter3 function [.NET Framework profiling]
ms.assetid: ef782c53-dae7-4990-b4ad-fddb1e690d4e
topic_type:
- apiref
ms.openlocfilehash: fd224279b3df6c9e8e55cd81ebfbf2e5ea2428d5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440776"
---
# <a name="functionenter3-function"></a><span data-ttu-id="73bc2-102">FunctionEnter3, fonction</span><span class="sxs-lookup"><span data-stu-id="73bc2-102">FunctionEnter3 Function</span></span>
<span data-ttu-id="73bc2-103">Notifies the profiler that control is being passed to a function.</span><span class="sxs-lookup"><span data-stu-id="73bc2-103">Notifies the profiler that control is being passed to a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73bc2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73bc2-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73bc2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="73bc2-105">Parameters</span></span>  
 `functionOrRemappedID`  
 <span data-ttu-id="73bc2-106">[in] The identifier of the function to which control is passed.</span><span class="sxs-lookup"><span data-stu-id="73bc2-106">[in] The identifier of the function to which control is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73bc2-107">Notes</span><span class="sxs-lookup"><span data-stu-id="73bc2-107">Remarks</span></span>  
 <span data-ttu-id="73bc2-108">The `FunctionEnter3` callback function notifies the profiler as functions are being called, but does not support argument inspection.</span><span class="sxs-lookup"><span data-stu-id="73bc2-108">The `FunctionEnter3` callback function notifies the profiler as functions are being called, but does not support argument inspection.</span></span> <span data-ttu-id="73bc2-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span><span class="sxs-lookup"><span data-stu-id="73bc2-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="73bc2-110">The `FunctionEnter3` function is a callback; you must implement it.</span><span class="sxs-lookup"><span data-stu-id="73bc2-110">The `FunctionEnter3` function is a callback; you must implement it.</span></span> <span data-ttu-id="73bc2-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span><span class="sxs-lookup"><span data-stu-id="73bc2-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="73bc2-112">The execution engine does not save any registers before calling this function.</span><span class="sxs-lookup"><span data-stu-id="73bc2-112">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="73bc2-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span><span class="sxs-lookup"><span data-stu-id="73bc2-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="73bc2-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span><span class="sxs-lookup"><span data-stu-id="73bc2-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73bc2-115">spécifications</span><span class="sxs-lookup"><span data-stu-id="73bc2-115">Requirements</span></span>  
 <span data-ttu-id="73bc2-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73bc2-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73bc2-117">**Header:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="73bc2-117">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="73bc2-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73bc2-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73bc2-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73bc2-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73bc2-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="73bc2-120">See also</span></span>

- [<span data-ttu-id="73bc2-121">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="73bc2-121">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="73bc2-122">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="73bc2-122">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="73bc2-123">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="73bc2-123">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="73bc2-124">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="73bc2-124">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="73bc2-125">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="73bc2-125">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="73bc2-126">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="73bc2-126">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="73bc2-127">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="73bc2-127">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="73bc2-128">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="73bc2-128">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="73bc2-129">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="73bc2-129">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="73bc2-130">Fonctions statiques globales de profilage</span><span class="sxs-lookup"><span data-stu-id="73bc2-130">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
