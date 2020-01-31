---
title: ICorProfilerCallback::ThreadCreated, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ThreadCreated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ThreadCreated
helpviewer_keywords:
- ICorProfilerCallback::ThreadCreated method [.NET Framework profiling]
- ThreadCreated method [.NET Framework profiling]
ms.assetid: cca0f799-09b8-4689-a33c-6d6537943a9b
topic_type:
- apiref
ms.openlocfilehash: 6514606290bf006443d7011c1a428bebb4cca0f6
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865827"
---
# <a name="icorprofilercallbackthreadcreated-method"></a><span data-ttu-id="fb1dd-102">ICorProfilerCallback::ThreadCreated, méthode</span><span class="sxs-lookup"><span data-stu-id="fb1dd-102">ICorProfilerCallback::ThreadCreated Method</span></span>
<span data-ttu-id="fb1dd-103">Notifie le profileur qu’un thread a été créé.</span><span class="sxs-lookup"><span data-stu-id="fb1dd-103">Notifies the profiler that a thread has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb1dd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fb1dd-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadCreated(  
    [in] ThreadID threadId);   
```  
  
## <a name="parameters"></a><span data-ttu-id="fb1dd-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="fb1dd-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="fb1dd-106">dans ID du thread qui a été créé.</span><span class="sxs-lookup"><span data-stu-id="fb1dd-106">[in] The ID of the thread that has been created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb1dd-107">Notes</span><span class="sxs-lookup"><span data-stu-id="fb1dd-107">Remarks</span></span>  
 <span data-ttu-id="fb1dd-108">La valeur `threadId` est immédiatement valide.</span><span class="sxs-lookup"><span data-stu-id="fb1dd-108">The `threadId` value is immediately valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb1dd-109">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="fb1dd-109">Requirements</span></span>  
 <span data-ttu-id="fb1dd-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb1dd-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb1dd-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fb1dd-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fb1dd-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb1dd-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb1dd-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb1dd-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb1dd-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fb1dd-114">See also</span></span>

- [<span data-ttu-id="fb1dd-115">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="fb1dd-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="fb1dd-116">ThreadDestroyed, méthode</span><span class="sxs-lookup"><span data-stu-id="fb1dd-116">ThreadDestroyed Method</span></span>](icorprofilercallback-threaddestroyed-method.md)
