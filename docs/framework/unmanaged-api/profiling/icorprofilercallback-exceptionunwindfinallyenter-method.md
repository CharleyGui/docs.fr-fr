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
ms.openlocfilehash: f5e4939c814239c297fc0aa88644dc0472b0c419
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500154"
---
# <a name="icorprofilercallbackexceptionunwindfinallyenter-method"></a><span data-ttu-id="37201-102">ICorProfilerCallback::ExceptionUnwindFinallyEnter, méthode</span><span class="sxs-lookup"><span data-stu-id="37201-102">ICorProfilerCallback::ExceptionUnwindFinallyEnter Method</span></span>
<span data-ttu-id="37201-103">Notifie le profileur que la phase de déroulement de la gestion des exceptions introduit une `finally` clause contenue dans la fonction spécifiée.</span><span class="sxs-lookup"><span data-stu-id="37201-103">Notifies the profiler that the unwind phase of exception handling is entering a `finally` clause contained in the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37201-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="37201-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwindFinallyEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="37201-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="37201-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="37201-106">\[in] ID de la fonction qui contient la `finally` clause.</span><span class="sxs-lookup"><span data-stu-id="37201-106">\[in] The ID of the function that contains the `finally` clause.</span></span>

## <a name="remarks"></a><span data-ttu-id="37201-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="37201-107">Remarks</span></span>  
 <span data-ttu-id="37201-108">Le profileur ne doit pas se bloquer dans son implémentation de cette méthode, car la pile n’est peut-être pas dans un État qui autorise garbage collection, et par conséquent, Preemptive garbage collection ne peut pas être activé.</span><span class="sxs-lookup"><span data-stu-id="37201-108">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="37201-109">Si le profileur est bloqué ici et que garbage collection est tentée, le runtime se bloque jusqu’à ce que ce rappel soit retourné.</span><span class="sxs-lookup"><span data-stu-id="37201-109">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="37201-110">L’implémentation du profileur de cette méthode ne doit pas appeler dans du code managé ou de quelque manière qu’elle provoque une allocation de mémoire managée.</span><span class="sxs-lookup"><span data-stu-id="37201-110">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37201-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="37201-111">Requirements</span></span>  
 <span data-ttu-id="37201-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37201-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37201-113">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="37201-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="37201-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="37201-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="37201-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37201-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37201-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="37201-116">See also</span></span>

- [<span data-ttu-id="37201-117">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="37201-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="37201-118">GetNotifiedExceptionClauseInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="37201-118">GetNotifiedExceptionClauseInfo Method</span></span>](icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)
- [<span data-ttu-id="37201-119">ExceptionUnwindFinallyLeave, méthode</span><span class="sxs-lookup"><span data-stu-id="37201-119">ExceptionUnwindFinallyLeave Method</span></span>](icorprofilercallback-exceptionunwindfinallyleave-method.md)
