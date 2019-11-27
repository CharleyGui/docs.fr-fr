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
ms.openlocfilehash: 9c9cd0b042dc22f35c38e349ab8881dafc602731
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445019"
---
# <a name="icorprofilercallbackexceptioncatcherenter-method"></a><span data-ttu-id="b5011-102">ICorProfilerCallback::ExceptionCatcherEnter, méthode</span><span class="sxs-lookup"><span data-stu-id="b5011-102">ICorProfilerCallback::ExceptionCatcherEnter Method</span></span>
<span data-ttu-id="b5011-103">Indique au profileur que le contrôle est passé au bloc de `catch` approprié.</span><span class="sxs-lookup"><span data-stu-id="b5011-103">Notifies the profiler that control is being passed to the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5011-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b5011-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCatcherEnter(  
    [in] FunctionID functionId,  
    [in] ObjectID   objectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b5011-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b5011-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="b5011-106">dans Identificateur de la fonction contenant le bloc `catch`.</span><span class="sxs-lookup"><span data-stu-id="b5011-106">[in] The identifier of the function containing the `catch` block.</span></span>  
  
 `objectId`  
 <span data-ttu-id="b5011-107">dans Identificateur de l’exception gérée.</span><span class="sxs-lookup"><span data-stu-id="b5011-107">[in] The identifier of the exception being handled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5011-108">Notes</span><span class="sxs-lookup"><span data-stu-id="b5011-108">Remarks</span></span>  
 <span data-ttu-id="b5011-109">La méthode `ExceptionCatcherEnter` est appelée uniquement si le point catch se trouve dans le code compilé avec le compilateur juste-à-temps (JIT).</span><span class="sxs-lookup"><span data-stu-id="b5011-109">The `ExceptionCatcherEnter` method is called only if the catch point is in code compiled with the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="b5011-110">Une exception interceptée dans du code non managé ou dans le code interne du runtime n’appelle pas cette notification.</span><span class="sxs-lookup"><span data-stu-id="b5011-110">An exception that is caught in unmanaged code or in the internal code of the runtime will not call this notification.</span></span> <span data-ttu-id="b5011-111">La valeur `objectId` est retransmise, car un garbage collection peut avoir déplacé l’objet depuis la notification de `ExceptionThrown`.</span><span class="sxs-lookup"><span data-stu-id="b5011-111">The `objectId` value is passed again since a garbage collection could have moved the object since the `ExceptionThrown` notification.</span></span>  
  
 <span data-ttu-id="b5011-112">Le profileur ne doit pas se bloquer dans son implémentation de cette méthode, car la pile n’est peut-être pas dans un État qui autorise garbage collection, et par conséquent, Preemptive garbage collection ne peut pas être activé.</span><span class="sxs-lookup"><span data-stu-id="b5011-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="b5011-113">Si le profileur est bloqué ici et que garbage collection est tentée, le runtime se bloque jusqu’à ce que ce rappel soit retourné.</span><span class="sxs-lookup"><span data-stu-id="b5011-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="b5011-114">L’implémentation du profileur de cette méthode ne doit pas appeler dans du code managé ou de quelque manière qu’elle provoque une allocation de mémoire managée.</span><span class="sxs-lookup"><span data-stu-id="b5011-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5011-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b5011-115">Requirements</span></span>  
 <span data-ttu-id="b5011-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5011-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5011-117">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b5011-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b5011-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b5011-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b5011-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5011-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5011-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b5011-120">See also</span></span>

- [<span data-ttu-id="b5011-121">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="b5011-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="b5011-122">ExceptionCatcherLeave, méthode</span><span class="sxs-lookup"><span data-stu-id="b5011-122">ExceptionCatcherLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)
