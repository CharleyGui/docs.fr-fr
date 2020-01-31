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
ms.openlocfilehash: 534e0672820cc2509f32765274ad970fda69ec5d
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866505"
---
# <a name="icorprofilercallbackexceptioncatcherenter-method"></a><span data-ttu-id="58553-102">ICorProfilerCallback::ExceptionCatcherEnter, méthode</span><span class="sxs-lookup"><span data-stu-id="58553-102">ICorProfilerCallback::ExceptionCatcherEnter Method</span></span>
<span data-ttu-id="58553-103">Indique au profileur que le contrôle est passé au bloc de `catch` approprié.</span><span class="sxs-lookup"><span data-stu-id="58553-103">Notifies the profiler that control is being passed to the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58553-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58553-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCatcherEnter(  
    [in] FunctionID functionId,  
    [in] ObjectID   objectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="58553-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="58553-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="58553-106">\[in] identificateur de la fonction contenant le bloc `catch`.</span><span class="sxs-lookup"><span data-stu-id="58553-106">\[in] The identifier of the function containing the `catch` block.</span></span>
  
- `objectId`

  <span data-ttu-id="58553-107">\[in] identificateur de l’exception gérée.</span><span class="sxs-lookup"><span data-stu-id="58553-107">\[in] The identifier of the exception being handled.</span></span>

## <a name="remarks"></a><span data-ttu-id="58553-108">Notes</span><span class="sxs-lookup"><span data-stu-id="58553-108">Remarks</span></span>  
 <span data-ttu-id="58553-109">La méthode `ExceptionCatcherEnter` est appelée uniquement si le point catch se trouve dans le code compilé avec le compilateur juste-à-temps (JIT).</span><span class="sxs-lookup"><span data-stu-id="58553-109">The `ExceptionCatcherEnter` method is called only if the catch point is in code compiled with the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="58553-110">Une exception interceptée dans du code non managé ou dans le code interne du runtime n’appelle pas cette notification.</span><span class="sxs-lookup"><span data-stu-id="58553-110">An exception that is caught in unmanaged code or in the internal code of the runtime will not call this notification.</span></span> <span data-ttu-id="58553-111">La valeur `objectId` est retransmise, car un garbage collection peut avoir déplacé l’objet depuis la notification de `ExceptionThrown`.</span><span class="sxs-lookup"><span data-stu-id="58553-111">The `objectId` value is passed again since a garbage collection could have moved the object since the `ExceptionThrown` notification.</span></span>  
  
 <span data-ttu-id="58553-112">Le profileur ne doit pas se bloquer dans son implémentation de cette méthode, car la pile n’est peut-être pas dans un État qui autorise garbage collection, et par conséquent, Preemptive garbage collection ne peut pas être activé.</span><span class="sxs-lookup"><span data-stu-id="58553-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="58553-113">Si le profileur est bloqué ici et que garbage collection est tentée, le runtime se bloque jusqu’à ce que ce rappel soit retourné.</span><span class="sxs-lookup"><span data-stu-id="58553-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="58553-114">L’implémentation du profileur de cette méthode ne doit pas appeler dans du code managé ou de quelque manière qu’elle provoque une allocation de mémoire managée.</span><span class="sxs-lookup"><span data-stu-id="58553-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58553-115">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="58553-115">Requirements</span></span>  
 <span data-ttu-id="58553-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58553-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58553-117">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="58553-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="58553-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58553-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58553-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58553-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58553-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="58553-120">See also</span></span>

- [<span data-ttu-id="58553-121">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="58553-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="58553-122">ExceptionCatcherLeave, méthode</span><span class="sxs-lookup"><span data-stu-id="58553-122">ExceptionCatcherLeave Method</span></span>](icorprofilercallback-exceptioncatcherleave-method.md)
