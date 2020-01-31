---
title: ICorProfilerCallback::RuntimeSuspendStarted, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeSuspendStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendStarted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendStarted method [.NET Framework profiling]
- RuntimeSuspendStarted method [.NET Framework profiling]
ms.assetid: c8461cac-e31b-4efa-ad2c-26598173eb96
topic_type:
- apiref
ms.openlocfilehash: e88f6356c2e29a1d8a9e49527c5921e8155c3ce4
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865881"
---
# <a name="icorprofilercallbackruntimesuspendstarted-method"></a><span data-ttu-id="5a10a-102">ICorProfilerCallback::RuntimeSuspendStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="5a10a-102">ICorProfilerCallback::RuntimeSuspendStarted Method</span></span>
<span data-ttu-id="5a10a-103">Indique au profileur que le runtime est sur le paragraphe d’interrompre tous les threads d’exécution.</span><span class="sxs-lookup"><span data-stu-id="5a10a-103">Notifies the profiler that the runtime is about to suspend all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a10a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a10a-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendStarted(  
    [in] COR_PRF_SUSPEND_REASON suspendReason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a10a-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="5a10a-105">Parameters</span></span>  
 `suspendReason`  
 <span data-ttu-id="5a10a-106">dans Valeur de l’énumération [COR_PRF_SUSPEND_REASON](cor-prf-suspend-reason-enumeration.md) qui indique la raison de la suspension.</span><span class="sxs-lookup"><span data-stu-id="5a10a-106">[in] A value of the [COR_PRF_SUSPEND_REASON](cor-prf-suspend-reason-enumeration.md) enumeration that indicates the reason for the suspension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a10a-107">Notes</span><span class="sxs-lookup"><span data-stu-id="5a10a-107">Remarks</span></span>  
 <span data-ttu-id="5a10a-108">Tous les threads d’exécution qui se trouvent dans du code non managé sont autorisés à continuer à s’exécuter jusqu’à ce qu’ils essaient d’entrer à nouveau dans le Runtime.</span><span class="sxs-lookup"><span data-stu-id="5a10a-108">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="5a10a-109">À ce stade, ils sont également suspendus jusqu’à la reprise du Runtime.</span><span class="sxs-lookup"><span data-stu-id="5a10a-109">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="5a10a-110">Cela s’applique également aux nouveaux threads qui entrent dans le Runtime.</span><span class="sxs-lookup"><span data-stu-id="5a10a-110">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="5a10a-111">Tous les threads du runtime sont suspendus immédiatement s’ils sont déjà dans du code interruptible, ou ils sont invités à s’interrompre lorsqu’ils atteignent du code interruptible.</span><span class="sxs-lookup"><span data-stu-id="5a10a-111">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a10a-112">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="5a10a-112">Requirements</span></span>  
 <span data-ttu-id="5a10a-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a10a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a10a-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5a10a-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5a10a-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a10a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a10a-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a10a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a10a-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5a10a-117">See also</span></span>

- [<span data-ttu-id="5a10a-118">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="5a10a-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="5a10a-119">RuntimeSuspendAborted, méthode</span><span class="sxs-lookup"><span data-stu-id="5a10a-119">RuntimeSuspendAborted Method</span></span>](icorprofilercallback-runtimesuspendaborted-method.md)
- [<span data-ttu-id="5a10a-120">RuntimeSuspendFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="5a10a-120">RuntimeSuspendFinished Method</span></span>](icorprofilercallback-runtimesuspendfinished-method.md)
