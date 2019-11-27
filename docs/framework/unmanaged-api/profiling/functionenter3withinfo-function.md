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
ms.openlocfilehash: 86b1c8b3f5bd88b216c59f5cc6846f83f3c094ee
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440754"
---
# <a name="functionenter3withinfo-function"></a><span data-ttu-id="6bbb5-102">FunctionEnter3WithInfo, fonction</span><span class="sxs-lookup"><span data-stu-id="6bbb5-102">FunctionEnter3WithInfo Function</span></span>
<span data-ttu-id="6bbb5-103">Notifie le profileur que le contrôle est passé à une fonction et fournit un handle qui peut être passé à la [méthode ICorProfilerInfo3 :: GetFunctionEnter3Info,](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) pour récupérer le frame de pile et les arguments de fonction.</span><span class="sxs-lookup"><span data-stu-id="6bbb5-103">Notifies the profiler that control is being passed to a function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionEnter3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) to retrieve the stack frame and function arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bbb5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6bbb5-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6bbb5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6bbb5-105">Parameters</span></span>  
 `functionIDOrClientID`  
 <span data-ttu-id="6bbb5-106">dans Identificateur de la fonction à laquelle le contrôle est passé.</span><span class="sxs-lookup"><span data-stu-id="6bbb5-106">[in] The identifier of the function to which control is passed.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="6bbb5-107">[in] Handle opaque qui représente des informations sur un frame de pile donné.</span><span class="sxs-lookup"><span data-stu-id="6bbb5-107">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="6bbb5-108">Ce handle est valide uniquement pendant le rappel auquel il est passé.</span><span class="sxs-lookup"><span data-stu-id="6bbb5-108">This handle is valid only during the callback to which it is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6bbb5-109">Notes</span><span class="sxs-lookup"><span data-stu-id="6bbb5-109">Remarks</span></span>  
 <span data-ttu-id="6bbb5-110">La méthode de rappel `FunctionEnter3WithInfo` informe le profileur que les fonctions sont appelées et permet au profileur d’utiliser la [méthode ICorProfilerInfo3 :: GetFunctionEnter3Info,](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) pour inspecter les valeurs des arguments.</span><span class="sxs-lookup"><span data-stu-id="6bbb5-110">The `FunctionEnter3WithInfo` callback method notifies the profiler as functions are called, and enables the profiler to use the [ICorProfilerInfo3::GetFunctionEnter3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) to inspect argument values.</span></span> <span data-ttu-id="6bbb5-111">Pour accéder aux informations d’argument, l’indicateur de `COR_PRF_ENABLE_FUNCTION_ARGS` doit être défini.</span><span class="sxs-lookup"><span data-stu-id="6bbb5-111">To access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag has to be set.</span></span> <span data-ttu-id="6bbb5-112">Le profileur peut utiliser la [méthode ICorProfilerInfo :: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) pour définir les indicateurs d’événement, puis utiliser la [méthode ICorProfilerInfo3 :: SetEnterLeaveFunctionHooks3WithInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) pour inscrire votre implémentation de cette fonction.</span><span class="sxs-lookup"><span data-stu-id="6bbb5-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="6bbb5-113">La fonction `FunctionEnter3WithInfo` est un rappel ; vous devez l’implémenter.</span><span class="sxs-lookup"><span data-stu-id="6bbb5-113">The `FunctionEnter3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="6bbb5-114">L’implémentation doit utiliser l’attribut de classe de stockage `__declspec(naked)`.</span><span class="sxs-lookup"><span data-stu-id="6bbb5-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="6bbb5-115">Le moteur d’exécution n’enregistre aucun registre avant d’appeler cette fonction.</span><span class="sxs-lookup"><span data-stu-id="6bbb5-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="6bbb5-116">À l’entrée, vous devez enregistrer tous les registres que vous utilisez, y compris ceux de l’unité à virgule flottante (FPU).</span><span class="sxs-lookup"><span data-stu-id="6bbb5-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="6bbb5-117">À la sortie, vous devez restaurer la pile en dépilant tous les paramètres qui ont été envoyés par son appelant.</span><span class="sxs-lookup"><span data-stu-id="6bbb5-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="6bbb5-118">L’implémentation de `FunctionEnter3WithInfo` ne doit pas être bloquée, car elle retardera garbage collection.</span><span class="sxs-lookup"><span data-stu-id="6bbb5-118">The implementation of `FunctionEnter3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="6bbb5-119">L’implémentation ne doit pas essayer un garbage collection, car la pile n’est peut-être pas dans un État garbage collection.</span><span class="sxs-lookup"><span data-stu-id="6bbb5-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="6bbb5-120">Si une garbage collection est tentée, le runtime se bloque jusqu’à ce que `FunctionEnter3WithInfo` retourne.</span><span class="sxs-lookup"><span data-stu-id="6bbb5-120">If a garbage collection is attempted, the runtime will block until `FunctionEnter3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="6bbb5-121">La fonction `FunctionEnter3WithInfo` ne doit pas appeler dans du code managé ou provoquer une allocation de mémoire managée de quelque manière que ce soit.</span><span class="sxs-lookup"><span data-stu-id="6bbb5-121">The `FunctionEnter3WithInfo` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bbb5-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6bbb5-122">Requirements</span></span>  
 <span data-ttu-id="6bbb5-123">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6bbb5-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bbb5-124">**En-tête :** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="6bbb5-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="6bbb5-125">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6bbb5-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6bbb5-126">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bbb5-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bbb5-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6bbb5-127">See also</span></span>

- [<span data-ttu-id="6bbb5-128">Getfunctionenter3info,</span><span class="sxs-lookup"><span data-stu-id="6bbb5-128">GetFunctionEnter3Info</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md)
- [<span data-ttu-id="6bbb5-129">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="6bbb5-129">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="6bbb5-130">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="6bbb5-130">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="6bbb5-131">Fonctions statiques globales de profilage</span><span class="sxs-lookup"><span data-stu-id="6bbb5-131">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
