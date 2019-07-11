---
title: ICorProfilerCallback::ExceptionUnwindFinallyEnter, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFinallyEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyEnter method [.NET Framework profiling]
- ExceptionUnwindFinallyEnter method [.NET Framework profiling]
ms.assetid: c7fab986-b69f-4ec8-b7b7-91dcfc239cd0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3b25ae535bfe50d216ca64a2e8163c0e6df58535
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755965"
---
# <a name="icorprofilercallbackexceptionunwindfinallyenter-method"></a><span data-ttu-id="e258a-102">ICorProfilerCallback::ExceptionUnwindFinallyEnter, méthode</span><span class="sxs-lookup"><span data-stu-id="e258a-102">ICorProfilerCallback::ExceptionUnwindFinallyEnter Method</span></span>
<span data-ttu-id="e258a-103">Notifie le profileur que la phase de déroulement d’exception gestion entre un `finally` clause contenue dans la fonction spécifiée.</span><span class="sxs-lookup"><span data-stu-id="e258a-103">Notifies the profiler that the unwind phase of exception handling is entering a `finally` clause contained in the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e258a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e258a-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwindFinallyEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e258a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e258a-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="e258a-106">[in] L’ID de la fonction qui contient le `finally` clause.</span><span class="sxs-lookup"><span data-stu-id="e258a-106">[in] The ID of the function that contains the `finally` clause.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e258a-107">Notes</span><span class="sxs-lookup"><span data-stu-id="e258a-107">Remarks</span></span>  
 <span data-ttu-id="e258a-108">Le profileur ne doit pas bloquer dans son implémentation de cette méthode, car la pile ne peut pas être dans un état qui autorise le garbage collection, et par conséquent, le garbage collection préemptif ne peut pas être activé.</span><span class="sxs-lookup"><span data-stu-id="e258a-108">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="e258a-109">Si le profileur bloque ici et le garbage collection est tenté, le runtime bloque jusqu'à ce que ce rappel renvoie.</span><span class="sxs-lookup"><span data-stu-id="e258a-109">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="e258a-110">L’implémentation du profileur de cette méthode ne doit pas appeler dans du code managé ou de quelque manière qu’une allocation de mémoire managée.</span><span class="sxs-lookup"><span data-stu-id="e258a-110">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e258a-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e258a-111">Requirements</span></span>  
 <span data-ttu-id="e258a-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e258a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e258a-113">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e258a-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e258a-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e258a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e258a-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e258a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e258a-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e258a-116">See also</span></span>

- [<span data-ttu-id="e258a-117">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="e258a-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="e258a-118">GetNotifiedExceptionClauseInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="e258a-118">GetNotifiedExceptionClauseInfo Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)
- [<span data-ttu-id="e258a-119">ExceptionUnwindFinallyLeave, méthode</span><span class="sxs-lookup"><span data-stu-id="e258a-119">ExceptionUnwindFinallyLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)
