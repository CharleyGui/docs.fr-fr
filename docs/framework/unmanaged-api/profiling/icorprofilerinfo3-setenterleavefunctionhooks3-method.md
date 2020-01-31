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
ms.openlocfilehash: 3e07d2b61e85bb626613c40832c1a6aa499ef248
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868497"
---
# <a name="icorprofilerinfo3setenterleavefunctionhooks3-method"></a><span data-ttu-id="71d58-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3, méthode</span><span class="sxs-lookup"><span data-stu-id="71d58-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 Method</span></span>
<span data-ttu-id="71d58-103">Spécifie les fonctions implémentées par le profileur qui seront appelées sur les fonctions [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md)et [FunctionTailcall3](functiontailcall3-function.md) .</span><span class="sxs-lookup"><span data-stu-id="71d58-103">Specifies the profiler-implemented functions that will be called on the [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md), and [FunctionTailcall3](functiontailcall3-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71d58-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="71d58-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks3(  
            [in] FunctionEnter3    *pFuncEnter3,  
            [in] FunctionLeave3    *pFuncLeave3,  
            [in] FunctionTailcall3 *pFuncTailcall3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="71d58-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="71d58-105">Parameters</span></span>  
 `pFuncEnter3`  
 <span data-ttu-id="71d58-106">dans Pointeur vers l’implémentation à utiliser comme rappel `FunctionEnter3`.</span><span class="sxs-lookup"><span data-stu-id="71d58-106">[in] A pointer to the implementation to be used as the `FunctionEnter3` callback.</span></span>  
  
 `pFuncLeave3`  
 <span data-ttu-id="71d58-107">dans Pointeur vers l’implémentation à utiliser comme rappel `FunctionLeave3`.</span><span class="sxs-lookup"><span data-stu-id="71d58-107">[in] A pointer to the implementation to be used as the `FunctionLeave3` callback.</span></span>  
  
 `pFuncTailcall3`  
 <span data-ttu-id="71d58-108">dans Pointeur vers l’implémentation à utiliser comme rappel `FunctionTailcall3`.</span><span class="sxs-lookup"><span data-stu-id="71d58-108">[in] A pointer to the implementation to be used as the `FunctionTailcall3` callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="71d58-109">Notes</span><span class="sxs-lookup"><span data-stu-id="71d58-109">Remarks</span></span>  
 <span data-ttu-id="71d58-110">Les hooks [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md)et [FunctionTailcall3](functiontailcall3-function.md) ne fournissent pas de frame de pile et d’inspection des arguments.</span><span class="sxs-lookup"><span data-stu-id="71d58-110">[FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md), and [FunctionTailcall3](functiontailcall3-function.md) hooks do not provide stack frame and argument inspection.</span></span> <span data-ttu-id="71d58-111">Pour accéder à ces informations, vous devez définir les indicateurs `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`et/ou `COR_PRF_ENABLE_FRAME_INFO`.</span><span class="sxs-lookup"><span data-stu-id="71d58-111">To access that information, the `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, and/or  `COR_PRF_ENABLE_FRAME_INFO` flags have to be set.</span></span> <span data-ttu-id="71d58-112">Le profileur peut utiliser la méthode [ICorProfilerInfo :: SetEventMask](icorprofilerinfo-seteventmask-method.md) pour définir les indicateurs d’événement, puis utiliser la méthode [ICorProfilerInfo3 :: SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) pour inscrire votre implémentation de cette fonction.</span><span class="sxs-lookup"><span data-stu-id="71d58-112">The profiler can use the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) method to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="71d58-113">Un seul ensemble de rappels peut être actif à la fois et la version la plus récente est prioritaire.</span><span class="sxs-lookup"><span data-stu-id="71d58-113">Only one set of callbacks may be active at a time, and the newest version takes precedence.</span></span> <span data-ttu-id="71d58-114">Par conséquent, si un profileur appelle la [méthode SetEnterLeaveFunctionHooks2,](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) et la méthode `SetEnterLeaveFunctionHooks3`, `SetEnterLeaveFunctionHooks3` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="71d58-114">Therefore, if a profiler calls both the [SetEnterLeaveFunctionHooks2 Method](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) and the `SetEnterLeaveFunctionHooks3` method, `SetEnterLeaveFunctionHooks3` is used.</span></span>  
  
 <span data-ttu-id="71d58-115">La méthode `SetEnterLeaveFunctionHooks3` peut être appelée uniquement à partir du rappel [ICorProfilerCallback :: Initialize](icorprofilercallback-initialize-method.md) du profileur.</span><span class="sxs-lookup"><span data-stu-id="71d58-115">The `SetEnterLeaveFunctionHooks3` method may be called only from the profiler's [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71d58-116">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="71d58-116">Requirements</span></span>  
 <span data-ttu-id="71d58-117">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71d58-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71d58-118">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="71d58-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="71d58-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="71d58-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="71d58-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71d58-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71d58-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="71d58-121">See also</span></span>

- [<span data-ttu-id="71d58-122">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="71d58-122">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="71d58-123">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="71d58-123">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="71d58-124">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="71d58-124">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="71d58-125">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="71d58-125">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="71d58-126">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="71d58-126">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="71d58-127">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="71d58-127">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="71d58-128">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="71d58-128">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="71d58-129">Fonctions statiques globales de profilage</span><span class="sxs-lookup"><span data-stu-id="71d58-129">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
- [<span data-ttu-id="71d58-130">ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="71d58-130">ICorProfilerInfo3</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="71d58-131">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="71d58-131">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="71d58-132">Profilage</span><span class="sxs-lookup"><span data-stu-id="71d58-132">Profiling</span></span>](index.md)
