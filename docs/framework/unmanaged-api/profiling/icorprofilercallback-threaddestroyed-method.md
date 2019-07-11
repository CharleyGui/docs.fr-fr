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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f114d32432cccd88e36ff76ed49c610bd03f873e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747016"
---
# <a name="icorprofilercallbackthreaddestroyed-method"></a><span data-ttu-id="ff663-102">ICorProfilerCallback::ThreadDestroyed, méthode</span><span class="sxs-lookup"><span data-stu-id="ff663-102">ICorProfilerCallback::ThreadDestroyed Method</span></span>
<span data-ttu-id="ff663-103">Informe le profileur qu’un thread a été détruit.</span><span class="sxs-lookup"><span data-stu-id="ff663-103">Notifies the profiler that a thread has been destroyed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff663-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff663-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadDestroyed(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff663-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ff663-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="ff663-106">[in] L’ID du thread qui a été détruite.</span><span class="sxs-lookup"><span data-stu-id="ff663-106">[in] The ID of the thread that has been destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff663-107">Notes</span><span class="sxs-lookup"><span data-stu-id="ff663-107">Remarks</span></span>  
 <span data-ttu-id="ff663-108">Le `threadId` valeur n’est plus valide au moment de cet appel.</span><span class="sxs-lookup"><span data-stu-id="ff663-108">The `threadId` value is no longer valid at the time of this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff663-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ff663-109">Requirements</span></span>  
 <span data-ttu-id="ff663-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff663-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff663-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ff663-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ff663-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ff663-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff663-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff663-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff663-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ff663-114">See also</span></span>

- [<span data-ttu-id="ff663-115">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="ff663-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="ff663-116">ThreadCreated, méthode</span><span class="sxs-lookup"><span data-stu-id="ff663-116">ThreadCreated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadcreated-method.md)
