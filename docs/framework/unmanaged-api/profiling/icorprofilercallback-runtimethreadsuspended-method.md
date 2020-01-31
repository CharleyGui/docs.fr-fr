---
title: ICorProfilerCallback::RuntimeThreadSuspended, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeThreadSuspended
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeThreadSuspended
helpviewer_keywords:
- RuntimeThreadSuspended method [.NET Framework profiling]
- ICorProfilerCallback::RuntimeThreadSuspended method [.NET Framework profiling]
ms.assetid: de830a8b-6ee1-4900-ace3-4237108f6b12
topic_type:
- apiref
ms.openlocfilehash: c8645bf828d0ad99bd25c1909cbee3314a11abf9
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865868"
---
# <a name="icorprofilercallbackruntimethreadsuspended-method"></a><span data-ttu-id="d706a-102">ICorProfilerCallback::RuntimeThreadSuspended, méthode</span><span class="sxs-lookup"><span data-stu-id="d706a-102">ICorProfilerCallback::RuntimeThreadSuspended Method</span></span>
<span data-ttu-id="d706a-103">Indique au profileur que le thread spécifié a été suspendu ou est sur le lieu d’être suspendu.</span><span class="sxs-lookup"><span data-stu-id="d706a-103">Notifies the profiler that the specified thread has been suspended or is about to be suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d706a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d706a-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeThreadSuspended(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d706a-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="d706a-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="d706a-106">dans ID du thread qui a été suspendu.</span><span class="sxs-lookup"><span data-stu-id="d706a-106">[in] The ID of the thread that has been suspended.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d706a-107">Notes</span><span class="sxs-lookup"><span data-stu-id="d706a-107">Remarks</span></span>  
 <span data-ttu-id="d706a-108">La notification `RuntimeThreadSuspended` peut se produire à tout moment entre [ICorProfilerCallback :: RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) et les rappels [ICorProfilerCallback :: RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) associés.</span><span class="sxs-lookup"><span data-stu-id="d706a-108">The `RuntimeThreadSuspended` notification can occur any time between the [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) and the associated [ICorProfilerCallback::RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span> <span data-ttu-id="d706a-109">Les notifications qui se produisent entre [ICorProfilerCallback :: RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) et `RuntimeResumeStarted` sont pour les threads qui étaient exécutés dans du code non managé et qui ont été suspendus lors de l’entrée dans le Runtime.</span><span class="sxs-lookup"><span data-stu-id="d706a-109">Notifications that occur between [ICorProfilerCallback::RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) and `RuntimeResumeStarted` are for threads that had been running in unmanaged code and were suspended upon entry to the runtime.</span></span>  
  
 <span data-ttu-id="d706a-110">En règle générale, ce rappel se produit juste après l’interruption d’un thread.</span><span class="sxs-lookup"><span data-stu-id="d706a-110">Generally, this callback occurs just after a thread is suspended.</span></span> <span data-ttu-id="d706a-111">Toutefois, si le thread en cours d’exécution (le thread qui a appelé ce rappel) est celui qui est suspendu, ce rappel se produit juste avant la suspension du thread.</span><span class="sxs-lookup"><span data-stu-id="d706a-111">However, if the currently executing thread (the thread that called this callback) is the one that is being suspended, this callback will occur just before the thread is suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d706a-112">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="d706a-112">Requirements</span></span>  
 <span data-ttu-id="d706a-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d706a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d706a-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d706a-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d706a-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d706a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d706a-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d706a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d706a-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d706a-117">See also</span></span>

- [<span data-ttu-id="d706a-118">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="d706a-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="d706a-119">RuntimeThreadResumed, méthode</span><span class="sxs-lookup"><span data-stu-id="d706a-119">RuntimeThreadResumed Method</span></span>](icorprofilercallback-runtimethreadresumed-method.md)
