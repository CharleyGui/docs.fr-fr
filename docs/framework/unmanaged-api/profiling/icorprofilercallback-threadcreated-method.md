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
ms.openlocfilehash: 72b074d1794a6039060cbd84aabb0bc0155c154e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717251"
---
# <a name="icorprofilercallbackthreadcreated-method"></a><span data-ttu-id="64d0b-102">ICorProfilerCallback::ThreadCreated, méthode</span><span class="sxs-lookup"><span data-stu-id="64d0b-102">ICorProfilerCallback::ThreadCreated Method</span></span>

<span data-ttu-id="64d0b-103">Notifie le profileur qu’un thread a été créé.</span><span class="sxs-lookup"><span data-stu-id="64d0b-103">Notifies the profiler that a thread has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64d0b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="64d0b-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadCreated(  
    [in] ThreadID threadId);
```  
  
## <a name="parameters"></a><span data-ttu-id="64d0b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="64d0b-105">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="64d0b-106">dans ID du thread qui a été créé.</span><span class="sxs-lookup"><span data-stu-id="64d0b-106">[in] The ID of the thread that has been created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64d0b-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="64d0b-107">Remarks</span></span>  

 <span data-ttu-id="64d0b-108">La `threadId` valeur est immédiatement valide.</span><span class="sxs-lookup"><span data-stu-id="64d0b-108">The `threadId` value is immediately valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64d0b-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="64d0b-109">Requirements</span></span>  

 <span data-ttu-id="64d0b-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64d0b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64d0b-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="64d0b-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="64d0b-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="64d0b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64d0b-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64d0b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64d0b-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="64d0b-114">See also</span></span>

- [<span data-ttu-id="64d0b-115">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="64d0b-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="64d0b-116">ThreadDestroyed, méthode</span><span class="sxs-lookup"><span data-stu-id="64d0b-116">ThreadDestroyed Method</span></span>](icorprofilercallback-threaddestroyed-method.md)
