---
title: ICorProfilerCallback::ExceptionCatcherLeave, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCatcherLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCatcherLeave
helpviewer_keywords:
- ExceptionCatcherLeave method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionCatcherLeave method [.NET Framework profiling]
ms.assetid: 1f3dbdf5-db0c-4b07-bbb7-375de2a63673
topic_type:
- apiref
ms.openlocfilehash: c0a24a8f9b7c40d87f9b9b6fe77eba7d6c0ea89f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700026"
---
# <a name="icorprofilercallbackexceptioncatcherleave-method"></a><span data-ttu-id="2f446-102">ICorProfilerCallback::ExceptionCatcherLeave, méthode</span><span class="sxs-lookup"><span data-stu-id="2f446-102">ICorProfilerCallback::ExceptionCatcherLeave Method</span></span>

<span data-ttu-id="2f446-103">Indique au profileur que le contrôle est passé en dehors du `catch` bloc approprié.</span><span class="sxs-lookup"><span data-stu-id="2f446-103">Notifies the profiler that control is being passed out of the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f446-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f446-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCatcherLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="2f446-105">Notes</span><span class="sxs-lookup"><span data-stu-id="2f446-105">Remarks</span></span>  

 <span data-ttu-id="2f446-106">Le profileur ne doit pas se bloquer dans son implémentation de cette méthode, car la pile n’est peut-être pas dans un État qui autorise garbage collection, et par conséquent, Preemptive garbage collection ne peut pas être activé.</span><span class="sxs-lookup"><span data-stu-id="2f446-106">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="2f446-107">Si le profileur est bloqué ici et que garbage collection est tentée, le runtime se bloque jusqu’à ce que ce rappel soit retourné.</span><span class="sxs-lookup"><span data-stu-id="2f446-107">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="2f446-108">L’implémentation du profileur de cette méthode ne doit pas appeler dans du code managé ou de quelque manière qu’elle provoque une allocation de mémoire managée.</span><span class="sxs-lookup"><span data-stu-id="2f446-108">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f446-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2f446-109">Requirements</span></span>  

 <span data-ttu-id="2f446-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f446-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f446-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2f446-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2f446-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f446-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f446-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f446-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f446-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f446-114">See also</span></span>

- [<span data-ttu-id="2f446-115">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="2f446-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="2f446-116">ExceptionCatcherEnter, méthode</span><span class="sxs-lookup"><span data-stu-id="2f446-116">ExceptionCatcherEnter Method</span></span>](icorprofilercallback-exceptioncatcherenter-method.md)
