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
ms.openlocfilehash: 5cafbca75992a5fe8a7d3d95628e0018f1a2e8fa
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865946"
---
# <a name="icorprofilercallbackruntimeresumefinished-method"></a><span data-ttu-id="29de4-102">ICorProfilerCallback::RuntimeResumeFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="29de4-102">ICorProfilerCallback::RuntimeResumeFinished Method</span></span>
<span data-ttu-id="29de4-103">Notifie le profileur que le runtime a repris tous les threads d’exécution et qu’il a retourné un fonctionnement normal.</span><span class="sxs-lookup"><span data-stu-id="29de4-103">Notifies the profiler that the runtime has resumed all runtime threads and has returned to normal operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29de4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29de4-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeResumeFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="29de4-105">Notes</span><span class="sxs-lookup"><span data-stu-id="29de4-105">Remarks</span></span>  
 <span data-ttu-id="29de4-106">Il n’est pas garanti que le rappel `RuntimeResumeFinished` se produise sur le même thread que le rappel [ICorProfilerCallback :: RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="29de4-106">The `RuntimeResumeFinished` callback is not guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span> <span data-ttu-id="29de4-107">Toutefois, il est garanti qu’il se produira sur le même thread que le rappel [ICorProfilerCallback :: RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="29de4-107">However, it is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29de4-108">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="29de4-108">Requirements</span></span>  
 <span data-ttu-id="29de4-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29de4-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29de4-110">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="29de4-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="29de4-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29de4-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29de4-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29de4-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29de4-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="29de4-113">See also</span></span>

- [<span data-ttu-id="29de4-114">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="29de4-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
