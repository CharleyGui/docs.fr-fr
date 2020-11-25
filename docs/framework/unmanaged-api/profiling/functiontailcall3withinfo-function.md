---
title: FunctionTailcall3WithInfo, fonction
ms.date: 03/30/2017
api_name:
- FunctionTailcall3WithInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall3WithInfo
helpviewer_keywords:
- FunctionTailcall3WithInfo function [.NET Framework profiling]
ms.assetid: 46380fcc-0198-43ae-a1f5-2d4939425886
topic_type:
- apiref
ms.openlocfilehash: c23c791197c9925038f71e70409e4ca3ebabb23e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722859"
---
# <a name="functiontailcall3withinfo-function"></a><span data-ttu-id="b8677-102">FunctionTailcall3WithInfo, fonction</span><span class="sxs-lookup"><span data-stu-id="b8677-102">FunctionTailcall3WithInfo Function</span></span>

<span data-ttu-id="b8677-103">Indique au profileur que la fonction en cours d’exécution est sur le paragraphe d’effectuer un appel tail à une autre fonction et fournit un handle qui peut être passé à la [méthode ICorProfilerInfo3 :: GetFunctionTailcall3Info,](icorprofilerinfo3-getfunctiontailcall3info-method.md) pour récupérer le frame de pile.</span><span class="sxs-lookup"><span data-stu-id="b8677-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionTailcall3Info method](icorprofilerinfo3-getfunctiontailcall3info-method.md) to retrieve the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8677-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8677-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionTailcall3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8677-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b8677-105">Parameters</span></span>  

- `functionIDOrClientID`

  <span data-ttu-id="b8677-106">\[in] identificateur de la fonction en cours d’exécution qui est sur le paragraphe d’effectuer un appel tail.</span><span class="sxs-lookup"><span data-stu-id="b8677-106">\[in] The identifier of the currently executing function that is about to make a tail call.</span></span>

- `eltInfo`

  <span data-ttu-id="b8677-107">\[in] handle opaque qui représente des informations sur un frame de pile donné.</span><span class="sxs-lookup"><span data-stu-id="b8677-107">\[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="b8677-108">Ce handle est valide uniquement pendant le rappel auquel il est passé.</span><span class="sxs-lookup"><span data-stu-id="b8677-108">This handle is valid only during the callback to which it is passed.</span></span>

## <a name="remarks"></a><span data-ttu-id="b8677-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="b8677-109">Remarks</span></span>  

 <span data-ttu-id="b8677-110">La `FunctionTailcall3WithInfo` méthode de rappel indique au profileur que les fonctions sont appelées et permet au profileur d’utiliser la [méthode ICorProfilerInfo3 :: GetFunctionTailcall3Info,](icorprofilerinfo3-getfunctiontailcall3info-method.md) pour inspecter le frame de pile.</span><span class="sxs-lookup"><span data-stu-id="b8677-110">The `FunctionTailcall3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionTailcall3Info method](icorprofilerinfo3-getfunctiontailcall3info-method.md) to inspect the stack frame.</span></span> <span data-ttu-id="b8677-111">Pour accéder aux informations de frame de pile, l' `COR_PRF_ENABLE_FRAME_INFO` indicateur doit être défini.</span><span class="sxs-lookup"><span data-stu-id="b8677-111">To access stack frame information, the `COR_PRF_ENABLE_FRAME_INFO` flag has to be set.</span></span> <span data-ttu-id="b8677-112">Le profileur peut utiliser la [méthode ICorProfilerInfo :: SetEventMask](icorprofilerinfo-seteventmask-method.md) pour définir les indicateurs d’événement, puis utiliser la [méthode ICorProfilerInfo3 :: SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) pour inscrire votre implémentation de cette fonction.</span><span class="sxs-lookup"><span data-stu-id="b8677-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="b8677-113">La `FunctionTailcall3WithInfo` fonction est un rappel ; vous devez l’implémenter.</span><span class="sxs-lookup"><span data-stu-id="b8677-113">The `FunctionTailcall3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="b8677-114">L’implémentation doit utiliser l' `__declspec(naked)` attribut de classe de stockage.</span><span class="sxs-lookup"><span data-stu-id="b8677-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="b8677-115">Le moteur d’exécution n’enregistre aucun registre avant d’appeler cette fonction.</span><span class="sxs-lookup"><span data-stu-id="b8677-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="b8677-116">À l’entrée, vous devez enregistrer tous les registres que vous utilisez, y compris ceux de l’unité à virgule flottante (FPU).</span><span class="sxs-lookup"><span data-stu-id="b8677-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="b8677-117">À la sortie, vous devez restaurer la pile en dépilant tous les paramètres qui ont été envoyés par son appelant.</span><span class="sxs-lookup"><span data-stu-id="b8677-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="b8677-118">L’implémentation de ne `FunctionTailcall3WithInfo` doit pas se bloquer, car elle retardera garbage collection.</span><span class="sxs-lookup"><span data-stu-id="b8677-118">The implementation of `FunctionTailcall3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="b8677-119">L’implémentation ne doit pas essayer un garbage collection, car la pile n’est peut-être pas dans un État garbage collection.</span><span class="sxs-lookup"><span data-stu-id="b8677-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="b8677-120">Si une garbage collection est tentée, le runtime se bloque jusqu’à ce que `FunctionTailcall3WithInfo` retourne la valeur.</span><span class="sxs-lookup"><span data-stu-id="b8677-120">If a garbage collection is attempted, the runtime will block until `FunctionTailcall3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="b8677-121">En outre, la fonction FunctionTailcall3WithInfo ne doit pas appeler dans du code managé ou provoquer une allocation de mémoire managée de quelque manière que ce soit.</span><span class="sxs-lookup"><span data-stu-id="b8677-121">Also, the FunctionTailcall3WithInfo function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8677-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b8677-122">Requirements</span></span>  

 <span data-ttu-id="b8677-123">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8677-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8677-124">**En-tête :** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="b8677-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="b8677-125">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b8677-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8677-126">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8677-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8677-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b8677-127">See also</span></span>

- [<span data-ttu-id="b8677-128">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="b8677-128">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="b8677-129">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="b8677-129">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="b8677-130">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="b8677-130">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="b8677-131">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="b8677-131">FunctionEnter3WithInfo</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="b8677-132">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="b8677-132">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="b8677-133">Setenterleavefunctionhooks3,</span><span class="sxs-lookup"><span data-stu-id="b8677-133">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="b8677-134">Setenterleavefunctionhooks3withinfo,</span><span class="sxs-lookup"><span data-stu-id="b8677-134">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="b8677-135">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="b8677-135">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="b8677-136">Setfunctionidmapper2,</span><span class="sxs-lookup"><span data-stu-id="b8677-136">SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="b8677-137">Fonctions statiques globales du profilage</span><span class="sxs-lookup"><span data-stu-id="b8677-137">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
