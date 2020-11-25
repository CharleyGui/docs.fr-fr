---
title: FunctionEnter3WithInfo, fonction
ms.date: 03/30/2017
api_name:
- FunctionEnter3WithInfo
api_location:
- mscorwks.cll
api_type:
- COM
f1_keywords:
- FunctionEnter3WithInfo
helpviewer_keywords:
- FunctionEnter3WithInfo function [.NET Framework profiling]
ms.assetid: 277c3344-d0cb-431e-beae-eb1eeeba8eea
topic_type:
- apiref
ms.openlocfilehash: b511c5abe10ab6c0ec856a5686b082132ed4a5d9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722858"
---
# <a name="functionenter3withinfo-function"></a><span data-ttu-id="96410-102">FunctionEnter3WithInfo, fonction</span><span class="sxs-lookup"><span data-stu-id="96410-102">FunctionEnter3WithInfo Function</span></span>

<span data-ttu-id="96410-103">Notifie le profileur que le contrôle est passé à une fonction et fournit un handle qui peut être passé à la [méthode ICorProfilerInfo3 :: GetFunctionEnter3Info,](icorprofilerinfo3-getfunctionenter3info-method.md) pour récupérer le frame de pile et les arguments de fonction.</span><span class="sxs-lookup"><span data-stu-id="96410-103">Notifies the profiler that control is being passed to a function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionEnter3Info method](icorprofilerinfo3-getfunctionenter3info-method.md) to retrieve the stack frame and function arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96410-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="96410-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96410-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="96410-105">Parameters</span></span>

- `functionIDOrClientID`

  <span data-ttu-id="96410-106">\[in] identificateur de la fonction vers laquelle le contrôle est passé.</span><span class="sxs-lookup"><span data-stu-id="96410-106">\[in] The identifier of the function to which control is passed.</span></span>

- `eltInfo`

  <span data-ttu-id="96410-107">\[in] handle opaque qui représente des informations sur un frame de pile donné.</span><span class="sxs-lookup"><span data-stu-id="96410-107">\[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="96410-108">Ce handle est valide uniquement pendant le rappel auquel il est passé.</span><span class="sxs-lookup"><span data-stu-id="96410-108">This handle is valid only during the callback to which it is passed.</span></span>

## <a name="remarks"></a><span data-ttu-id="96410-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="96410-109">Remarks</span></span>  

 <span data-ttu-id="96410-110">La `FunctionEnter3WithInfo` méthode de rappel indique au profileur que les fonctions sont appelées et permet au profileur d’utiliser la [méthode ICorProfilerInfo3 :: GetFunctionEnter3Info,](icorprofilerinfo3-getfunctionenter3info-method.md) pour inspecter les valeurs des arguments.</span><span class="sxs-lookup"><span data-stu-id="96410-110">The `FunctionEnter3WithInfo` callback method notifies the profiler as functions are called, and enables the profiler to use the [ICorProfilerInfo3::GetFunctionEnter3Info method](icorprofilerinfo3-getfunctionenter3info-method.md) to inspect argument values.</span></span> <span data-ttu-id="96410-111">Pour accéder aux informations d’argument, l' `COR_PRF_ENABLE_FUNCTION_ARGS` indicateur doit être défini.</span><span class="sxs-lookup"><span data-stu-id="96410-111">To access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag has to be set.</span></span> <span data-ttu-id="96410-112">Le profileur peut utiliser la [méthode ICorProfilerInfo :: SetEventMask](icorprofilerinfo-seteventmask-method.md) pour définir les indicateurs d’événement, puis utiliser la [méthode ICorProfilerInfo3 :: SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) pour inscrire votre implémentation de cette fonction.</span><span class="sxs-lookup"><span data-stu-id="96410-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="96410-113">La `FunctionEnter3WithInfo` fonction est un rappel ; vous devez l’implémenter.</span><span class="sxs-lookup"><span data-stu-id="96410-113">The `FunctionEnter3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="96410-114">L’implémentation doit utiliser l' `__declspec(naked)` attribut de classe de stockage.</span><span class="sxs-lookup"><span data-stu-id="96410-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="96410-115">Le moteur d’exécution n’enregistre aucun registre avant d’appeler cette fonction.</span><span class="sxs-lookup"><span data-stu-id="96410-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="96410-116">À l’entrée, vous devez enregistrer tous les registres que vous utilisez, y compris ceux de l’unité à virgule flottante (FPU).</span><span class="sxs-lookup"><span data-stu-id="96410-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="96410-117">À la sortie, vous devez restaurer la pile en dépilant tous les paramètres qui ont été envoyés par son appelant.</span><span class="sxs-lookup"><span data-stu-id="96410-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="96410-118">L’implémentation de ne `FunctionEnter3WithInfo` doit pas se bloquer, car elle retardera garbage collection.</span><span class="sxs-lookup"><span data-stu-id="96410-118">The implementation of `FunctionEnter3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="96410-119">L’implémentation ne doit pas essayer un garbage collection, car la pile n’est peut-être pas dans un État garbage collection.</span><span class="sxs-lookup"><span data-stu-id="96410-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="96410-120">Si une garbage collection est tentée, le runtime se bloque jusqu’à ce que `FunctionEnter3WithInfo` retourne la valeur.</span><span class="sxs-lookup"><span data-stu-id="96410-120">If a garbage collection is attempted, the runtime will block until `FunctionEnter3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="96410-121">La `FunctionEnter3WithInfo` fonction ne doit pas appeler dans du code managé ou provoquer une allocation de mémoire managée de quelque manière que ce soit.</span><span class="sxs-lookup"><span data-stu-id="96410-121">The `FunctionEnter3WithInfo` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96410-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="96410-122">Requirements</span></span>  

 <span data-ttu-id="96410-123">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96410-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96410-124">**En-tête :** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="96410-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="96410-125">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="96410-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96410-126">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96410-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96410-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="96410-127">See also</span></span>

- [<span data-ttu-id="96410-128">Getfunctionenter3info,</span><span class="sxs-lookup"><span data-stu-id="96410-128">GetFunctionEnter3Info</span></span>](icorprofilerinfo3-getfunctionenter3info-method.md)
- [<span data-ttu-id="96410-129">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="96410-129">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="96410-130">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="96410-130">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="96410-131">Fonctions statiques globales du profilage</span><span class="sxs-lookup"><span data-stu-id="96410-131">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
