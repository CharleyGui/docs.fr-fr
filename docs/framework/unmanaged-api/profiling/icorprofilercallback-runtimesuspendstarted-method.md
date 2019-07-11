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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 20fd186c32857fe547c47d06874f635a5628b178
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750769"
---
# <a name="icorprofilercallbackruntimesuspendstarted-method"></a><span data-ttu-id="68021-102">ICorProfilerCallback::RuntimeSuspendStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="68021-102">ICorProfilerCallback::RuntimeSuspendStarted Method</span></span>
<span data-ttu-id="68021-103">Notifie le profileur que le runtime est sur le point d’interrompre tous les threads d’exécution.</span><span class="sxs-lookup"><span data-stu-id="68021-103">Notifies the profiler that the runtime is about to suspend all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68021-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68021-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendStarted(  
    [in] COR_PRF_SUSPEND_REASON suspendReason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68021-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="68021-105">Parameters</span></span>  
 `suspendReason`  
 <span data-ttu-id="68021-106">[in] Une valeur de la [COR_PRF_SUSPEND_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md) énumération qui indique la raison de la suspension.</span><span class="sxs-lookup"><span data-stu-id="68021-106">[in] A value of the [COR_PRF_SUSPEND_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md) enumeration that indicates the reason for the suspension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68021-107">Notes</span><span class="sxs-lookup"><span data-stu-id="68021-107">Remarks</span></span>  
 <span data-ttu-id="68021-108">Tous les threads de runtime qui se trouvent dans le code non managé sont autorisés à continuer à s’exécuter jusqu'à ce qu’ils essaient d’entrer à nouveau le runtime.</span><span class="sxs-lookup"><span data-stu-id="68021-108">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="68021-109">À ce stade qu’ils seront aussi suspendues jusqu'à ce que le runtime reprend.</span><span class="sxs-lookup"><span data-stu-id="68021-109">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="68021-110">Cela s’applique également aux nouveaux threads qui entrent dans le runtime.</span><span class="sxs-lookup"><span data-stu-id="68021-110">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="68021-111">Tous les threads dans le runtime sont qu'immédiatement suspendus s’ils sont déjà dans du code interruptible, ou ils sont invités à s’interrompre lorsqu’ils atteignent du code interruptible.</span><span class="sxs-lookup"><span data-stu-id="68021-111">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68021-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="68021-112">Requirements</span></span>  
 <span data-ttu-id="68021-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68021-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68021-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="68021-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="68021-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68021-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68021-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68021-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68021-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="68021-117">See also</span></span>

- [<span data-ttu-id="68021-118">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="68021-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="68021-119">RuntimeSuspendAborted, méthode</span><span class="sxs-lookup"><span data-stu-id="68021-119">RuntimeSuspendAborted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)
- [<span data-ttu-id="68021-120">RuntimeSuspendFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="68021-120">RuntimeSuspendFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)
