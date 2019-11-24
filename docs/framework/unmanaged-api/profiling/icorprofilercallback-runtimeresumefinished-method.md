---
title: ICorProfilerCallback::RuntimeResumeFinished, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeResumeFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeResumeFinished
helpviewer_keywords:
- RuntimeResumeFinished method [.NET Framework profiling]
- ICorProfilerCallback::RuntimeResumeFinished method [.NET Framework profiling]
ms.assetid: 76de0494-dc49-426b-887d-bee98806a982
topic_type:
- apiref
ms.openlocfilehash: 81c26214762fba1cac43e42adc1ee9909759972f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430311"
---
# <a name="icorprofilercallbackruntimeresumefinished-method"></a><span data-ttu-id="ba2d7-102">ICorProfilerCallback::RuntimeResumeFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="ba2d7-102">ICorProfilerCallback::RuntimeResumeFinished Method</span></span>
<span data-ttu-id="ba2d7-103">Notifies the profiler that the runtime has resumed all runtime threads and has returned to normal operation.</span><span class="sxs-lookup"><span data-stu-id="ba2d7-103">Notifies the profiler that the runtime has resumed all runtime threads and has returned to normal operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba2d7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ba2d7-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeResumeFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="ba2d7-105">Notes</span><span class="sxs-lookup"><span data-stu-id="ba2d7-105">Remarks</span></span>  
 <span data-ttu-id="ba2d7-106">The `RuntimeResumeFinished` callback is not guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span><span class="sxs-lookup"><span data-stu-id="ba2d7-106">The `RuntimeResumeFinished` callback is not guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span> <span data-ttu-id="ba2d7-107">However, it is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callback.</span><span class="sxs-lookup"><span data-stu-id="ba2d7-107">However, it is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba2d7-108">spécifications</span><span class="sxs-lookup"><span data-stu-id="ba2d7-108">Requirements</span></span>  
 <span data-ttu-id="ba2d7-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba2d7-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba2d7-110">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ba2d7-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ba2d7-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ba2d7-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba2d7-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba2d7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba2d7-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ba2d7-113">See also</span></span>

- [<span data-ttu-id="ba2d7-114">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="ba2d7-114">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
