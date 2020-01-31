---
title: FunctionEnter2 (fonction)
ms.date: 03/30/2017
api_name:
- FunctionEnter2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter2
helpviewer_keywords:
- FunctionEnter2 function [.NET Framework profiling]
ms.assetid: ce7a21f9-0ca3-4b92-bc4b-bb803cae3f51
topic_type:
- apiref
ms.openlocfilehash: 6cd35c180b8a322b3402b050c6d6840073010b1f
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866981"
---
# <a name="functionenter2-function"></a><span data-ttu-id="ddb04-102">FunctionEnter2 (fonction)</span><span class="sxs-lookup"><span data-stu-id="ddb04-102">FunctionEnter2 Function</span></span>
<span data-ttu-id="ddb04-103">Notifie le profileur que le contrôle est passé à une fonction et fournit des informations sur le frame de pile et les arguments de fonction.</span><span class="sxs-lookup"><span data-stu-id="ddb04-103">Notifies the profiler that control is being passed to a function and provides information about the stack frame and function arguments.</span></span> <span data-ttu-id="ddb04-104">Cette fonction remplace la fonction [FunctionEnter](functionenter-function.md) .</span><span class="sxs-lookup"><span data-stu-id="ddb04-104">This function supersedes the [FunctionEnter](functionenter-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddb04-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ddb04-105">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter2 (  
    [in]  FunctionID                       funcId,   
    [in]  UINT_PTR                         clientData,   
    [in]  COR_PRF_FRAME_INFO               func,   
    [in]  COR_PRF_FUNCTION_ARGUMENT_INFO  *argumentInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ddb04-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="ddb04-106">Parameters</span></span>

- `funcId`

  <span data-ttu-id="ddb04-107">\[in] identificateur de la fonction vers laquelle le contrôle est passé.</span><span class="sxs-lookup"><span data-stu-id="ddb04-107">\[in] The identifier of the function to which control is passed.</span></span>

- `clientData`

  <span data-ttu-id="ddb04-108">\[dans] identificateur de fonction remappée, que le profileur a précédemment spécifié à l’aide de la fonction [FunctionIDMapper](functionidmapper-function.md) .</span><span class="sxs-lookup"><span data-stu-id="ddb04-108">\[in] The remapped function identifier, which the profiler previously specified by using the [FunctionIDMapper](functionidmapper-function.md) function.</span></span>
  
- `func`

  <span data-ttu-id="ddb04-109">\[dans] valeur `COR_PRF_FRAME_INFO` qui pointe vers les informations sur le frame de pile.</span><span class="sxs-lookup"><span data-stu-id="ddb04-109">\[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>
  
  <span data-ttu-id="ddb04-110">Le profileur doit traiter ceci comme un handle opaque qui peut être retourné au moteur d’exécution dans la méthode [ICorProfilerInfo2 :: GetFunctionInfo2,](icorprofilerinfo2-getfunctioninfo2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ddb04-110">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
- `argumentInfo`

  <span data-ttu-id="ddb04-111">\[in] pointeur vers une structure [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) qui spécifie les emplacements en mémoire des arguments de la fonction.</span><span class="sxs-lookup"><span data-stu-id="ddb04-111">\[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) structure that specifies the locations in memory of the function's arguments.</span></span>

  <span data-ttu-id="ddb04-112">Pour accéder aux informations d’argument, l’indicateur `COR_PRF_ENABLE_FUNCTION_ARGS` doit être défini.</span><span class="sxs-lookup"><span data-stu-id="ddb04-112">In order to access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag must be set.</span></span> <span data-ttu-id="ddb04-113">Le profileur peut utiliser la méthode [ICorProfilerInfo :: SetEventMask](icorprofilerinfo-seteventmask-method.md) pour définir les indicateurs d’événement.</span><span class="sxs-lookup"><span data-stu-id="ddb04-113">The profiler can use the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>

## <a name="remarks"></a><span data-ttu-id="ddb04-114">Notes</span><span class="sxs-lookup"><span data-stu-id="ddb04-114">Remarks</span></span>  
 <span data-ttu-id="ddb04-115">Les valeurs des paramètres `func` et `argumentInfo` ne sont pas valides après le retour de la fonction `FunctionEnter2`, car les valeurs peuvent changer ou être détruites.</span><span class="sxs-lookup"><span data-stu-id="ddb04-115">The values of the `func` and `argumentInfo` parameters are not valid after the `FunctionEnter2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="ddb04-116">La fonction `FunctionEnter2` est un rappel ; vous devez l’implémenter.</span><span class="sxs-lookup"><span data-stu-id="ddb04-116">The `FunctionEnter2` function is a callback; you must implement it.</span></span> <span data-ttu-id="ddb04-117">L’implémentation doit utiliser l’attribut de classe de stockage `__declspec`(`naked`).</span><span class="sxs-lookup"><span data-stu-id="ddb04-117">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="ddb04-118">Le moteur d’exécution n’enregistre aucun registre avant d’appeler cette fonction.</span><span class="sxs-lookup"><span data-stu-id="ddb04-118">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="ddb04-119">À l’entrée, vous devez enregistrer tous les registres que vous utilisez, y compris ceux de l’unité à virgule flottante (FPU).</span><span class="sxs-lookup"><span data-stu-id="ddb04-119">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="ddb04-120">À la sortie, vous devez restaurer la pile en dépilant tous les paramètres qui ont été envoyés par son appelant.</span><span class="sxs-lookup"><span data-stu-id="ddb04-120">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="ddb04-121">L’implémentation de `FunctionEnter2` ne doit pas être bloquée, car elle retardera garbage collection.</span><span class="sxs-lookup"><span data-stu-id="ddb04-121">The implementation of `FunctionEnter2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="ddb04-122">L’implémentation ne doit pas essayer un garbage collection, car la pile n’est peut-être pas dans un État garbage collection.</span><span class="sxs-lookup"><span data-stu-id="ddb04-122">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="ddb04-123">Si une garbage collection est tentée, le runtime se bloque jusqu’à ce que `FunctionEnter2` retourne.</span><span class="sxs-lookup"><span data-stu-id="ddb04-123">If a garbage collection is attempted, the runtime will block until `FunctionEnter2` returns.</span></span>  
  
 <span data-ttu-id="ddb04-124">En outre, la fonction `FunctionEnter2` ne doit pas appeler dans du code managé ou de quelque manière qu’elle génère une allocation de mémoire managée.</span><span class="sxs-lookup"><span data-stu-id="ddb04-124">Also, the `FunctionEnter2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ddb04-125">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="ddb04-125">Requirements</span></span>  
 <span data-ttu-id="ddb04-126">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ddb04-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ddb04-127">**En-tête :** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="ddb04-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="ddb04-128">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ddb04-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ddb04-129">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ddb04-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddb04-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ddb04-130">See also</span></span>

- [<span data-ttu-id="ddb04-131">FunctionLeave2, fonction</span><span class="sxs-lookup"><span data-stu-id="ddb04-131">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="ddb04-132">FunctionTailcall2, fonction</span><span class="sxs-lookup"><span data-stu-id="ddb04-132">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="ddb04-133">SetEnterLeaveFunctionHooks2, méthode</span><span class="sxs-lookup"><span data-stu-id="ddb04-133">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="ddb04-134">Fonctions statiques globales de profilage</span><span class="sxs-lookup"><span data-stu-id="ddb04-134">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
