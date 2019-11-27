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
ms.openlocfilehash: 57ad0bd3ed76376421d22a84c0863d36ec2707c9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430271"
---
# <a name="icorprofilercallbackruntimethreadresumed-method"></a><span data-ttu-id="cbfd3-102">ICorProfilerCallback::RuntimeThreadResumed, méthode</span><span class="sxs-lookup"><span data-stu-id="cbfd3-102">ICorProfilerCallback::RuntimeThreadResumed Method</span></span>
<span data-ttu-id="cbfd3-103">Notifie le profileur que le thread spécifié a repris après avoir été suspendu.</span><span class="sxs-lookup"><span data-stu-id="cbfd3-103">Notifies the profiler that the specified thread has resumed after being suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbfd3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cbfd3-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeThreadResumed(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cbfd3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cbfd3-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="cbfd3-106">dans ID du thread qui a été repris.</span><span class="sxs-lookup"><span data-stu-id="cbfd3-106">[in] The ID of the thread that has been resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbfd3-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="cbfd3-107">Requirements</span></span>  
 <span data-ttu-id="cbfd3-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cbfd3-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbfd3-109">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cbfd3-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cbfd3-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cbfd3-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cbfd3-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbfd3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbfd3-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cbfd3-112">See also</span></span>

- [<span data-ttu-id="cbfd3-113">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="cbfd3-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="cbfd3-114">RuntimeThreadSuspended, méthode</span><span class="sxs-lookup"><span data-stu-id="cbfd3-114">RuntimeThreadSuspended Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)
