---
title: ICorProfilerCallback::JITCompilationStarted, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCompilationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCompilationStarted
helpviewer_keywords:
- JITCompilationStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationStarted method [.NET Framework profiling]
ms.assetid: 31782b36-d311-4518-8f45-25f65385af5b
topic_type:
- apiref
ms.openlocfilehash: 96ab77a36c0a0bddda0fca342433666dd19082d3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426194"
---
# <a name="icorprofilercallbackjitcompilationstarted-method"></a><span data-ttu-id="d4f20-102">ICorProfilerCallback::JITCompilationStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="d4f20-102">ICorProfilerCallback::JITCompilationStarted Method</span></span>
<span data-ttu-id="d4f20-103">Notifies the profiler that the just-in-time (JIT) compiler has started to compile a function.</span><span class="sxs-lookup"><span data-stu-id="d4f20-103">Notifies the profiler that the just-in-time (JIT) compiler has started to compile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4f20-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4f20-104">Syntax</span></span>  
  
```cpp  
HRESULT JITCompilationStarted(  
    [in] FunctionID functionId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4f20-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d4f20-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="d4f20-106">[in] The ID of the function for which the compilation is starting.</span><span class="sxs-lookup"><span data-stu-id="d4f20-106">[in] The ID of the function for which the compilation is starting.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="d4f20-107">[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span><span class="sxs-lookup"><span data-stu-id="d4f20-107">[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="d4f20-108">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span><span class="sxs-lookup"><span data-stu-id="d4f20-108">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="d4f20-109">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span><span class="sxs-lookup"><span data-stu-id="d4f20-109">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4f20-110">Notes</span><span class="sxs-lookup"><span data-stu-id="d4f20-110">Remarks</span></span>  
 <span data-ttu-id="d4f20-111">It is possible to receive more than one pair of `JITCompilationStarted` and [ICorProfilerCallback::JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md) calls for each function because of the way the runtime handles class constructors.</span><span class="sxs-lookup"><span data-stu-id="d4f20-111">It is possible to receive more than one pair of `JITCompilationStarted` and [ICorProfilerCallback::JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md) calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="d4f20-112">For example, the runtime starts to JIT-compile method A, but the class constructor for class B needs to be run.</span><span class="sxs-lookup"><span data-stu-id="d4f20-112">For example, the runtime starts to JIT-compile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="d4f20-113">Therefore, the runtime JIT-compiles the constructor for class B and runs it.</span><span class="sxs-lookup"><span data-stu-id="d4f20-113">Therefore, the runtime JIT-compiles the constructor for class B and runs it.</span></span> <span data-ttu-id="d4f20-114">While the constructor is running, it makes a call to method A, which causes method A to be JIT-compiled again.</span><span class="sxs-lookup"><span data-stu-id="d4f20-114">While the constructor is running, it makes a call to method A, which causes method A to be JIT-compiled again.</span></span> <span data-ttu-id="d4f20-115">In this scenario, the first JIT compilation of method A is halted.</span><span class="sxs-lookup"><span data-stu-id="d4f20-115">In this scenario, the first JIT compilation of method A is halted.</span></span> <span data-ttu-id="d4f20-116">However, both attempts to JIT-compile method A are reported with JIT-compilation events.</span><span class="sxs-lookup"><span data-stu-id="d4f20-116">However, both attempts to JIT-compile method A are reported with JIT-compilation events.</span></span> <span data-ttu-id="d4f20-117">If the profiler is going to replace Microsoft intermediate language (MSIL) code for method A by calling the [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) method, it must do so for both `JITCompilationStarted` events, but it may use the same MSIL block for both.</span><span class="sxs-lookup"><span data-stu-id="d4f20-117">If the profiler is going to replace Microsoft intermediate language (MSIL) code for method A by calling the [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) method, it must do so for both `JITCompilationStarted` events, but it may use the same MSIL block for both.</span></span>  
  
 <span data-ttu-id="d4f20-118">Profilers must support the sequence of JIT callbacks in cases where two threads are simultaneously making callbacks.</span><span class="sxs-lookup"><span data-stu-id="d4f20-118">Profilers must support the sequence of JIT callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="d4f20-119">For example, thread A calls `JITCompilationStarted`.</span><span class="sxs-lookup"><span data-stu-id="d4f20-119">For example, thread A calls `JITCompilationStarted`.</span></span> <span data-ttu-id="d4f20-120">However, before thread A calls `JITCompilationFinished`, thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from thread A's `JITCompilationStarted` callback.</span><span class="sxs-lookup"><span data-stu-id="d4f20-120">However, before thread A calls `JITCompilationFinished`, thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from thread A's `JITCompilationStarted` callback.</span></span> <span data-ttu-id="d4f20-121">It might appear that the function ID should not yet be valid because a call to `JITCompilationFinished` had not yet been received by the profiler.</span><span class="sxs-lookup"><span data-stu-id="d4f20-121">It might appear that the function ID should not yet be valid because a call to `JITCompilationFinished` had not yet been received by the profiler.</span></span> <span data-ttu-id="d4f20-122">However, in a case like this one, the function ID is valid.</span><span class="sxs-lookup"><span data-stu-id="d4f20-122">However, in a case like this one, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4f20-123">spécifications</span><span class="sxs-lookup"><span data-stu-id="d4f20-123">Requirements</span></span>  
 <span data-ttu-id="d4f20-124">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4f20-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4f20-125">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d4f20-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d4f20-126">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d4f20-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4f20-127">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4f20-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4f20-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d4f20-128">See also</span></span>

- [<span data-ttu-id="d4f20-129">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="d4f20-129">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="d4f20-130">JITCompilationFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="d4f20-130">JITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)
