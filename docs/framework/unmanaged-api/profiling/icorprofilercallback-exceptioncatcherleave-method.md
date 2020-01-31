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
ms.openlocfilehash: 6b7aa7c60b5e861787d7a115d90a00d67cc48db0
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866531"
---
# <a name="icorprofilercallbackexceptioncatcherleave-method"></a><span data-ttu-id="2dfa8-102">ICorProfilerCallback::ExceptionCatcherLeave, méthode</span><span class="sxs-lookup"><span data-stu-id="2dfa8-102">ICorProfilerCallback::ExceptionCatcherLeave Method</span></span>
<span data-ttu-id="2dfa8-103">Indique au profileur que le contrôle est passé en dehors du bloc de `catch` approprié.</span><span class="sxs-lookup"><span data-stu-id="2dfa8-103">Notifies the profiler that control is being passed out of the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2dfa8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2dfa8-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCatcherLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="2dfa8-105">Notes</span><span class="sxs-lookup"><span data-stu-id="2dfa8-105">Remarks</span></span>  
 <span data-ttu-id="2dfa8-106">Le profileur ne doit pas se bloquer dans son implémentation de cette méthode, car la pile n’est peut-être pas dans un État qui autorise garbage collection, et par conséquent, Preemptive garbage collection ne peut pas être activé.</span><span class="sxs-lookup"><span data-stu-id="2dfa8-106">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="2dfa8-107">Si le profileur est bloqué ici et que garbage collection est tentée, le runtime se bloque jusqu’à ce que ce rappel soit retourné.</span><span class="sxs-lookup"><span data-stu-id="2dfa8-107">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="2dfa8-108">L’implémentation du profileur de cette méthode ne doit pas appeler dans du code managé ou de quelque manière qu’elle provoque une allocation de mémoire managée.</span><span class="sxs-lookup"><span data-stu-id="2dfa8-108">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2dfa8-109">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="2dfa8-109">Requirements</span></span>  
 <span data-ttu-id="2dfa8-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2dfa8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2dfa8-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2dfa8-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2dfa8-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2dfa8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2dfa8-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2dfa8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dfa8-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2dfa8-114">See also</span></span>

- [<span data-ttu-id="2dfa8-115">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="2dfa8-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="2dfa8-116">ExceptionCatcherEnter, méthode</span><span class="sxs-lookup"><span data-stu-id="2dfa8-116">ExceptionCatcherEnter Method</span></span>](icorprofilercallback-exceptioncatcherenter-method.md)
