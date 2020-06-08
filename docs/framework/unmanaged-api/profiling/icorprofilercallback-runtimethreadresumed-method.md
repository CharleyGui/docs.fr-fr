---
title: ICorProfilerCallback::RuntimeThreadResumed, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeThreadResumed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeThreadResumed
helpviewer_keywords:
- ICorProfilerCallback::RuntimeThreadResumed method [.NET Framework profiling]
- RuntimeThreadResumed method [.NET Framework profiling]
ms.assetid: da984f89-4f53-4ab0-ae6f-3e2ee6085994
topic_type:
- apiref
ms.openlocfilehash: d3949189a72583ebb50b67a270694a31f1eb23dc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503209"
---
# <a name="icorprofilercallbackruntimethreadresumed-method"></a><span data-ttu-id="1292d-102">ICorProfilerCallback::RuntimeThreadResumed, méthode</span><span class="sxs-lookup"><span data-stu-id="1292d-102">ICorProfilerCallback::RuntimeThreadResumed Method</span></span>
<span data-ttu-id="1292d-103">Notifie le profileur que le thread spécifié a repris après avoir été suspendu.</span><span class="sxs-lookup"><span data-stu-id="1292d-103">Notifies the profiler that the specified thread has resumed after being suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1292d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1292d-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeThreadResumed(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1292d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1292d-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="1292d-106">dans ID du thread qui a été repris.</span><span class="sxs-lookup"><span data-stu-id="1292d-106">[in] The ID of the thread that has been resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1292d-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1292d-107">Requirements</span></span>  
 <span data-ttu-id="1292d-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1292d-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1292d-109">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1292d-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1292d-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1292d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1292d-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1292d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1292d-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1292d-112">See also</span></span>

- [<span data-ttu-id="1292d-113">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="1292d-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="1292d-114">RuntimeThreadSuspended, méthode</span><span class="sxs-lookup"><span data-stu-id="1292d-114">RuntimeThreadSuspended Method</span></span>](icorprofilercallback-runtimethreadsuspended-method.md)
