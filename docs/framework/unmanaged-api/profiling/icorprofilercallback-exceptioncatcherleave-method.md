---
title: ICorProfilerCallback::ExceptionCatcherLeave, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCatcherLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCatcherLeave
helpviewer_keywords:
- ExceptionCatcherLeave method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionCatcherLeave method [.NET Framework profiling]
ms.assetid: 1f3dbdf5-db0c-4b07-bbb7-375de2a63673
topic_type:
- apiref
ms.openlocfilehash: 7d61a6db8f42398a0d6e0d818605592f4fe71cf7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444998"
---
# <a name="icorprofilercallbackexceptioncatcherleave-method"></a><span data-ttu-id="34957-102">ICorProfilerCallback::ExceptionCatcherLeave, méthode</span><span class="sxs-lookup"><span data-stu-id="34957-102">ICorProfilerCallback::ExceptionCatcherLeave Method</span></span>
<span data-ttu-id="34957-103">Notifies the profiler that control is being passed out of the appropriate `catch` block.</span><span class="sxs-lookup"><span data-stu-id="34957-103">Notifies the profiler that control is being passed out of the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34957-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="34957-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCatcherLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="34957-105">Notes</span><span class="sxs-lookup"><span data-stu-id="34957-105">Remarks</span></span>  
 <span data-ttu-id="34957-106">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span><span class="sxs-lookup"><span data-stu-id="34957-106">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="34957-107">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span><span class="sxs-lookup"><span data-stu-id="34957-107">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="34957-108">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span><span class="sxs-lookup"><span data-stu-id="34957-108">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34957-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="34957-109">Requirements</span></span>  
 <span data-ttu-id="34957-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34957-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34957-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="34957-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="34957-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="34957-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34957-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34957-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34957-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="34957-114">See also</span></span>

- [<span data-ttu-id="34957-115">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="34957-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="34957-116">ExceptionCatcherEnter, méthode</span><span class="sxs-lookup"><span data-stu-id="34957-116">ExceptionCatcherEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)
