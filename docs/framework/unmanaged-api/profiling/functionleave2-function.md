---
title: FunctionLeave2 (fonction)
ms.date: 03/30/2017
api_name:
- FunctionLeave2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave2
helpviewer_keywords:
- FunctionLeave2 function [.NET Framework profiling]
ms.assetid: 8cdac941-8b94-4497-b874-4e571785f3fe
topic_type:
- apiref
ms.openlocfilehash: 0b1ecd1266528f8a08ef114de2f111dd0f71ca8b
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866929"
---
# <a name="functionleave2-function"></a><span data-ttu-id="94549-102">FunctionLeave2 (fonction)</span><span class="sxs-lookup"><span data-stu-id="94549-102">FunctionLeave2 Function</span></span>
<span data-ttu-id="94549-103">Notifie le profileur qu’une fonction va retourner à l’appelant et fournit des informations sur le frame de pile et la valeur de retour de fonction.</span><span class="sxs-lookup"><span data-stu-id="94549-103">Notifies the profiler that a function is about to return to the caller and provides information about the stack frame and function return value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94549-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="94549-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave2 (  
    [in]  FunctionID                        funcId,  
    [in]  UINT_PTR                          clientData,  
    [in]  COR_PRF_FRAME_INFO                func,  
    [in]  COR_PRF_FUNCTION_ARGUMENT_RANGE  *retvalRange  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94549-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="94549-105">Parameters</span></span>

- `funcId`

  <span data-ttu-id="94549-106">\[in] identificateur de la fonction qui retourne.</span><span class="sxs-lookup"><span data-stu-id="94549-106">\[in] The identifier of the function that is returning.</span></span>

- `clientData`

  <span data-ttu-id="94549-107">\[dans] identificateur de fonction remappée, que le profileur a précédemment spécifié via la fonction [FunctionIDMapper](functionidmapper-function.md) .</span><span class="sxs-lookup"><span data-stu-id="94549-107">\[in] The remapped function identifier, which the profiler previously specified via the [FunctionIDMapper](functionidmapper-function.md) function.</span></span>

- `func`

  <span data-ttu-id="94549-108">\[dans] valeur `COR_PRF_FRAME_INFO` qui pointe vers les informations sur le frame de pile.</span><span class="sxs-lookup"><span data-stu-id="94549-108">\[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>

  <span data-ttu-id="94549-109">Le profileur doit traiter ceci comme un handle opaque qui peut être retourné au moteur d’exécution dans la méthode [ICorProfilerInfo2 :: GetFunctionInfo2,](icorprofilerinfo2-getfunctioninfo2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="94549-109">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
- `retvalRange`

  <span data-ttu-id="94549-110">\[in] pointeur vers une structure [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) qui spécifie l’emplacement de mémoire de la valeur de retour de la fonction.</span><span class="sxs-lookup"><span data-stu-id="94549-110">\[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) structure that specifies the memory location of the function's return value.</span></span>

  <span data-ttu-id="94549-111">Pour accéder aux informations de valeur de retour, l’indicateur `COR_PRF_ENABLE_FUNCTION_RETVAL` doit être défini.</span><span class="sxs-lookup"><span data-stu-id="94549-111">In order to access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span></span> <span data-ttu-id="94549-112">Le profileur peut utiliser la méthode [ICorProfilerInfo :: SetEventMask](icorprofilerinfo-seteventmask-method.md) pour définir les indicateurs d’événement.</span><span class="sxs-lookup"><span data-stu-id="94549-112">The profiler can use the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>

## <a name="remarks"></a><span data-ttu-id="94549-113">Notes</span><span class="sxs-lookup"><span data-stu-id="94549-113">Remarks</span></span>  
 <span data-ttu-id="94549-114">Les valeurs des paramètres `func` et `retvalRange` ne sont pas valides après le retour de la fonction `FunctionLeave2`, car les valeurs peuvent changer ou être détruites.</span><span class="sxs-lookup"><span data-stu-id="94549-114">The values of the `func` and `retvalRange` parameters are not valid after the `FunctionLeave2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="94549-115">La fonction `FunctionLeave2` est un rappel ; vous devez l’implémenter.</span><span class="sxs-lookup"><span data-stu-id="94549-115">The `FunctionLeave2` function is a callback; you must implement it.</span></span> <span data-ttu-id="94549-116">L’implémentation doit utiliser l’attribut de classe de stockage `__declspec`(`naked`).</span><span class="sxs-lookup"><span data-stu-id="94549-116">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="94549-117">Le moteur d’exécution n’enregistre aucun registre avant d’appeler cette fonction.</span><span class="sxs-lookup"><span data-stu-id="94549-117">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="94549-118">À l’entrée, vous devez enregistrer tous les registres que vous utilisez, y compris ceux de l’unité à virgule flottante (FPU).</span><span class="sxs-lookup"><span data-stu-id="94549-118">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="94549-119">À la sortie, vous devez restaurer la pile en dépilant tous les paramètres qui ont été envoyés par son appelant.</span><span class="sxs-lookup"><span data-stu-id="94549-119">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="94549-120">L’implémentation de `FunctionLeave2` ne doit pas être bloquée, car elle retardera garbage collection.</span><span class="sxs-lookup"><span data-stu-id="94549-120">The implementation of `FunctionLeave2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="94549-121">L’implémentation ne doit pas essayer un garbage collection, car la pile n’est peut-être pas dans un État garbage collection.</span><span class="sxs-lookup"><span data-stu-id="94549-121">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="94549-122">Si une garbage collection est tentée, le runtime se bloque jusqu’à ce que `FunctionLeave2` retourne.</span><span class="sxs-lookup"><span data-stu-id="94549-122">If a garbage collection is attempted, the runtime will block until `FunctionLeave2` returns.</span></span>  
  
 <span data-ttu-id="94549-123">En outre, la fonction `FunctionLeave2` ne doit pas appeler dans du code managé ou de quelque manière qu’elle génère une allocation de mémoire managée.</span><span class="sxs-lookup"><span data-stu-id="94549-123">Also, the `FunctionLeave2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94549-124">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="94549-124">Requirements</span></span>  
 <span data-ttu-id="94549-125">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94549-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94549-126">**En-tête :** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="94549-126">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="94549-127">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="94549-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="94549-128">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94549-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94549-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="94549-129">See also</span></span>

- [<span data-ttu-id="94549-130">FunctionEnter2, fonction</span><span class="sxs-lookup"><span data-stu-id="94549-130">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="94549-131">FunctionTailcall2, fonction</span><span class="sxs-lookup"><span data-stu-id="94549-131">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="94549-132">SetEnterLeaveFunctionHooks2, méthode</span><span class="sxs-lookup"><span data-stu-id="94549-132">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="94549-133">Fonctions statiques globales de profilage</span><span class="sxs-lookup"><span data-stu-id="94549-133">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
