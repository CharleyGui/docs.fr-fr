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
ms.openlocfilehash: b778088f53a3c49def95d715f5fefcb26af81489
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731980"
---
# <a name="icorprofilercallbackruntimesuspendstarted-method"></a><span data-ttu-id="08d03-102">ICorProfilerCallback::RuntimeSuspendStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="08d03-102">ICorProfilerCallback::RuntimeSuspendStarted Method</span></span>

<span data-ttu-id="08d03-103">Indique au profileur que le runtime est sur le paragraphe d’interrompre tous les threads d’exécution.</span><span class="sxs-lookup"><span data-stu-id="08d03-103">Notifies the profiler that the runtime is about to suspend all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08d03-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08d03-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendStarted(  
    [in] COR_PRF_SUSPEND_REASON suspendReason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08d03-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="08d03-105">Parameters</span></span>  

 `suspendReason`  
 <span data-ttu-id="08d03-106">dans Valeur de l’énumération [COR_PRF_SUSPEND_REASON](cor-prf-suspend-reason-enumeration.md) qui indique la raison de la suspension.</span><span class="sxs-lookup"><span data-stu-id="08d03-106">[in] A value of the [COR_PRF_SUSPEND_REASON](cor-prf-suspend-reason-enumeration.md) enumeration that indicates the reason for the suspension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08d03-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="08d03-107">Remarks</span></span>  

 <span data-ttu-id="08d03-108">Tous les threads d’exécution qui se trouvent dans du code non managé sont autorisés à continuer à s’exécuter jusqu’à ce qu’ils essaient d’entrer à nouveau dans le Runtime.</span><span class="sxs-lookup"><span data-stu-id="08d03-108">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="08d03-109">À ce stade, ils sont également suspendus jusqu’à la reprise du Runtime.</span><span class="sxs-lookup"><span data-stu-id="08d03-109">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="08d03-110">Cela s’applique également aux nouveaux threads qui entrent dans le Runtime.</span><span class="sxs-lookup"><span data-stu-id="08d03-110">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="08d03-111">Tous les threads du runtime sont suspendus immédiatement s’ils sont déjà dans du code interruptible, ou ils sont invités à s’interrompre lorsqu’ils atteignent du code interruptible.</span><span class="sxs-lookup"><span data-stu-id="08d03-111">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08d03-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="08d03-112">Requirements</span></span>  

 <span data-ttu-id="08d03-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08d03-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08d03-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="08d03-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="08d03-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="08d03-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="08d03-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08d03-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08d03-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="08d03-117">See also</span></span>

- [<span data-ttu-id="08d03-118">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="08d03-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="08d03-119">RuntimeSuspendAborted, méthode</span><span class="sxs-lookup"><span data-stu-id="08d03-119">RuntimeSuspendAborted Method</span></span>](icorprofilercallback-runtimesuspendaborted-method.md)
- [<span data-ttu-id="08d03-120">RuntimeSuspendFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="08d03-120">RuntimeSuspendFinished Method</span></span>](icorprofilercallback-runtimesuspendfinished-method.md)
