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
ms.openlocfilehash: 7fb58c0eb2446253bd658434fc9d68bb857fe0e6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175120"
---
# <a name="icorprofilercallbackthreadcreated-method"></a><span data-ttu-id="46cd2-102">ICorProfilerCallback::ThreadCreated, méthode</span><span class="sxs-lookup"><span data-stu-id="46cd2-102">ICorProfilerCallback::ThreadCreated Method</span></span>
<span data-ttu-id="46cd2-103">Informe le profileur qu’un fil a été créé.</span><span class="sxs-lookup"><span data-stu-id="46cd2-103">Notifies the profiler that a thread has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46cd2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46cd2-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadCreated(  
    [in] ThreadID threadId);
```  
  
## <a name="parameters"></a><span data-ttu-id="46cd2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="46cd2-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="46cd2-106">[dans] L’ID du fil qui a été créé.</span><span class="sxs-lookup"><span data-stu-id="46cd2-106">[in] The ID of the thread that has been created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46cd2-107">Notes </span><span class="sxs-lookup"><span data-stu-id="46cd2-107">Remarks</span></span>  
 <span data-ttu-id="46cd2-108">La `threadId` valeur est immédiatement valide.</span><span class="sxs-lookup"><span data-stu-id="46cd2-108">The `threadId` value is immediately valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46cd2-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="46cd2-109">Requirements</span></span>  
 <span data-ttu-id="46cd2-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46cd2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46cd2-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="46cd2-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="46cd2-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="46cd2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46cd2-113">**.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46cd2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46cd2-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="46cd2-114">See also</span></span>

- [<span data-ttu-id="46cd2-115">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="46cd2-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="46cd2-116">ThreadDestroyed, méthode</span><span class="sxs-lookup"><span data-stu-id="46cd2-116">ThreadDestroyed Method</span></span>](icorprofilercallback-threaddestroyed-method.md)
