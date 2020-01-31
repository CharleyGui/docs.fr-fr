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
ms.openlocfilehash: ab7c8cbc41967af04c4c9a8813f32b9b1f01c6a1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866349"
---
# <a name="icorprofilercallbackexceptionunwindfinallyenter-method"></a><span data-ttu-id="356bf-102">ICorProfilerCallback::ExceptionUnwindFinallyEnter, méthode</span><span class="sxs-lookup"><span data-stu-id="356bf-102">ICorProfilerCallback::ExceptionUnwindFinallyEnter Method</span></span>
<span data-ttu-id="356bf-103">Notifie le profileur que la phase de déroulement de la gestion des exceptions introduit une clause `finally` contenue dans la fonction spécifiée.</span><span class="sxs-lookup"><span data-stu-id="356bf-103">Notifies the profiler that the unwind phase of exception handling is entering a `finally` clause contained in the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="356bf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="356bf-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwindFinallyEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="356bf-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="356bf-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="356bf-106">\[in] ID de la fonction qui contient la clause `finally`.</span><span class="sxs-lookup"><span data-stu-id="356bf-106">\[in] The ID of the function that contains the `finally` clause.</span></span>

## <a name="remarks"></a><span data-ttu-id="356bf-107">Notes</span><span class="sxs-lookup"><span data-stu-id="356bf-107">Remarks</span></span>  
 <span data-ttu-id="356bf-108">Le profileur ne doit pas se bloquer dans son implémentation de cette méthode, car la pile n’est peut-être pas dans un État qui autorise garbage collection, et par conséquent, Preemptive garbage collection ne peut pas être activé.</span><span class="sxs-lookup"><span data-stu-id="356bf-108">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="356bf-109">Si le profileur est bloqué ici et que garbage collection est tentée, le runtime se bloque jusqu’à ce que ce rappel soit retourné.</span><span class="sxs-lookup"><span data-stu-id="356bf-109">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="356bf-110">L’implémentation du profileur de cette méthode ne doit pas appeler dans du code managé ou de quelque manière qu’elle provoque une allocation de mémoire managée.</span><span class="sxs-lookup"><span data-stu-id="356bf-110">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="356bf-111">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="356bf-111">Requirements</span></span>  
 <span data-ttu-id="356bf-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="356bf-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="356bf-113">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="356bf-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="356bf-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="356bf-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="356bf-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="356bf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="356bf-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="356bf-116">See also</span></span>

- [<span data-ttu-id="356bf-117">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="356bf-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="356bf-118">GetNotifiedExceptionClauseInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="356bf-118">GetNotifiedExceptionClauseInfo Method</span></span>](icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)
- [<span data-ttu-id="356bf-119">ExceptionUnwindFinallyLeave, méthode</span><span class="sxs-lookup"><span data-stu-id="356bf-119">ExceptionUnwindFinallyLeave Method</span></span>](icorprofilercallback-exceptionunwindfinallyleave-method.md)
