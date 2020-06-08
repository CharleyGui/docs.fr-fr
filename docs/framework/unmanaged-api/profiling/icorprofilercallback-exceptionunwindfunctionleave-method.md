---
title: ICorProfilerCallback::ExceptionUnwindFunctionLeave, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFunctionLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionLeave method [.NET Framework profiling]
- ExceptionUnwindFunctionLeave method [.NET Framework profiling]
ms.assetid: ebaad1d5-ee0a-4cb0-96bc-8ba5d371b747
topic_type:
- apiref
ms.openlocfilehash: 8694a2d19c3b98487b86da4273eb0c68fb9d9ace
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500115"
---
# <a name="icorprofilercallbackexceptionunwindfunctionleave-method"></a><span data-ttu-id="c7747-102">ICorProfilerCallback::ExceptionUnwindFunctionLeave, méthode</span><span class="sxs-lookup"><span data-stu-id="c7747-102">ICorProfilerCallback::ExceptionUnwindFunctionLeave Method</span></span>
<span data-ttu-id="c7747-103">Notifie le profileur que la phase de déroulement de la gestion des exceptions a terminé le déroulement d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="c7747-103">Notifies the profiler that the unwind phase of exception handling has finished unwinding a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7747-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c7747-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwindFunctionLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="c7747-105">Notes</span><span class="sxs-lookup"><span data-stu-id="c7747-105">Remarks</span></span>  
 <span data-ttu-id="c7747-106">Lorsque la `ExceptionUnwindFunctionLeave` méthode est appelée, l’instance de fonction et ses données de pile sont supprimés de la pile.</span><span class="sxs-lookup"><span data-stu-id="c7747-106">When the `ExceptionUnwindFunctionLeave` method is called, the function instance and its stack data are removed from the stack.</span></span>  
  
 <span data-ttu-id="c7747-107">Le profileur ne doit pas se bloquer pendant cet appel, car la pile n’est peut-être pas dans un État qui autorise garbage collection, et par conséquent, Preemptive garbage collection ne peut pas être activé.</span><span class="sxs-lookup"><span data-stu-id="c7747-107">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="c7747-108">Si le profileur est bloqué ici et qu’une garbage collection est tentée, le runtime se bloque jusqu’à ce que ce rappel soit retourné.</span><span class="sxs-lookup"><span data-stu-id="c7747-108">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="c7747-109">En outre, pendant cet appel, le profileur ne doit pas appeler dans du code managé ou de quelque manière qu’il soit à l’origine d’une allocation de mémoire managée.</span><span class="sxs-lookup"><span data-stu-id="c7747-109">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7747-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c7747-110">Requirements</span></span>  
 <span data-ttu-id="c7747-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7747-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7747-112">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c7747-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c7747-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c7747-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7747-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7747-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7747-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c7747-115">See also</span></span>

- [<span data-ttu-id="c7747-116">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="c7747-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="c7747-117">ExceptionUnwindFunctionEnter, méthode</span><span class="sxs-lookup"><span data-stu-id="c7747-117">ExceptionUnwindFunctionEnter Method</span></span>](icorprofilercallback-exceptionunwindfunctionenter-method.md)
