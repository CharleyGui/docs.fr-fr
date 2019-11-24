---
title: ICorProfilerCallback::ExceptionUnwindFinallyEnter, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFinallyEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyEnter method [.NET Framework profiling]
- ExceptionUnwindFinallyEnter method [.NET Framework profiling]
ms.assetid: c7fab986-b69f-4ec8-b7b7-91dcfc239cd0
topic_type:
- apiref
ms.openlocfilehash: 1f16add7b5a9d18e0c1eb33209b609e9bf7e18b0
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445310"
---
# <a name="icorprofilercallbackexceptionunwindfinallyenter-method"></a><span data-ttu-id="08f0e-102">ICorProfilerCallback::ExceptionUnwindFinallyEnter, méthode</span><span class="sxs-lookup"><span data-stu-id="08f0e-102">ICorProfilerCallback::ExceptionUnwindFinallyEnter Method</span></span>
<span data-ttu-id="08f0e-103">Notifies the profiler that the unwind phase of exception handling is entering a `finally` clause contained in the specified function.</span><span class="sxs-lookup"><span data-stu-id="08f0e-103">Notifies the profiler that the unwind phase of exception handling is entering a `finally` clause contained in the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08f0e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08f0e-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwindFinallyEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08f0e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="08f0e-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="08f0e-106">[in] The ID of the function that contains the `finally` clause.</span><span class="sxs-lookup"><span data-stu-id="08f0e-106">[in] The ID of the function that contains the `finally` clause.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08f0e-107">Notes</span><span class="sxs-lookup"><span data-stu-id="08f0e-107">Remarks</span></span>  
 <span data-ttu-id="08f0e-108">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span><span class="sxs-lookup"><span data-stu-id="08f0e-108">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="08f0e-109">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span><span class="sxs-lookup"><span data-stu-id="08f0e-109">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="08f0e-110">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span><span class="sxs-lookup"><span data-stu-id="08f0e-110">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08f0e-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="08f0e-111">Requirements</span></span>  
 <span data-ttu-id="08f0e-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08f0e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08f0e-113">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="08f0e-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="08f0e-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="08f0e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="08f0e-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08f0e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08f0e-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="08f0e-116">See also</span></span>

- [<span data-ttu-id="08f0e-117">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="08f0e-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="08f0e-118">GetNotifiedExceptionClauseInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="08f0e-118">GetNotifiedExceptionClauseInfo Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)
- [<span data-ttu-id="08f0e-119">ExceptionUnwindFinallyLeave, méthode</span><span class="sxs-lookup"><span data-stu-id="08f0e-119">ExceptionUnwindFinallyLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)
