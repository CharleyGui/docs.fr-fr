---
title: ICorProfilerInfo3::SetEnterLeaveFunctionHooks3, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.SetEnterLeaveFunctionHooks3 Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3
helpviewer_keywords:
- SetEnterLeaveFunctionHooks3 method [.NET Framework profiling]
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method [.NET Framework profiling]
ms.assetid: f0621465-b84f-40ab-a4e5-56a7abc776a7
topic_type:
- apiref
ms.openlocfilehash: a7272d55771620db129125ce543d12d19a0b4dfb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697842"
---
# <a name="icorprofilerinfo3setenterleavefunctionhooks3-method"></a><span data-ttu-id="ff17d-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3, méthode</span><span class="sxs-lookup"><span data-stu-id="ff17d-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 Method</span></span>

<span data-ttu-id="ff17d-103">Spécifie les fonctions implémentées par le profileur qui seront appelées sur les fonctions [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md)et [FunctionTailcall3](functiontailcall3-function.md) .</span><span class="sxs-lookup"><span data-stu-id="ff17d-103">Specifies the profiler-implemented functions that will be called on the [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md), and [FunctionTailcall3](functiontailcall3-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff17d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff17d-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks3(  
            [in] FunctionEnter3    *pFuncEnter3,  
            [in] FunctionLeave3    *pFuncLeave3,  
            [in] FunctionTailcall3 *pFuncTailcall3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff17d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ff17d-105">Parameters</span></span>  

 `pFuncEnter3`  
 <span data-ttu-id="ff17d-106">dans Pointeur vers l’implémentation à utiliser comme `FunctionEnter3` rappel.</span><span class="sxs-lookup"><span data-stu-id="ff17d-106">[in] A pointer to the implementation to be used as the `FunctionEnter3` callback.</span></span>  
  
 `pFuncLeave3`  
 <span data-ttu-id="ff17d-107">dans Pointeur vers l’implémentation à utiliser comme `FunctionLeave3` rappel.</span><span class="sxs-lookup"><span data-stu-id="ff17d-107">[in] A pointer to the implementation to be used as the `FunctionLeave3` callback.</span></span>  
  
 `pFuncTailcall3`  
 <span data-ttu-id="ff17d-108">dans Pointeur vers l’implémentation à utiliser comme `FunctionTailcall3` rappel.</span><span class="sxs-lookup"><span data-stu-id="ff17d-108">[in] A pointer to the implementation to be used as the `FunctionTailcall3` callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff17d-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="ff17d-109">Remarks</span></span>  

 <span data-ttu-id="ff17d-110">Les hooks [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md)et [FunctionTailcall3](functiontailcall3-function.md) ne fournissent pas de frame de pile et d’inspection des arguments.</span><span class="sxs-lookup"><span data-stu-id="ff17d-110">[FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md), and [FunctionTailcall3](functiontailcall3-function.md) hooks do not provide stack frame and argument inspection.</span></span> <span data-ttu-id="ff17d-111">Pour accéder à ces informations, `COR_PRF_ENABLE_FUNCTION_ARGS` les `COR_PRF_ENABLE_FUNCTION_RETVAL` indicateurs,, et  `COR_PRF_ENABLE_FRAME_INFO` doivent être définis.</span><span class="sxs-lookup"><span data-stu-id="ff17d-111">To access that information, the `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, and/or  `COR_PRF_ENABLE_FRAME_INFO` flags have to be set.</span></span> <span data-ttu-id="ff17d-112">Le profileur peut utiliser la méthode [ICorProfilerInfo :: SetEventMask](icorprofilerinfo-seteventmask-method.md) pour définir les indicateurs d’événement, puis utiliser la méthode [ICorProfilerInfo3 :: SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) pour inscrire votre implémentation de cette fonction.</span><span class="sxs-lookup"><span data-stu-id="ff17d-112">The profiler can use the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) method to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="ff17d-113">Un seul ensemble de rappels peut être actif à la fois et la version la plus récente est prioritaire.</span><span class="sxs-lookup"><span data-stu-id="ff17d-113">Only one set of callbacks may be active at a time, and the newest version takes precedence.</span></span> <span data-ttu-id="ff17d-114">Par conséquent, si un profileur appelle la [méthode SetEnterLeaveFunctionHooks2,](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) et la `SetEnterLeaveFunctionHooks3` méthode, `SetEnterLeaveFunctionHooks3` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="ff17d-114">Therefore, if a profiler calls both the [SetEnterLeaveFunctionHooks2 Method](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) and the `SetEnterLeaveFunctionHooks3` method, `SetEnterLeaveFunctionHooks3` is used.</span></span>  
  
 <span data-ttu-id="ff17d-115">La `SetEnterLeaveFunctionHooks3` méthode peut être appelée uniquement à partir du rappel [ICorProfilerCallback :: Initialize](icorprofilercallback-initialize-method.md) du profileur.</span><span class="sxs-lookup"><span data-stu-id="ff17d-115">The `SetEnterLeaveFunctionHooks3` method may be called only from the profiler's [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff17d-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ff17d-116">Requirements</span></span>  

 <span data-ttu-id="ff17d-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff17d-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff17d-118">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ff17d-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ff17d-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ff17d-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff17d-120">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff17d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff17d-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ff17d-121">See also</span></span>

- [<span data-ttu-id="ff17d-122">Setenterleavefunctionhooks3withinfo,</span><span class="sxs-lookup"><span data-stu-id="ff17d-122">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="ff17d-123">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="ff17d-123">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="ff17d-124">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="ff17d-124">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="ff17d-125">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="ff17d-125">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="ff17d-126">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="ff17d-126">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="ff17d-127">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="ff17d-127">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="ff17d-128">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="ff17d-128">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="ff17d-129">Fonctions statiques globales du profilage</span><span class="sxs-lookup"><span data-stu-id="ff17d-129">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
- [<span data-ttu-id="ff17d-130">ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="ff17d-130">ICorProfilerInfo3</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="ff17d-131">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="ff17d-131">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="ff17d-132">Profilage</span><span class="sxs-lookup"><span data-stu-id="ff17d-132">Profiling</span></span>](index.md)
