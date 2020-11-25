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
ms.openlocfilehash: e02716350aa2bf32bdd7c4b2e01841405de6dc14
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720397"
---
# <a name="icorprofilercallbackexceptionunwindfinallyleave-method"></a><span data-ttu-id="8ab27-102">ICorProfilerCallback::ExceptionUnwindFinallyLeave, méthode</span><span class="sxs-lookup"><span data-stu-id="8ab27-102">ICorProfilerCallback::ExceptionUnwindFinallyLeave Method</span></span>

<span data-ttu-id="8ab27-103">Notifie le profileur que la phase de déroulement de la gestion des exceptions a quitté une `finally` clause.</span><span class="sxs-lookup"><span data-stu-id="8ab27-103">Notifies the profiler that the unwind phase of exception handling has left a `finally` clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ab27-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ab27-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwindFinallyLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="8ab27-105">Notes</span><span class="sxs-lookup"><span data-stu-id="8ab27-105">Remarks</span></span>  

 <span data-ttu-id="8ab27-106">Le profileur ne doit pas se bloquer pendant cet appel, car la pile n’est peut-être pas dans un État qui autorise garbage collection, et par conséquent, Preemptive garbage collection ne peut pas être activé.</span><span class="sxs-lookup"><span data-stu-id="8ab27-106">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="8ab27-107">Si le profileur est bloqué ici et qu’une garbage collection est tentée, le runtime se bloque jusqu’à ce que ce rappel soit retourné.</span><span class="sxs-lookup"><span data-stu-id="8ab27-107">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="8ab27-108">En outre, pendant cet appel, le profileur ne doit pas appeler dans du code managé ou de quelque manière qu’il soit à l’origine d’une allocation de mémoire managée.</span><span class="sxs-lookup"><span data-stu-id="8ab27-108">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ab27-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8ab27-109">Requirements</span></span>  

 <span data-ttu-id="8ab27-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ab27-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ab27-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8ab27-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8ab27-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ab27-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ab27-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ab27-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ab27-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ab27-114">See also</span></span>

- [<span data-ttu-id="8ab27-115">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="8ab27-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="8ab27-116">ExceptionUnwindFinallyEnter, méthode</span><span class="sxs-lookup"><span data-stu-id="8ab27-116">ExceptionUnwindFinallyEnter Method</span></span>](icorprofilercallback-exceptionunwindfinallyenter-method.md)
