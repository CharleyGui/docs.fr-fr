---
title: FunctionLeave3WithInfo, fonction
ms.date: 03/30/2017
api_name:
- FunctionLeave3WithInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave3WithInfo
helpviewer_keywords:
- FunctionLeave3WithInfo function [.NET Framework profiling]
ms.assetid: 5fa68a67-ced6-41c6-a2c0-467060fd0692
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 495ed887126f0b569acc1309609a0c132d0766eb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763308"
---
# <a name="functionleave3withinfo-function"></a><span data-ttu-id="b8188-102">FunctionLeave3WithInfo, fonction</span><span class="sxs-lookup"><span data-stu-id="b8188-102">FunctionLeave3WithInfo Function</span></span>
<span data-ttu-id="b8188-103">Notifie le profileur que le contrôle a été renvoyé à partir d’une fonction et fournit un handle qui peut être passé à la [ICorProfilerInfo3::GetFunctionLeave3Info, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) pour récupérer le frame de pile et la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="b8188-103">Notifies the profiler that control is being returned from a function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionLeave3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) to retrieve the stack frame and the return value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8188-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8188-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8188-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b8188-105">Parameters</span></span>  
 `functionIDOrClientID`  
 <span data-ttu-id="b8188-106">[in] L’identificateur de la fonction à partir de laquelle le contrôle est retourné.</span><span class="sxs-lookup"><span data-stu-id="b8188-106">[in] The identifier of the function from which control is returned.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="b8188-107">[in] Handle opaque qui représente des informations sur un frame de pile donné.</span><span class="sxs-lookup"><span data-stu-id="b8188-107">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="b8188-108">Ce handle est valide uniquement pendant le rappel auquel il est passé.</span><span class="sxs-lookup"><span data-stu-id="b8188-108">This handle is valid only during the callback to which it is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8188-109">Notes</span><span class="sxs-lookup"><span data-stu-id="b8188-109">Remarks</span></span>  
 <span data-ttu-id="b8188-110">Le `FunctionLeave3WithInfo` méthode de rappel notifie le profileur que les fonctions sont appelées et permet au profileur d’utiliser le [ICorProfilerInfo3::GetFunctionLeave3Info, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) pour inspecter la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="b8188-110">The `FunctionLeave3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionLeave3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) to inspect the return value.</span></span> <span data-ttu-id="b8188-111">Pour accéder aux informations de valeur de retour, le `COR_PRF_ENABLE_FUNCTION_RETVAL` indicateur doit être défini.</span><span class="sxs-lookup"><span data-stu-id="b8188-111">To access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag has to be set.</span></span> <span data-ttu-id="b8188-112">Le profileur peut utiliser le [ICorProfilerInfo::SetEventMask, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) pour définir les indicateurs d’événement, puis utiliser le [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) pour inscrire votre implémentation de cette fonction.</span><span class="sxs-lookup"><span data-stu-id="b8188-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="b8188-113">Le `FunctionLeave3WithInfo` fonction est un rappel ; vous devez l’implémenter.</span><span class="sxs-lookup"><span data-stu-id="b8188-113">The `FunctionLeave3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="b8188-114">L’implémentation doit utiliser le `__declspec(naked)` attribut de classe de stockage.</span><span class="sxs-lookup"><span data-stu-id="b8188-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="b8188-115">Le moteur d’exécution n’enregistre pas les registres avant d’appeler cette fonction.</span><span class="sxs-lookup"><span data-stu-id="b8188-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="b8188-116">À l’entrée, vous devez enregistrer tous les registres que vous utilisez, y compris celles dans l’unité de virgule flottante (FPU).</span><span class="sxs-lookup"><span data-stu-id="b8188-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="b8188-117">À la sortie, vous devez restaurer la pile en dépilant tous les paramètres qui ont été envoyés par son appelant.</span><span class="sxs-lookup"><span data-stu-id="b8188-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="b8188-118">L’implémentation de `FunctionLeave3WithInfo` ne doivent pas bloquer, car il sera retarder le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="b8188-118">The implementation of `FunctionLeave3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="b8188-119">L’implémentation ne doit pas tenter un garbage collection, car la pile est peut-être pas dans un état de la collection convivial garbage.</span><span class="sxs-lookup"><span data-stu-id="b8188-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="b8188-120">Si un garbage collection est tenté, le runtime bloque jusqu'à ce que `FunctionLeave3WithInfo` retourne.</span><span class="sxs-lookup"><span data-stu-id="b8188-120">If a garbage collection is attempted, the runtime will block until `FunctionLeave3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="b8188-121">Le `FunctionLeave3WithInfo` (fonction) ne doit pas appeler dans du code managé ou provoquer une allocation de mémoire managée en aucune façon.</span><span class="sxs-lookup"><span data-stu-id="b8188-121">The `FunctionLeave3WithInfo` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8188-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b8188-122">Requirements</span></span>  
 <span data-ttu-id="b8188-123">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8188-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8188-124">**En-tête :** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="b8188-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="b8188-125">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b8188-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8188-126">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8188-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8188-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b8188-127">See also</span></span>

- [<span data-ttu-id="b8188-128">GetFunctionLeave3Info</span><span class="sxs-lookup"><span data-stu-id="b8188-128">GetFunctionLeave3Info</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md)
- [<span data-ttu-id="b8188-129">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="b8188-129">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="b8188-130">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="b8188-130">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="b8188-131">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="b8188-131">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="b8188-132">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="b8188-132">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="b8188-133">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="b8188-133">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="b8188-134">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="b8188-134">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="b8188-135">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="b8188-135">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="b8188-136">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="b8188-136">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="b8188-137">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="b8188-137">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="b8188-138">Fonctions statiques globales de profilage</span><span class="sxs-lookup"><span data-stu-id="b8188-138">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
