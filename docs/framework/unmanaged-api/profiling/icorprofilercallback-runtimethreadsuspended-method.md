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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b6d03e760d2b08cd9ee8cdfd85e2e28223aeacd4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747235"
---
# <a name="icorprofilercallbackruntimethreadsuspended-method"></a><span data-ttu-id="56d56-102">ICorProfilerCallback::RuntimeThreadSuspended, méthode</span><span class="sxs-lookup"><span data-stu-id="56d56-102">ICorProfilerCallback::RuntimeThreadSuspended Method</span></span>
<span data-ttu-id="56d56-103">Notifie le profileur que le thread spécifié a été suspendu ou qu’il doit être interrompu.</span><span class="sxs-lookup"><span data-stu-id="56d56-103">Notifies the profiler that the specified thread has been suspended or is about to be suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56d56-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56d56-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeThreadSuspended(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56d56-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="56d56-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="56d56-106">[in] L’ID du thread qui a été suspendu.</span><span class="sxs-lookup"><span data-stu-id="56d56-106">[in] The ID of the thread that has been suspended.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56d56-107">Notes</span><span class="sxs-lookup"><span data-stu-id="56d56-107">Remarks</span></span>  
 <span data-ttu-id="56d56-108">Le `RuntimeThreadSuspended` notification peut se produire à tout moment entre le [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) et associé [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) rappels.</span><span class="sxs-lookup"><span data-stu-id="56d56-108">The `RuntimeThreadSuspended` notification can occur any time between the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) and the associated [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span> <span data-ttu-id="56d56-109">Les notifications qui se produisent entre [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) et `RuntimeResumeStarted` concernent les threads qui étaient exécutés dans du code non managé et ont été suspendus lors de l’entrée à l’exécution.</span><span class="sxs-lookup"><span data-stu-id="56d56-109">Notifications that occur between [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) and `RuntimeResumeStarted` are for threads that had been running in unmanaged code and were suspended upon entry to the runtime.</span></span>  
  
 <span data-ttu-id="56d56-110">En règle générale, ce rappel se produit juste après qu’un thread est suspendu.</span><span class="sxs-lookup"><span data-stu-id="56d56-110">Generally, this callback occurs just after a thread is suspended.</span></span> <span data-ttu-id="56d56-111">Toutefois, si le thread en cours d’exécution (le thread qui a appelé ce rappel) est celui qui est suspendu, ce rappel se produit juste avant que le thread est suspendu.</span><span class="sxs-lookup"><span data-stu-id="56d56-111">However, if the currently executing thread (the thread that called this callback) is the one that is being suspended, this callback will occur just before the thread is suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56d56-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="56d56-112">Requirements</span></span>  
 <span data-ttu-id="56d56-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56d56-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56d56-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="56d56-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="56d56-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="56d56-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56d56-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56d56-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56d56-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="56d56-117">See also</span></span>

- [<span data-ttu-id="56d56-118">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="56d56-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="56d56-119">RuntimeThreadResumed, méthode</span><span class="sxs-lookup"><span data-stu-id="56d56-119">RuntimeThreadResumed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)
