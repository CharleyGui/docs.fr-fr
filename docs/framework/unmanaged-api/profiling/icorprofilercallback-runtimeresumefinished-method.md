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
ms.openlocfilehash: e7bd07205a87ecefb658e01db17100a48681b54b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732032"
---
# <a name="icorprofilercallbackruntimeresumefinished-method"></a><span data-ttu-id="6b728-102">ICorProfilerCallback::RuntimeResumeFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="6b728-102">ICorProfilerCallback::RuntimeResumeFinished Method</span></span>

<span data-ttu-id="6b728-103">Notifie le profileur que le runtime a repris tous les threads d’exécution et qu’il a retourné un fonctionnement normal.</span><span class="sxs-lookup"><span data-stu-id="6b728-103">Notifies the profiler that the runtime has resumed all runtime threads and has returned to normal operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b728-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6b728-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeResumeFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="6b728-105">Notes</span><span class="sxs-lookup"><span data-stu-id="6b728-105">Remarks</span></span>  

 <span data-ttu-id="6b728-106">Il n' `RuntimeResumeFinished` est pas garanti que le rappel se produise sur le même thread que le rappel [ICorProfilerCallback :: RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6b728-106">The `RuntimeResumeFinished` callback is not guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span> <span data-ttu-id="6b728-107">Toutefois, il est garanti qu’il se produira sur le même thread que le rappel [ICorProfilerCallback :: RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6b728-107">However, it is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b728-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6b728-108">Requirements</span></span>  

 <span data-ttu-id="6b728-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b728-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b728-110">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6b728-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6b728-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b728-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b728-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b728-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b728-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6b728-113">See also</span></span>

- [<span data-ttu-id="6b728-114">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="6b728-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
