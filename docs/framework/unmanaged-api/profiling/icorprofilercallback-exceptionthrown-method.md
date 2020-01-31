---
title: ICorProfilerCallback::ExceptionThrown, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionThrown
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionThrown
helpviewer_keywords:
- ExceptionThrown method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionThrown method [.NET Framework profiling]
ms.assetid: f1a23f3b-ac21-4905-8abf-8ea59f15af53
topic_type:
- apiref
ms.openlocfilehash: b1799472c4923aaccfabeae459ad72f6ae94c80d
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866375"
---
# <a name="icorprofilercallbackexceptionthrown-method"></a><span data-ttu-id="05d59-102">ICorProfilerCallback::ExceptionThrown, méthode</span><span class="sxs-lookup"><span data-stu-id="05d59-102">ICorProfilerCallback::ExceptionThrown Method</span></span>
<span data-ttu-id="05d59-103">Notifie le profileur qu’une exception a été levée.</span><span class="sxs-lookup"><span data-stu-id="05d59-103">Notifies the profiler that an exception has been thrown.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="05d59-104">Cette fonction est appelée uniquement si l’exception atteint le code managé.</span><span class="sxs-lookup"><span data-stu-id="05d59-104">This function is called only if the exception reaches managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05d59-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05d59-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionThrown(  
    [in] ObjectID thrownObjectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05d59-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="05d59-106">Parameters</span></span>

- `thrownObjectId`

  <span data-ttu-id="05d59-107">\[in] ID de l’objet qui a provoqué la levée de l’exception.</span><span class="sxs-lookup"><span data-stu-id="05d59-107">\[in] The ID of the object that caused the exception to be thrown.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="05d59-108">Notes</span><span class="sxs-lookup"><span data-stu-id="05d59-108">Remarks</span></span>  
 <span data-ttu-id="05d59-109">Le profileur ne doit pas se bloquer dans son implémentation de cette méthode, car la pile n’est peut-être pas dans un État qui autorise garbage collection, et par conséquent, Preemptive garbage collection ne peut pas être activé.</span><span class="sxs-lookup"><span data-stu-id="05d59-109">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="05d59-110">Si le profileur est bloqué ici et que garbage collection est tentée, le runtime se bloque jusqu’à ce que ce rappel soit retourné.</span><span class="sxs-lookup"><span data-stu-id="05d59-110">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="05d59-111">L’implémentation du profileur de cette méthode ne doit pas appeler dans du code managé ou de quelque manière qu’elle provoque une allocation de mémoire managée.</span><span class="sxs-lookup"><span data-stu-id="05d59-111">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05d59-112">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="05d59-112">Requirements</span></span>  
 <span data-ttu-id="05d59-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05d59-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05d59-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="05d59-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="05d59-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="05d59-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05d59-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05d59-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05d59-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="05d59-117">See also</span></span>

- [<span data-ttu-id="05d59-118">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="05d59-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
