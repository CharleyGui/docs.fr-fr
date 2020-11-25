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
ms.openlocfilehash: 0cef868861155d553aba42fe28c3f1f1b86763b0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731967"
---
# <a name="icorprofilercallbackthreaddestroyed-method"></a><span data-ttu-id="4918a-102">ICorProfilerCallback::ThreadDestroyed, méthode</span><span class="sxs-lookup"><span data-stu-id="4918a-102">ICorProfilerCallback::ThreadDestroyed Method</span></span>

<span data-ttu-id="4918a-103">Notifie le profileur qu’un thread a été détruit.</span><span class="sxs-lookup"><span data-stu-id="4918a-103">Notifies the profiler that a thread has been destroyed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4918a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4918a-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadDestroyed(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4918a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4918a-105">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="4918a-106">dans ID du thread qui a été détruit.</span><span class="sxs-lookup"><span data-stu-id="4918a-106">[in] The ID of the thread that has been destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4918a-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="4918a-107">Remarks</span></span>  

 <span data-ttu-id="4918a-108">La `threadId` valeur n’est plus valide au moment de cet appel.</span><span class="sxs-lookup"><span data-stu-id="4918a-108">The `threadId` value is no longer valid at the time of this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4918a-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4918a-109">Requirements</span></span>  

 <span data-ttu-id="4918a-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4918a-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4918a-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4918a-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4918a-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4918a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4918a-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4918a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4918a-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4918a-114">See also</span></span>

- [<span data-ttu-id="4918a-115">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="4918a-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="4918a-116">ThreadCreated, méthode</span><span class="sxs-lookup"><span data-stu-id="4918a-116">ThreadCreated Method</span></span>](icorprofilercallback-threadcreated-method.md)
