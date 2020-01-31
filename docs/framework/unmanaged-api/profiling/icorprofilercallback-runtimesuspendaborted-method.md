---
title: ICorProfilerCallback::RuntimeSuspendAborted, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeSuspendAborted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendAborted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendAborted method [.NET Framework profiling]
- RuntimeSuspendAborted method [.NET Framework profiling]
ms.assetid: 5a8a4277-345b-448b-a028-fc8cff9998aa
topic_type:
- apiref
ms.openlocfilehash: 285bdd3f2a96d3c6cb0039382d9944e48c49971a
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865907"
---
# <a name="icorprofilercallbackruntimesuspendaborted-method"></a><span data-ttu-id="77508-102">ICorProfilerCallback::RuntimeSuspendAborted, méthode</span><span class="sxs-lookup"><span data-stu-id="77508-102">ICorProfilerCallback::RuntimeSuspendAborted Method</span></span>
<span data-ttu-id="77508-103">Notifie le profileur que le runtime a abandonné l’interruption d’exécution qui s’est produite.</span><span class="sxs-lookup"><span data-stu-id="77508-103">Notifies the profiler that the runtime has aborted the runtime suspension that was occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77508-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="77508-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendAborted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="77508-105">Notes</span><span class="sxs-lookup"><span data-stu-id="77508-105">Remarks</span></span>  
 <span data-ttu-id="77508-106">La suspension au moment de l’exécution peut être abandonnée si deux threads essaient simultanément de suspendre le Runtime.</span><span class="sxs-lookup"><span data-stu-id="77508-106">The run-time suspension might be aborted if two threads simultaneously attempt to suspend the runtime.</span></span>  
  
 <span data-ttu-id="77508-107">Soit le rappel [ICorProfilerCallback :: RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) , soit le rappel `RuntimeSuspendAborted` se produisent sur un thread unique après un rappel [ICorProfilerCallback :: RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="77508-107">Either the [ICorProfilerCallback::RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) callback or the `RuntimeSuspendAborted` callback will occur on a single thread following a [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
 <span data-ttu-id="77508-108">Le rappel de `RuntimeSuspendAborted` est garanti sur le même thread que le rappel `RuntimeSuspendStarted`.</span><span class="sxs-lookup"><span data-stu-id="77508-108">The `RuntimeSuspendAborted` callback is guaranteed to occur on the same thread as the `RuntimeSuspendStarted` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77508-109">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="77508-109">Requirements</span></span>  
 <span data-ttu-id="77508-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77508-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77508-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="77508-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="77508-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="77508-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77508-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77508-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77508-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="77508-114">See also</span></span>

- [<span data-ttu-id="77508-115">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="77508-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
