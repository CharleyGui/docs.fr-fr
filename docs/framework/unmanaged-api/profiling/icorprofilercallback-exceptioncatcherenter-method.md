---
title: ICorProfilerCallback::ExceptionCatcherEnter, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCatcherEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCatcherEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionCatcherEnter method [.NET Framework profiling]
- ExceptionCatcherEnter method [.NET Framework profiling]
ms.assetid: 41462329-a648-46f0-ae6d-728b94c31aa9
topic_type:
- apiref
ms.openlocfilehash: 97b9f517a24a7d82b7697cd0723628ede073b537
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700156"
---
# <a name="icorprofilercallbackexceptioncatcherenter-method"></a><span data-ttu-id="91c0c-102">ICorProfilerCallback::ExceptionCatcherEnter, méthode</span><span class="sxs-lookup"><span data-stu-id="91c0c-102">ICorProfilerCallback::ExceptionCatcherEnter Method</span></span>

<span data-ttu-id="91c0c-103">Indique au profileur que le contrôle est passé au bloc approprié `catch` .</span><span class="sxs-lookup"><span data-stu-id="91c0c-103">Notifies the profiler that control is being passed to the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91c0c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="91c0c-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCatcherEnter(  
    [in] FunctionID functionId,  
    [in] ObjectID   objectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91c0c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="91c0c-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="91c0c-106">\[in] identificateur de la fonction contenant le `catch` bloc.</span><span class="sxs-lookup"><span data-stu-id="91c0c-106">\[in] The identifier of the function containing the `catch` block.</span></span>
  
- `objectId`

  <span data-ttu-id="91c0c-107">\[in] identificateur de l’exception gérée.</span><span class="sxs-lookup"><span data-stu-id="91c0c-107">\[in] The identifier of the exception being handled.</span></span>

## <a name="remarks"></a><span data-ttu-id="91c0c-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="91c0c-108">Remarks</span></span>  

 <span data-ttu-id="91c0c-109">La `ExceptionCatcherEnter` méthode est appelée uniquement si le point catch se trouve dans le code compilé avec le compilateur juste-à-temps (JIT).</span><span class="sxs-lookup"><span data-stu-id="91c0c-109">The `ExceptionCatcherEnter` method is called only if the catch point is in code compiled with the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="91c0c-110">Une exception interceptée dans du code non managé ou dans le code interne du runtime n’appelle pas cette notification.</span><span class="sxs-lookup"><span data-stu-id="91c0c-110">An exception that is caught in unmanaged code or in the internal code of the runtime will not call this notification.</span></span> <span data-ttu-id="91c0c-111">La `objectId` valeur est repassée, car une garbage collection aurait pu déplacer l’objet depuis la `ExceptionThrown` notification.</span><span class="sxs-lookup"><span data-stu-id="91c0c-111">The `objectId` value is passed again since a garbage collection could have moved the object since the `ExceptionThrown` notification.</span></span>  
  
 <span data-ttu-id="91c0c-112">Le profileur ne doit pas se bloquer dans son implémentation de cette méthode, car la pile n’est peut-être pas dans un État qui autorise garbage collection, et par conséquent, Preemptive garbage collection ne peut pas être activé.</span><span class="sxs-lookup"><span data-stu-id="91c0c-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="91c0c-113">Si le profileur est bloqué ici et que garbage collection est tentée, le runtime se bloque jusqu’à ce que ce rappel soit retourné.</span><span class="sxs-lookup"><span data-stu-id="91c0c-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="91c0c-114">L’implémentation du profileur de cette méthode ne doit pas appeler dans du code managé ou de quelque manière qu’elle provoque une allocation de mémoire managée.</span><span class="sxs-lookup"><span data-stu-id="91c0c-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91c0c-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="91c0c-115">Requirements</span></span>  

 <span data-ttu-id="91c0c-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91c0c-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91c0c-117">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="91c0c-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="91c0c-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91c0c-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91c0c-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91c0c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91c0c-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="91c0c-120">See also</span></span>

- [<span data-ttu-id="91c0c-121">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="91c0c-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="91c0c-122">ExceptionCatcherLeave, méthode</span><span class="sxs-lookup"><span data-stu-id="91c0c-122">ExceptionCatcherLeave Method</span></span>](icorprofilercallback-exceptioncatcherleave-method.md)
