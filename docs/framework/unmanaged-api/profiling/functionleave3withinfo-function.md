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
ms.openlocfilehash: 235bae64fe5e6a534f2a650050c6c9ad4aa8fe84
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500622"
---
# <a name="functionleave3withinfo-function"></a><span data-ttu-id="08cfc-102">FunctionLeave3WithInfo, fonction</span><span class="sxs-lookup"><span data-stu-id="08cfc-102">FunctionLeave3WithInfo Function</span></span>
<span data-ttu-id="08cfc-103">Indique au profileur que le contrôle est retourné à partir d’une fonction et fournit un handle qui peut être passé à la [méthode ICorProfilerInfo3 :: GetFunctionLeave3Info,](icorprofilerinfo3-getfunctionleave3info-method.md) pour récupérer le frame de pile et la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="08cfc-103">Notifies the profiler that control is being returned from a function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionLeave3Info method](icorprofilerinfo3-getfunctionleave3info-method.md) to retrieve the stack frame and the return value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08cfc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08cfc-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08cfc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="08cfc-105">Parameters</span></span>

- `functionIDOrClientID`

  <span data-ttu-id="08cfc-106">\[in] identificateur de la fonction à partir de laquelle le contrôle est retourné.</span><span class="sxs-lookup"><span data-stu-id="08cfc-106">\[in] The identifier of the function from which control is returned.</span></span>

- `eltInfo`

  <span data-ttu-id="08cfc-107">\[in] handle opaque qui représente des informations sur un frame de pile donné.</span><span class="sxs-lookup"><span data-stu-id="08cfc-107">\[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="08cfc-108">Ce handle est valide uniquement pendant le rappel auquel il est passé.</span><span class="sxs-lookup"><span data-stu-id="08cfc-108">This handle is valid only during the callback to which it is passed.</span></span>

## <a name="remarks"></a><span data-ttu-id="08cfc-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="08cfc-109">Remarks</span></span>  
 <span data-ttu-id="08cfc-110">La `FunctionLeave3WithInfo` méthode de rappel indique au profileur que les fonctions sont appelées et permet au profileur d’utiliser la [méthode ICorProfilerInfo3 :: GetFunctionLeave3Info,](icorprofilerinfo3-getfunctionleave3info-method.md) pour inspecter la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="08cfc-110">The `FunctionLeave3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionLeave3Info method](icorprofilerinfo3-getfunctionleave3info-method.md) to inspect the return value.</span></span> <span data-ttu-id="08cfc-111">Pour accéder aux informations de valeur de retour, l' `COR_PRF_ENABLE_FUNCTION_RETVAL` indicateur doit être défini.</span><span class="sxs-lookup"><span data-stu-id="08cfc-111">To access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag has to be set.</span></span> <span data-ttu-id="08cfc-112">Le profileur peut utiliser la [méthode ICorProfilerInfo :: SetEventMask](icorprofilerinfo-seteventmask-method.md) pour définir les indicateurs d’événement, puis utiliser la [méthode ICorProfilerInfo3 :: SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) pour inscrire votre implémentation de cette fonction.</span><span class="sxs-lookup"><span data-stu-id="08cfc-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="08cfc-113">La `FunctionLeave3WithInfo` fonction est un rappel ; vous devez l’implémenter.</span><span class="sxs-lookup"><span data-stu-id="08cfc-113">The `FunctionLeave3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="08cfc-114">L’implémentation doit utiliser l' `__declspec(naked)` attribut de classe de stockage.</span><span class="sxs-lookup"><span data-stu-id="08cfc-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="08cfc-115">Le moteur d’exécution n’enregistre aucun registre avant d’appeler cette fonction.</span><span class="sxs-lookup"><span data-stu-id="08cfc-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="08cfc-116">À l’entrée, vous devez enregistrer tous les registres que vous utilisez, y compris ceux de l’unité à virgule flottante (FPU).</span><span class="sxs-lookup"><span data-stu-id="08cfc-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="08cfc-117">À la sortie, vous devez restaurer la pile en dépilant tous les paramètres qui ont été envoyés par son appelant.</span><span class="sxs-lookup"><span data-stu-id="08cfc-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="08cfc-118">L’implémentation de ne `FunctionLeave3WithInfo` doit pas se bloquer, car elle retardera garbage collection.</span><span class="sxs-lookup"><span data-stu-id="08cfc-118">The implementation of `FunctionLeave3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="08cfc-119">L’implémentation ne doit pas essayer un garbage collection, car la pile n’est peut-être pas dans un État garbage collection.</span><span class="sxs-lookup"><span data-stu-id="08cfc-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="08cfc-120">Si une garbage collection est tentée, le runtime se bloque jusqu’à ce que `FunctionLeave3WithInfo` retourne la valeur.</span><span class="sxs-lookup"><span data-stu-id="08cfc-120">If a garbage collection is attempted, the runtime will block until `FunctionLeave3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="08cfc-121">La `FunctionLeave3WithInfo` fonction ne doit pas appeler dans du code managé ou provoquer une allocation de mémoire managée de quelque manière que ce soit.</span><span class="sxs-lookup"><span data-stu-id="08cfc-121">The `FunctionLeave3WithInfo` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08cfc-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="08cfc-122">Requirements</span></span>  
 <span data-ttu-id="08cfc-123">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08cfc-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08cfc-124">**En-tête :** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="08cfc-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="08cfc-125">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="08cfc-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="08cfc-126">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08cfc-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08cfc-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="08cfc-127">See also</span></span>

- [<span data-ttu-id="08cfc-128">Getfunctionleave3info,</span><span class="sxs-lookup"><span data-stu-id="08cfc-128">GetFunctionLeave3Info</span></span>](icorprofilerinfo3-getfunctionleave3info-method.md)
- [<span data-ttu-id="08cfc-129">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="08cfc-129">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="08cfc-130">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="08cfc-130">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="08cfc-131">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="08cfc-131">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="08cfc-132">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="08cfc-132">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="08cfc-133">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="08cfc-133">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="08cfc-134">Setenterleavefunctionhooks3,</span><span class="sxs-lookup"><span data-stu-id="08cfc-134">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="08cfc-135">Setenterleavefunctionhooks3withinfo,</span><span class="sxs-lookup"><span data-stu-id="08cfc-135">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="08cfc-136">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="08cfc-136">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="08cfc-137">Setfunctionidmapper2,</span><span class="sxs-lookup"><span data-stu-id="08cfc-137">SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="08cfc-138">Fonctions statiques globales du profilage</span><span class="sxs-lookup"><span data-stu-id="08cfc-138">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
