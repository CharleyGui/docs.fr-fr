---
title: ICorProfilerCallback::ExceptionUnwindFinallyLeave, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFinallyLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyLeave method [.NET Framework profiling]
- ExceptionUnwindFinallyLeave method [.NET Framework profiling]
ms.assetid: 2350351e-f253-4c0c-a191-f952bc5700e6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0a6b754e6ceef0c451c38055078d403c0601ce45
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755946"
---
# <a name="icorprofilercallbackexceptionunwindfinallyleave-method"></a><span data-ttu-id="5a755-102">ICorProfilerCallback::ExceptionUnwindFinallyLeave, méthode</span><span class="sxs-lookup"><span data-stu-id="5a755-102">ICorProfilerCallback::ExceptionUnwindFinallyLeave Method</span></span>
<span data-ttu-id="5a755-103">Informe le profileur que la phase de déroulement d’exception gestion a quitté un `finally` clause.</span><span class="sxs-lookup"><span data-stu-id="5a755-103">Notifies the profiler that the unwind phase of exception handling has left a `finally` clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a755-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a755-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwindFinallyLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="5a755-105">Notes</span><span class="sxs-lookup"><span data-stu-id="5a755-105">Remarks</span></span>  
 <span data-ttu-id="5a755-106">Le profileur ne doit pas bloquer pendant cet appel, car la pile ne peut pas être dans un état qui autorise le garbage collection, et par conséquent, le garbage collection préemptif ne peut pas être activé.</span><span class="sxs-lookup"><span data-stu-id="5a755-106">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="5a755-107">Si le profileur bloque et un garbage collection est tentée, le runtime bloque jusqu'à ce que ce rappel renvoie.</span><span class="sxs-lookup"><span data-stu-id="5a755-107">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="5a755-108">En outre, pendant cet appel, le profileur doit appeler pas dans le code managé ou de quelque manière qu’une allocation de mémoire managée.</span><span class="sxs-lookup"><span data-stu-id="5a755-108">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a755-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5a755-109">Requirements</span></span>  
 <span data-ttu-id="5a755-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a755-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a755-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5a755-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5a755-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a755-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a755-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a755-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a755-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5a755-114">See also</span></span>

- [<span data-ttu-id="5a755-115">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="5a755-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="5a755-116">ExceptionUnwindFinallyEnter, méthode</span><span class="sxs-lookup"><span data-stu-id="5a755-116">ExceptionUnwindFinallyEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)
