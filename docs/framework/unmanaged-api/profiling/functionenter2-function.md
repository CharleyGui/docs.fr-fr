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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 413cde3d0977c1fd6897fc5bd6fa7a3fef00ac02
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763337"
---
# <a name="functionenter2-function"></a><span data-ttu-id="a8a2f-102">FunctionEnter2 (fonction)</span><span class="sxs-lookup"><span data-stu-id="a8a2f-102">FunctionEnter2 Function</span></span>
<span data-ttu-id="a8a2f-103">Notifie le profileur que le contrôle est passé à une fonction et fournit des informations sur la pile des arguments de fonction et de frame.</span><span class="sxs-lookup"><span data-stu-id="a8a2f-103">Notifies the profiler that control is being passed to a function and provides information about the stack frame and function arguments.</span></span> <span data-ttu-id="a8a2f-104">Cette fonction remplace la [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) (fonction).</span><span class="sxs-lookup"><span data-stu-id="a8a2f-104">This function supersedes the [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8a2f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a8a2f-105">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter2 (  
    [in]  FunctionID                       funcId,   
    [in]  UINT_PTR                         clientData,   
    [in]  COR_PRF_FRAME_INFO               func,   
    [in]  COR_PRF_FUNCTION_ARGUMENT_INFO  *argumentInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8a2f-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a8a2f-106">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="a8a2f-107">[in] L’identificateur de la fonction à laquelle le contrôle est passé.</span><span class="sxs-lookup"><span data-stu-id="a8a2f-107">[in] The identifier of the function to which control is passed.</span></span>  
  
 `clientData`  
 <span data-ttu-id="a8a2f-108">[in] Identificateur de fonction remappée, avec le profileur spécifié précédemment à l’aide de la [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) (fonction).</span><span class="sxs-lookup"><span data-stu-id="a8a2f-108">[in] The remapped function identifier, which the profiler previously specified by using the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) function.</span></span>  
  
 `func`  
 <span data-ttu-id="a8a2f-109">[in] Un `COR_PRF_FRAME_INFO` valeur qui pointe vers des informations sur le frame de pile.</span><span class="sxs-lookup"><span data-stu-id="a8a2f-109">[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>  
  
 <span data-ttu-id="a8a2f-110">Le profileur doit traiter ceci comme un handle opaque qui peut être passé au moteur d’exécution dans le [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="a8a2f-110">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
 `argumentInfo`  
 <span data-ttu-id="a8a2f-111">[in] Un pointeur vers un [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) structure qui spécifie les emplacements en mémoire des arguments de fonction.</span><span class="sxs-lookup"><span data-stu-id="a8a2f-111">[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) structure that specifies the locations in memory of the function's arguments.</span></span>  
  
 <span data-ttu-id="a8a2f-112">Pour accéder aux informations d’argument, la `COR_PRF_ENABLE_FUNCTION_ARGS` l’indicateur doit être défini.</span><span class="sxs-lookup"><span data-stu-id="a8a2f-112">In order to access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag must be set.</span></span> <span data-ttu-id="a8a2f-113">Le profileur peut utiliser le [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) méthode pour définir les indicateurs d’événement.</span><span class="sxs-lookup"><span data-stu-id="a8a2f-113">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8a2f-114">Notes</span><span class="sxs-lookup"><span data-stu-id="a8a2f-114">Remarks</span></span>  
 <span data-ttu-id="a8a2f-115">Les valeurs de la `func` et `argumentInfo` paramètres ne sont pas valides après la `FunctionEnter2` fonction retourne, car les valeurs peuvent changer ou être détruites.</span><span class="sxs-lookup"><span data-stu-id="a8a2f-115">The values of the `func` and `argumentInfo` parameters are not valid after the `FunctionEnter2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="a8a2f-116">Le `FunctionEnter2` fonction est un rappel ; vous devez l’implémenter.</span><span class="sxs-lookup"><span data-stu-id="a8a2f-116">The `FunctionEnter2` function is a callback; you must implement it.</span></span> <span data-ttu-id="a8a2f-117">L’implémentation doit utiliser le `__declspec`(`naked`) attribut de classe de stockage.</span><span class="sxs-lookup"><span data-stu-id="a8a2f-117">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="a8a2f-118">Le moteur d’exécution n’enregistre pas les registres avant d’appeler cette fonction.</span><span class="sxs-lookup"><span data-stu-id="a8a2f-118">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="a8a2f-119">À l’entrée, vous devez enregistrer tous les registres que vous utilisez, y compris celles dans l’unité de virgule flottante (FPU).</span><span class="sxs-lookup"><span data-stu-id="a8a2f-119">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="a8a2f-120">À la sortie, vous devez restaurer la pile en dépilant tous les paramètres qui ont été envoyés par son appelant.</span><span class="sxs-lookup"><span data-stu-id="a8a2f-120">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="a8a2f-121">L’implémentation de `FunctionEnter2` ne doivent pas bloquer, car il sera retarder le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="a8a2f-121">The implementation of `FunctionEnter2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="a8a2f-122">L’implémentation ne doit pas tenter un garbage collection, car la pile est peut-être pas à l’état garbage collection convivial.</span><span class="sxs-lookup"><span data-stu-id="a8a2f-122">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="a8a2f-123">Si un garbage collection est tenté, le runtime bloque jusqu'à ce que `FunctionEnter2` retourne.</span><span class="sxs-lookup"><span data-stu-id="a8a2f-123">If a garbage collection is attempted, the runtime will block until `FunctionEnter2` returns.</span></span>  
  
 <span data-ttu-id="a8a2f-124">En outre, le `FunctionEnter2` (fonction) ne doit pas appeler dans du code managé ou de quelque manière qu’une allocation de mémoire managée.</span><span class="sxs-lookup"><span data-stu-id="a8a2f-124">Also, the `FunctionEnter2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8a2f-125">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a8a2f-125">Requirements</span></span>  
 <span data-ttu-id="a8a2f-126">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8a2f-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8a2f-127">**En-tête :** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="a8a2f-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="a8a2f-128">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a8a2f-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8a2f-129">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8a2f-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8a2f-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a8a2f-130">See also</span></span>

- [<span data-ttu-id="a8a2f-131">FunctionLeave2, fonction</span><span class="sxs-lookup"><span data-stu-id="a8a2f-131">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [<span data-ttu-id="a8a2f-132">FunctionTailcall2, fonction</span><span class="sxs-lookup"><span data-stu-id="a8a2f-132">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [<span data-ttu-id="a8a2f-133">SetEnterLeaveFunctionHooks2, méthode</span><span class="sxs-lookup"><span data-stu-id="a8a2f-133">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="a8a2f-134">Fonctions statiques globales de profilage</span><span class="sxs-lookup"><span data-stu-id="a8a2f-134">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
