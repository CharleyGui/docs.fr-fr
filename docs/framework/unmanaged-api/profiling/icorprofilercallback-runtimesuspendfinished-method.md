---
title: ICorProfilerCallback::RuntimeSuspendFinished, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeSuspendFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendFinished
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendFinished method [.NET Framework profiling]
- RuntimeSuspendFinished method [.NET Framework profiling]
ms.assetid: b7723f58-c55c-4399-9972-1bbf3b866694
topic_type:
- apiref
ms.openlocfilehash: e6c21e5ec9491e2ccade48a5019b284e333b5ead
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865933"
---
# <a name="icorprofilercallbackruntimesuspendfinished-method"></a><span data-ttu-id="2375e-102">ICorProfilerCallback::RuntimeSuspendFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="2375e-102">ICorProfilerCallback::RuntimeSuspendFinished Method</span></span>
<span data-ttu-id="2375e-103">Notifie le profileur que le runtime a terminé la suspension de tous les threads d’exécution.</span><span class="sxs-lookup"><span data-stu-id="2375e-103">Notifies the profiler that the runtime has completed suspension of all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2375e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2375e-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="2375e-105">Notes</span><span class="sxs-lookup"><span data-stu-id="2375e-105">Remarks</span></span>  
 <span data-ttu-id="2375e-106">Tous les threads d’exécution qui se trouvent dans du code non managé sont autorisés à continuer à s’exécuter jusqu’à ce qu’ils essaient d’entrer à nouveau dans le Runtime.</span><span class="sxs-lookup"><span data-stu-id="2375e-106">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="2375e-107">À ce stade, ils sont également suspendus jusqu’à la reprise du Runtime.</span><span class="sxs-lookup"><span data-stu-id="2375e-107">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="2375e-108">Cela s’applique également aux nouveaux threads qui entrent dans le Runtime.</span><span class="sxs-lookup"><span data-stu-id="2375e-108">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="2375e-109">Tous les threads du runtime sont suspendus immédiatement s’ils sont déjà dans du code interruptible, ou ils sont invités à s’interrompre lorsqu’ils atteignent du code interruptible.</span><span class="sxs-lookup"><span data-stu-id="2375e-109">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
 <span data-ttu-id="2375e-110">Le rappel de `RuntimeSuspendFinished` est garanti sur le même thread que le rappel [ICorProfilerCallback :: RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="2375e-110">The `RuntimeSuspendFinished` callback is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2375e-111">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="2375e-111">Requirements</span></span>  
 <span data-ttu-id="2375e-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2375e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2375e-113">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2375e-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2375e-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2375e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2375e-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2375e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2375e-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2375e-116">See also</span></span>

- [<span data-ttu-id="2375e-117">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="2375e-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="2375e-118">RuntimeSuspendAborted, méthode</span><span class="sxs-lookup"><span data-stu-id="2375e-118">RuntimeSuspendAborted Method</span></span>](icorprofilercallback-runtimesuspendaborted-method.md)
