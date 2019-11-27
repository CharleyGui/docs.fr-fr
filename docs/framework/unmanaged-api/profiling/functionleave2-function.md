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
ms.openlocfilehash: e40687f7f843dc563801bb01b503d2ae94a094fc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446018"
---
# <a name="functionleave2-function"></a><span data-ttu-id="b581a-102">FunctionLeave2 (fonction)</span><span class="sxs-lookup"><span data-stu-id="b581a-102">FunctionLeave2 Function</span></span>
<span data-ttu-id="b581a-103">Notifie le profileur qu’une fonction va retourner à l’appelant et fournit des informations sur le frame de pile et la valeur de retour de fonction.</span><span class="sxs-lookup"><span data-stu-id="b581a-103">Notifies the profiler that a function is about to return to the caller and provides information about the stack frame and function return value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b581a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b581a-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave2 (  
    [in]  FunctionID                        funcId,  
    [in]  UINT_PTR                          clientData,  
    [in]  COR_PRF_FRAME_INFO                func,  
    [in]  COR_PRF_FUNCTION_ARGUMENT_RANGE  *retvalRange  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b581a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b581a-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="b581a-106">dans Identificateur de la fonction qui retourne.</span><span class="sxs-lookup"><span data-stu-id="b581a-106">[in] The identifier of the function that is returning.</span></span>  
  
 `clientData`  
 <span data-ttu-id="b581a-107">dans Identificateur de fonction remappée, que le profileur a précédemment spécifié via la fonction [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) .</span><span class="sxs-lookup"><span data-stu-id="b581a-107">[in] The remapped function identifier, which the profiler previously specified via the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) function.</span></span>  
  
 `func`  
 <span data-ttu-id="b581a-108">dans Valeur `COR_PRF_FRAME_INFO` qui pointe vers les informations sur le frame de pile.</span><span class="sxs-lookup"><span data-stu-id="b581a-108">[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>  
  
 <span data-ttu-id="b581a-109">Le profileur doit traiter ceci comme un handle opaque qui peut être retourné au moteur d’exécution dans la méthode [ICorProfilerInfo2 :: GetFunctionInfo2,](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b581a-109">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
 `retvalRange`  
 <span data-ttu-id="b581a-110">dans Pointeur vers une structure [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) qui spécifie l’emplacement de la mémoire de la valeur de retour de la fonction.</span><span class="sxs-lookup"><span data-stu-id="b581a-110">[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structure that specifies the memory location of the function's return value.</span></span>  
  
 <span data-ttu-id="b581a-111">Pour accéder aux informations de valeur de retour, l’indicateur `COR_PRF_ENABLE_FUNCTION_RETVAL` doit être défini.</span><span class="sxs-lookup"><span data-stu-id="b581a-111">In order to access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span></span> <span data-ttu-id="b581a-112">Le profileur peut utiliser la méthode [ICorProfilerInfo :: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) pour définir les indicateurs d’événement.</span><span class="sxs-lookup"><span data-stu-id="b581a-112">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b581a-113">Notes</span><span class="sxs-lookup"><span data-stu-id="b581a-113">Remarks</span></span>  
 <span data-ttu-id="b581a-114">Les valeurs des paramètres `func` et `retvalRange` ne sont pas valides après le retour de la fonction `FunctionLeave2`, car les valeurs peuvent changer ou être détruites.</span><span class="sxs-lookup"><span data-stu-id="b581a-114">The values of the `func` and `retvalRange` parameters are not valid after the `FunctionLeave2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="b581a-115">La fonction `FunctionLeave2` est un rappel ; vous devez l’implémenter.</span><span class="sxs-lookup"><span data-stu-id="b581a-115">The `FunctionLeave2` function is a callback; you must implement it.</span></span> <span data-ttu-id="b581a-116">L’implémentation doit utiliser l’attribut de classe de stockage `__declspec`(`naked`).</span><span class="sxs-lookup"><span data-stu-id="b581a-116">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="b581a-117">Le moteur d’exécution n’enregistre aucun registre avant d’appeler cette fonction.</span><span class="sxs-lookup"><span data-stu-id="b581a-117">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="b581a-118">À l’entrée, vous devez enregistrer tous les registres que vous utilisez, y compris ceux de l’unité à virgule flottante (FPU).</span><span class="sxs-lookup"><span data-stu-id="b581a-118">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="b581a-119">À la sortie, vous devez restaurer la pile en dépilant tous les paramètres qui ont été envoyés par son appelant.</span><span class="sxs-lookup"><span data-stu-id="b581a-119">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="b581a-120">L’implémentation de `FunctionLeave2` ne doit pas être bloquée, car elle retardera garbage collection.</span><span class="sxs-lookup"><span data-stu-id="b581a-120">The implementation of `FunctionLeave2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="b581a-121">L’implémentation ne doit pas essayer un garbage collection, car la pile n’est peut-être pas dans un État garbage collection.</span><span class="sxs-lookup"><span data-stu-id="b581a-121">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="b581a-122">Si une garbage collection est tentée, le runtime se bloque jusqu’à ce que `FunctionLeave2` retourne.</span><span class="sxs-lookup"><span data-stu-id="b581a-122">If a garbage collection is attempted, the runtime will block until `FunctionLeave2` returns.</span></span>  
  
 <span data-ttu-id="b581a-123">En outre, la fonction `FunctionLeave2` ne doit pas appeler dans du code managé ou de quelque manière qu’elle génère une allocation de mémoire managée.</span><span class="sxs-lookup"><span data-stu-id="b581a-123">Also, the `FunctionLeave2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b581a-124">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b581a-124">Requirements</span></span>  
 <span data-ttu-id="b581a-125">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b581a-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b581a-126">**En-tête :** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="b581a-126">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="b581a-127">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b581a-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b581a-128">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b581a-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b581a-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b581a-129">See also</span></span>

- [<span data-ttu-id="b581a-130">FunctionEnter2, fonction</span><span class="sxs-lookup"><span data-stu-id="b581a-130">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="b581a-131">FunctionTailcall2, fonction</span><span class="sxs-lookup"><span data-stu-id="b581a-131">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [<span data-ttu-id="b581a-132">SetEnterLeaveFunctionHooks2, méthode</span><span class="sxs-lookup"><span data-stu-id="b581a-132">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="b581a-133">Fonctions statiques globales de profilage</span><span class="sxs-lookup"><span data-stu-id="b581a-133">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
