---
title: ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.SetEnterLeaveFunctionHooks3WithInfo Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo
helpviewer_keywords:
- SetEnterLeaveFunctionHooks3WithInfo method [.NET Framework profiling]
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method [.NET Framework profiling]
ms.assetid: ca8ea534-e441-47b8-be85-466410988c0a
topic_type:
- apiref
ms.openlocfilehash: 4fe18b4f07e6f282571b13faff5ce51b66ce416b
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868484"
---
# <a name="icorprofilerinfo3setenterleavefunctionhooks3withinfo-method"></a><span data-ttu-id="bbe6a-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="bbe6a-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo Method</span></span>
<span data-ttu-id="bbe6a-103">Spécifie les fonctions implémentées par le profileur qui seront appelées sur les raccordements [FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md)et [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) des fonctions managées.</span><span class="sxs-lookup"><span data-stu-id="bbe6a-103">Specifies the profiler-implemented functions that will be called on the [FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbe6a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bbe6a-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks3WithInfo(  
            [in] FunctionEnter3WithInfo    *pFuncEnter3,  
            [in] FunctionLeave3withInfo    *pFuncLeave3,  
            [in] FunctionTailcall3WithInfo *pFuncTailcall3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bbe6a-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="bbe6a-105">Parameters</span></span>  
 `pFuncEnter3`  
 <span data-ttu-id="bbe6a-106">dans Pointeur vers l’implémentation à utiliser comme rappel `FunctionEnter3WithInfo`.</span><span class="sxs-lookup"><span data-stu-id="bbe6a-106">[in] A pointer to the implementation to be used as the `FunctionEnter3WithInfo` callback.</span></span>  
  
 `pFuncLeave3`  
 <span data-ttu-id="bbe6a-107">dans Pointeur vers l’implémentation à utiliser comme rappel `FunctionLeave3WithInfo`.</span><span class="sxs-lookup"><span data-stu-id="bbe6a-107">[in] A pointer to the implementation to be used as the `FunctionLeave3WithInfo` callback.</span></span>  
  
 `pFuncTailcall3`  
 <span data-ttu-id="bbe6a-108">dans Pointeur vers l’implémentation à utiliser comme rappel `FunctionTailcall3WithInfo`.</span><span class="sxs-lookup"><span data-stu-id="bbe6a-108">[in] A pointer to the implementation to be used as the `FunctionTailcall3WithInfo` callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bbe6a-109">Notes</span><span class="sxs-lookup"><span data-stu-id="bbe6a-109">Remarks</span></span>  
 <span data-ttu-id="bbe6a-110">Les raccordements [FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md)et [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) fournissent le frame de pile et l’inspection des arguments.</span><span class="sxs-lookup"><span data-stu-id="bbe6a-110">The [FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) hooks provide stack frame and argument inspection.</span></span> <span data-ttu-id="bbe6a-111">Pour accéder à ces informations, vous devez définir les indicateurs `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`et/ou `COR_PRF_ENABLE_FRAME_INFO`.</span><span class="sxs-lookup"><span data-stu-id="bbe6a-111">To access that information, the `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, and/or `COR_PRF_ENABLE_FRAME_INFO` flags have to be set.</span></span> <span data-ttu-id="bbe6a-112">Le profileur peut utiliser la méthode [ICorProfilerInfo :: SetEventMask](icorprofilerinfo-seteventmask-method.md) pour définir les indicateurs d’événement, puis utiliser la méthode `SetEnterLeaveFunctionHooks3WithInfo` pour inscrire votre implémentation de cette fonction.</span><span class="sxs-lookup"><span data-stu-id="bbe6a-112">The profiler can use the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the event flags, and then use the `SetEnterLeaveFunctionHooks3WithInfo` method to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="bbe6a-113">Un seul ensemble de rappels peut être actif à la fois et la version la plus récente est prioritaire.</span><span class="sxs-lookup"><span data-stu-id="bbe6a-113">Only one set of callbacks may be active at a time, and the newest version takes precedence.</span></span> <span data-ttu-id="bbe6a-114">Par conséquent, si un profileur appelle à la fois [SetEnterLeaveFunctionHooks2,](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) et `SetEnterLeaveFunctionHooks3WithInfo`, `SetEnterLeaveFunctionHooks3WithInfo` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="bbe6a-114">Therefore, if a profiler calls both [SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) and `SetEnterLeaveFunctionHooks3WithInfo`, `SetEnterLeaveFunctionHooks3WithInfo` is used.</span></span>  
  
 <span data-ttu-id="bbe6a-115">La méthode `SetEnterLeaveFunctionHooks3WithInfo` peut être appelée uniquement à partir du rappel [ICorProfilerCallback :: Initialize](icorprofilercallback-initialize-method.md) du profileur.</span><span class="sxs-lookup"><span data-stu-id="bbe6a-115">The `SetEnterLeaveFunctionHooks3WithInfo` method may be called only from the profiler's [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbe6a-116">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="bbe6a-116">Requirements</span></span>  
 <span data-ttu-id="bbe6a-117">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bbe6a-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbe6a-118">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bbe6a-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bbe6a-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bbe6a-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bbe6a-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbe6a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbe6a-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bbe6a-121">See also</span></span>

- [<span data-ttu-id="bbe6a-122">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="bbe6a-122">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="bbe6a-123">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="bbe6a-123">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="bbe6a-124">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="bbe6a-124">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="bbe6a-125">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="bbe6a-125">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="bbe6a-126">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="bbe6a-126">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="bbe6a-127">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="bbe6a-127">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="bbe6a-128">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="bbe6a-128">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="bbe6a-129">Fonctions statiques globales de profilage</span><span class="sxs-lookup"><span data-stu-id="bbe6a-129">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
- [<span data-ttu-id="bbe6a-130">ICorProfilerInfo3, interface</span><span class="sxs-lookup"><span data-stu-id="bbe6a-130">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="bbe6a-131">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="bbe6a-131">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="bbe6a-132">Profilage</span><span class="sxs-lookup"><span data-stu-id="bbe6a-132">Profiling</span></span>](index.md)
