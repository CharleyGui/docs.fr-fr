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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 62682ca19b9f987370ca11d2bda63fba27f28474
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782993"
---
# <a name="icorprofilercallbackruntimesuspendaborted-method"></a><span data-ttu-id="b00d0-102">ICorProfilerCallback::RuntimeSuspendAborted, méthode</span><span class="sxs-lookup"><span data-stu-id="b00d0-102">ICorProfilerCallback::RuntimeSuspendAborted Method</span></span>
<span data-ttu-id="b00d0-103">Notifie le profileur que le runtime a abandonné la suspension de runtime qui s’est produit.</span><span class="sxs-lookup"><span data-stu-id="b00d0-103">Notifies the profiler that the runtime has aborted the runtime suspension that was occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b00d0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b00d0-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendAborted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="b00d0-105">Notes</span><span class="sxs-lookup"><span data-stu-id="b00d0-105">Remarks</span></span>  
 <span data-ttu-id="b00d0-106">L’exécution peut être abandonné si deux threads tentent simultanément d’arrêter le runtime.</span><span class="sxs-lookup"><span data-stu-id="b00d0-106">The run-time suspension might be aborted if two threads simultaneously attempt to suspend the runtime.</span></span>  
  
 <span data-ttu-id="b00d0-107">Soit le [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) rappel ou `RuntimeSuspendAborted` rappel se produira un suivant le thread unique un [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) rappel.</span><span class="sxs-lookup"><span data-stu-id="b00d0-107">Either the [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) callback or the `RuntimeSuspendAborted` callback will occur on a single thread following a [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
 <span data-ttu-id="b00d0-108">Le `RuntimeSuspendAborted` rappel est assuré de se produire sur le même thread que le `RuntimeSuspendStarted` rappel.</span><span class="sxs-lookup"><span data-stu-id="b00d0-108">The `RuntimeSuspendAborted` callback is guaranteed to occur on the same thread as the `RuntimeSuspendStarted` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b00d0-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b00d0-109">Requirements</span></span>  
 <span data-ttu-id="b00d0-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b00d0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b00d0-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b00d0-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b00d0-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b00d0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b00d0-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b00d0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b00d0-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b00d0-114">See also</span></span>

- [<span data-ttu-id="b00d0-115">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="b00d0-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
