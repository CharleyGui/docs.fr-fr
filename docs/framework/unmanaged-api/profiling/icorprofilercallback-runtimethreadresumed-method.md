---
title: ICorProfilerCallback::RuntimeThreadResumed, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeThreadResumed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeThreadResumed
helpviewer_keywords:
- ICorProfilerCallback::RuntimeThreadResumed method [.NET Framework profiling]
- RuntimeThreadResumed method [.NET Framework profiling]
ms.assetid: da984f89-4f53-4ab0-ae6f-3e2ee6085994
topic_type:
- apiref
ms.openlocfilehash: 5a9ca2f4587c4881820e1aa3d4134f90ce47d557
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865894"
---
# <a name="icorprofilercallbackruntimethreadresumed-method"></a><span data-ttu-id="b2d2a-102">ICorProfilerCallback::RuntimeThreadResumed, méthode</span><span class="sxs-lookup"><span data-stu-id="b2d2a-102">ICorProfilerCallback::RuntimeThreadResumed Method</span></span>
<span data-ttu-id="b2d2a-103">Notifie le profileur que le thread spécifié a repris après avoir été suspendu.</span><span class="sxs-lookup"><span data-stu-id="b2d2a-103">Notifies the profiler that the specified thread has resumed after being suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2d2a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b2d2a-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeThreadResumed(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2d2a-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="b2d2a-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="b2d2a-106">dans ID du thread qui a été repris.</span><span class="sxs-lookup"><span data-stu-id="b2d2a-106">[in] The ID of the thread that has been resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2d2a-107">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="b2d2a-107">Requirements</span></span>  
 <span data-ttu-id="b2d2a-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2d2a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2d2a-109">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b2d2a-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b2d2a-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b2d2a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2d2a-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2d2a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2d2a-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b2d2a-112">See also</span></span>

- [<span data-ttu-id="b2d2a-113">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="b2d2a-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="b2d2a-114">RuntimeThreadSuspended, méthode</span><span class="sxs-lookup"><span data-stu-id="b2d2a-114">RuntimeThreadSuspended Method</span></span>](icorprofilercallback-runtimethreadsuspended-method.md)
