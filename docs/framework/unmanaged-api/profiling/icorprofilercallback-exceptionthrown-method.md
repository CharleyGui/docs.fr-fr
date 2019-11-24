---
title: ICorProfilerCallback::ExceptionThrown, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionThrown
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionThrown
helpviewer_keywords:
- ExceptionThrown method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionThrown method [.NET Framework profiling]
ms.assetid: f1a23f3b-ac21-4905-8abf-8ea59f15af53
topic_type:
- apiref
ms.openlocfilehash: 4ecbe0ef3c3021c5633b9380da2eb31cf22aa4b1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445326"
---
# <a name="icorprofilercallbackexceptionthrown-method"></a><span data-ttu-id="eadbd-102">ICorProfilerCallback::ExceptionThrown, méthode</span><span class="sxs-lookup"><span data-stu-id="eadbd-102">ICorProfilerCallback::ExceptionThrown Method</span></span>
<span data-ttu-id="eadbd-103">Notifies the profiler that an exception has been thrown.</span><span class="sxs-lookup"><span data-stu-id="eadbd-103">Notifies the profiler that an exception has been thrown.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eadbd-104">This function is called only if the exception reaches managed code.</span><span class="sxs-lookup"><span data-stu-id="eadbd-104">This function is called only if the exception reaches managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eadbd-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eadbd-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionThrown(  
    [in] ObjectID thrownObjectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eadbd-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="eadbd-106">Parameters</span></span>  
 `thrownObjectId`  
 <span data-ttu-id="eadbd-107">[in] The ID of the object that caused the exception to be thrown.</span><span class="sxs-lookup"><span data-stu-id="eadbd-107">[in] The ID of the object that caused the exception to be thrown.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eadbd-108">Notes</span><span class="sxs-lookup"><span data-stu-id="eadbd-108">Remarks</span></span>  
 <span data-ttu-id="eadbd-109">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span><span class="sxs-lookup"><span data-stu-id="eadbd-109">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="eadbd-110">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span><span class="sxs-lookup"><span data-stu-id="eadbd-110">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="eadbd-111">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span><span class="sxs-lookup"><span data-stu-id="eadbd-111">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eadbd-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="eadbd-112">Requirements</span></span>  
 <span data-ttu-id="eadbd-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eadbd-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eadbd-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="eadbd-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eadbd-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eadbd-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eadbd-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eadbd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eadbd-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eadbd-117">See also</span></span>

- [<span data-ttu-id="eadbd-118">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="eadbd-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
