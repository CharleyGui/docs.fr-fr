---
title: ICorProfilerCallback::ThreadDestroyed, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ThreadDestroyed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ThreadDestroyed
helpviewer_keywords:
- ThreadDestroyed method [.NET Framework profiling]
- ICorProfilerCallback::ThreadDestroyed method [.NET Framework profiling]
ms.assetid: 4c2b66fd-0595-40a3-8931-f9c4fff97ac8
topic_type:
- apiref
ms.openlocfilehash: 07041d06668d474a3d30968fb623854a24ebf0eb
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865816"
---
# <a name="icorprofilercallbackthreaddestroyed-method"></a><span data-ttu-id="59d85-102">ICorProfilerCallback::ThreadDestroyed, méthode</span><span class="sxs-lookup"><span data-stu-id="59d85-102">ICorProfilerCallback::ThreadDestroyed Method</span></span>
<span data-ttu-id="59d85-103">Notifie le profileur qu’un thread a été détruit.</span><span class="sxs-lookup"><span data-stu-id="59d85-103">Notifies the profiler that a thread has been destroyed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59d85-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59d85-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadDestroyed(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="59d85-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="59d85-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="59d85-106">dans ID du thread qui a été détruit.</span><span class="sxs-lookup"><span data-stu-id="59d85-106">[in] The ID of the thread that has been destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="59d85-107">Notes</span><span class="sxs-lookup"><span data-stu-id="59d85-107">Remarks</span></span>  
 <span data-ttu-id="59d85-108">La valeur `threadId` n’est plus valide au moment de cet appel.</span><span class="sxs-lookup"><span data-stu-id="59d85-108">The `threadId` value is no longer valid at the time of this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59d85-109">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="59d85-109">Requirements</span></span>  
 <span data-ttu-id="59d85-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59d85-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59d85-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="59d85-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="59d85-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="59d85-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59d85-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59d85-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59d85-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59d85-114">See also</span></span>

- [<span data-ttu-id="59d85-115">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="59d85-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="59d85-116">ThreadCreated, méthode</span><span class="sxs-lookup"><span data-stu-id="59d85-116">ThreadCreated Method</span></span>](icorprofilercallback-threadcreated-method.md)
