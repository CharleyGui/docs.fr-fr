---
title: ICorProfilerInfo3::GetFunctionLeave3Info, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionLeave3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionLeave3Info
helpviewer_keywords:
- GetFunctionLeave3Info method [.NET Framework profiling]
- ICorProfilerInfo3::GetFunctionLeave3Info method [.NET Framework profiling]
ms.assetid: df7083d2-fd43-44c7-9ce5-912c25cef0ff
topic_type:
- apiref
ms.openlocfilehash: bacb50520df9f1553226ec6bf1e878238b64bb17
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449711"
---
# <a name="icorprofilerinfo3getfunctionleave3info-method"></a><span data-ttu-id="9f1bd-102">ICorProfilerInfo3::GetFunctionLeave3Info, méthode</span><span class="sxs-lookup"><span data-stu-id="9f1bd-102">ICorProfilerInfo3::GetFunctionLeave3Info Method</span></span>
<span data-ttu-id="9f1bd-103">Provides the stack frame and return value of the function that is being reported to the profiler by the [FunctionLeave3WithInfo function](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) function.</span><span class="sxs-lookup"><span data-stu-id="9f1bd-103">Provides the stack frame and return value of the function that is being reported to the profiler by the [FunctionLeave3WithInfo function](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) function.</span></span> <span data-ttu-id="9f1bd-104">Cette méthode peut être appelée uniquement pendant le rappel de `FunctionLeave3WithInfo`.</span><span class="sxs-lookup"><span data-stu-id="9f1bd-104">This method can be called only during the `FunctionLeave3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f1bd-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f1bd-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionLeave3Info(  
            [in]  FunctionID functionId,  
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [out] COR_PRF_FUNCTION_ARGUMENT_RANGE *pRetvalRange);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f1bd-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9f1bd-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="9f1bd-107">[in] The `FunctionID` of the function that is returning.</span><span class="sxs-lookup"><span data-stu-id="9f1bd-107">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="9f1bd-108">[in] Handle opaque qui représente des informations sur un frame de pile donné.</span><span class="sxs-lookup"><span data-stu-id="9f1bd-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="9f1bd-109">The profiler should provide the same `eltInfo` that was given to the profiler by the [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) function.</span><span class="sxs-lookup"><span data-stu-id="9f1bd-109">The profiler should provide the same `eltInfo` that was given to the profiler by the [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="9f1bd-110">[out] Handle opaque qui représente des informations génériques sur un frame de pile donné.</span><span class="sxs-lookup"><span data-stu-id="9f1bd-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="9f1bd-111">Ce handle est uniquement valide pendant le rappel `FunctionLeave3WithInfo` au cours duquel le profileur a appelé la méthode `GetFunctionLeave3Info`.</span><span class="sxs-lookup"><span data-stu-id="9f1bd-111">This handle is valid only during the `FunctionLeave3WithInfo` callback in which the profiler called the `GetFunctionLeave3Info` method.</span></span>  
  
 `pRetvalRange`  
 <span data-ttu-id="9f1bd-112">[out] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structure that contains the value that is returned from the function.</span><span class="sxs-lookup"><span data-stu-id="9f1bd-112">[out] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structure that contains the value that is returned from the function.</span></span> <span data-ttu-id="9f1bd-113">To access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span><span class="sxs-lookup"><span data-stu-id="9f1bd-113">To access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span></span> <span data-ttu-id="9f1bd-114">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags.</span><span class="sxs-lookup"><span data-stu-id="9f1bd-114">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f1bd-115">Notes</span><span class="sxs-lookup"><span data-stu-id="9f1bd-115">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f1bd-116">spécifications</span><span class="sxs-lookup"><span data-stu-id="9f1bd-116">Requirements</span></span>  
 <span data-ttu-id="9f1bd-117">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f1bd-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f1bd-118">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9f1bd-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9f1bd-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9f1bd-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9f1bd-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f1bd-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f1bd-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9f1bd-121">See also</span></span>

- [<span data-ttu-id="9f1bd-122">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="9f1bd-122">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="9f1bd-123">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="9f1bd-123">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="9f1bd-124">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="9f1bd-124">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="9f1bd-125">ICorProfilerInfo3, interface</span><span class="sxs-lookup"><span data-stu-id="9f1bd-125">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="9f1bd-126">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="9f1bd-126">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="9f1bd-127">Profilage</span><span class="sxs-lookup"><span data-stu-id="9f1bd-127">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
