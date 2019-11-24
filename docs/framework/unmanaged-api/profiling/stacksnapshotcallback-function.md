---
title: StackSnapshotCallback (fonction)
ms.date: 03/30/2017
api_name:
- StackSnapshotCallback
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- StackSnapshotCallback
helpviewer_keywords:
- StackSnapshotCallback function [.NET Framework profiling]
ms.assetid: d0f235b2-91fe-4f82-b7d5-e5c64186eea8
topic_type:
- apiref
ms.openlocfilehash: c0cec9eb7bb8bbc94b255152a9b4d79108bdd1b1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427079"
---
# <a name="stacksnapshotcallback-function"></a><span data-ttu-id="d0511-102">StackSnapshotCallback (fonction)</span><span class="sxs-lookup"><span data-stu-id="d0511-102">StackSnapshotCallback Function</span></span>
<span data-ttu-id="d0511-103">Provides the profiler with information about each managed frame and each run of unmanaged frames on the stack during a stack walk, which is initiated by the [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method.</span><span class="sxs-lookup"><span data-stu-id="d0511-103">Provides the profiler with information about each managed frame and each run of unmanaged frames on the stack during a stack walk, which is initiated by the [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0511-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d0511-104">Syntax</span></span>  
  
```cpp  
HRESULT __stdcall StackSnapshotCallback (  
    [in] FunctionID funcId,  
    [in] UINT_PTR ip,  
    [in] COR_PRF_FRAME_INFO frameInfo,  
    [in] ULONG32 contextSize,  
    [in] BYTE context[],  
    [in] void *clientData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0511-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d0511-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="d0511-106">[in] If this value is zero, this callback is for a run of unmanaged frames; otherwise, it is the identifier of a managed function and this callback is for a managed frame.</span><span class="sxs-lookup"><span data-stu-id="d0511-106">[in] If this value is zero, this callback is for a run of unmanaged frames; otherwise, it is the identifier of a managed function and this callback is for a managed frame.</span></span>  
  
 `ip`  
 <span data-ttu-id="d0511-107">[in] The value of the native code instruction pointer in the frame.</span><span class="sxs-lookup"><span data-stu-id="d0511-107">[in] The value of the native code instruction pointer in the frame.</span></span>  
  
 `frameInfo`  
 <span data-ttu-id="d0511-108">[in] A `COR_PRF_FRAME_INFO` value that references information about the stack frame.</span><span class="sxs-lookup"><span data-stu-id="d0511-108">[in] A `COR_PRF_FRAME_INFO` value that references information about the stack frame.</span></span> <span data-ttu-id="d0511-109">This value is valid for use only during this callback.</span><span class="sxs-lookup"><span data-stu-id="d0511-109">This value is valid for use only during this callback.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="d0511-110">[in] The size of the `CONTEXT` structure, which is referenced by the `context` parameter.</span><span class="sxs-lookup"><span data-stu-id="d0511-110">[in] The size of the `CONTEXT` structure, which is referenced by the `context` parameter.</span></span>  
  
 `context`  
 <span data-ttu-id="d0511-111">[in] A pointer to a Win32 `CONTEXT` structure that represents the state of the CPU for this frame.</span><span class="sxs-lookup"><span data-stu-id="d0511-111">[in] A pointer to a Win32 `CONTEXT` structure that represents the state of the CPU for this frame.</span></span>  
  
 <span data-ttu-id="d0511-112">The `context` parameter is valid only if the COR_PRF_SNAPSHOT_CONTEXT flag was passed in `ICorProfilerInfo2::DoStackSnapshot`.</span><span class="sxs-lookup"><span data-stu-id="d0511-112">The `context` parameter is valid only if the COR_PRF_SNAPSHOT_CONTEXT flag was passed in `ICorProfilerInfo2::DoStackSnapshot`.</span></span>  
  
 `clientData`  
 <span data-ttu-id="d0511-113">[in] A pointer to the client data, which is passed straight through from `ICorProfilerInfo2::DoStackSnapshot`.</span><span class="sxs-lookup"><span data-stu-id="d0511-113">[in] A pointer to the client data, which is passed straight through from `ICorProfilerInfo2::DoStackSnapshot`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0511-114">Notes</span><span class="sxs-lookup"><span data-stu-id="d0511-114">Remarks</span></span>  
 <span data-ttu-id="d0511-115">The `StackSnapshotCallback` function is implemented by the profiler writer.</span><span class="sxs-lookup"><span data-stu-id="d0511-115">The `StackSnapshotCallback` function is implemented by the profiler writer.</span></span> <span data-ttu-id="d0511-116">You must limit the complexity of work done in `StackSnapshotCallback`.</span><span class="sxs-lookup"><span data-stu-id="d0511-116">You must limit the complexity of work done in `StackSnapshotCallback`.</span></span> <span data-ttu-id="d0511-117">For example, when using `ICorProfilerInfo2::DoStackSnapshot` in an asynchronous manner, the target thread may be holding locks.</span><span class="sxs-lookup"><span data-stu-id="d0511-117">For example, when using `ICorProfilerInfo2::DoStackSnapshot` in an asynchronous manner, the target thread may be holding locks.</span></span> <span data-ttu-id="d0511-118">If code within `StackSnapshotCallback` requires the same locks, a deadlock could ensue.</span><span class="sxs-lookup"><span data-stu-id="d0511-118">If code within `StackSnapshotCallback` requires the same locks, a deadlock could ensue.</span></span>  
  
 <span data-ttu-id="d0511-119">The `ICorProfilerInfo2::DoStackSnapshot` method calls the `StackSnapshotCallback` function once per managed frame or once per run of unmanaged frames.</span><span class="sxs-lookup"><span data-stu-id="d0511-119">The `ICorProfilerInfo2::DoStackSnapshot` method calls the `StackSnapshotCallback` function once per managed frame or once per run of unmanaged frames.</span></span> <span data-ttu-id="d0511-120">If `StackSnapshotCallback` is called for a run of unmanaged frames, the profiler may use the register context (referenced by the `context` parameter) to perform its own unmanaged stack walk.</span><span class="sxs-lookup"><span data-stu-id="d0511-120">If `StackSnapshotCallback` is called for a run of unmanaged frames, the profiler may use the register context (referenced by the `context` parameter) to perform its own unmanaged stack walk.</span></span> <span data-ttu-id="d0511-121">In this case, the Win32 `CONTEXT` structure represents the CPU state for the most recently pushed frame within the run of unmanaged frames.</span><span class="sxs-lookup"><span data-stu-id="d0511-121">In this case, the Win32 `CONTEXT` structure represents the CPU state for the most recently pushed frame within the run of unmanaged frames.</span></span> <span data-ttu-id="d0511-122">Although the Win32 `CONTEXT` structure includes values for all registers, you should rely only on the values of the stack pointer register, frame pointer register, instruction pointer register, and the nonvolatile (that is, preserved) integer registers.</span><span class="sxs-lookup"><span data-stu-id="d0511-122">Although the Win32 `CONTEXT` structure includes values for all registers, you should rely only on the values of the stack pointer register, frame pointer register, instruction pointer register, and the nonvolatile (that is, preserved) integer registers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0511-123">spécifications</span><span class="sxs-lookup"><span data-stu-id="d0511-123">Requirements</span></span>  
 <span data-ttu-id="d0511-124">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0511-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0511-125">**Header:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="d0511-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="d0511-126">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d0511-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0511-127">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0511-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0511-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d0511-128">See also</span></span>

- [<span data-ttu-id="d0511-129">DoStackSnapshot, méthode</span><span class="sxs-lookup"><span data-stu-id="d0511-129">DoStackSnapshot Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)
- [<span data-ttu-id="d0511-130">Fonctions statiques globales de profilage</span><span class="sxs-lookup"><span data-stu-id="d0511-130">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
