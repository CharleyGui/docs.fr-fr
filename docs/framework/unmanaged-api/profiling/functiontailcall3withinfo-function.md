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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9cd301ac9d82dd49fc9680d2724714f267ed88ae
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763287"
---
# <a name="functiontailcall3withinfo-function"></a><span data-ttu-id="bcda4-102">FunctionTailcall3WithInfo, fonction</span><span class="sxs-lookup"><span data-stu-id="bcda4-102">FunctionTailcall3WithInfo Function</span></span>
<span data-ttu-id="bcda4-103">Informe le profileur que la fonction en cours d’exécution est sur le point d’effectuer un appel tail à une autre fonction et fournit un handle qui peut être passé à la [ICorProfilerInfo3::GetFunctionTailcall3Info, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) pour récupérer le frame de pile.</span><span class="sxs-lookup"><span data-stu-id="bcda4-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionTailcall3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) to retrieve the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcda4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bcda4-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionTailcall3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bcda4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bcda4-105">Parameters</span></span>  
 `functionIDOrClientID`  
 <span data-ttu-id="bcda4-106">[in] L’identificateur de la fonction en cours d’exécution qui doit faire un appel tail.</span><span class="sxs-lookup"><span data-stu-id="bcda4-106">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="bcda4-107">[in] Handle opaque qui représente des informations sur un frame de pile donné.</span><span class="sxs-lookup"><span data-stu-id="bcda4-107">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="bcda4-108">Ce handle est valide uniquement pendant le rappel auquel il est passé.</span><span class="sxs-lookup"><span data-stu-id="bcda4-108">This handle is valid only during the callback to which it is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bcda4-109">Notes</span><span class="sxs-lookup"><span data-stu-id="bcda4-109">Remarks</span></span>  
 <span data-ttu-id="bcda4-110">Le `FunctionTailcall3WithInfo` méthode de rappel notifie le profileur que les fonctions sont appelées et permet au profileur d’utiliser le [ICorProfilerInfo3::GetFunctionTailcall3Info, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) pour inspecter le frame de pile.</span><span class="sxs-lookup"><span data-stu-id="bcda4-110">The `FunctionTailcall3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionTailcall3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) to inspect the stack frame.</span></span> <span data-ttu-id="bcda4-111">Pour accéder aux informations de frame de pile, le `COR_PRF_ENABLE_FRAME_INFO` indicateur doit être défini.</span><span class="sxs-lookup"><span data-stu-id="bcda4-111">To access stack frame information, the `COR_PRF_ENABLE_FRAME_INFO` flag has to be set.</span></span> <span data-ttu-id="bcda4-112">Le profileur peut utiliser le [ICorProfilerInfo::SetEventMask, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) pour définir les indicateurs d’événement, puis utiliser le [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) pour inscrire votre implémentation de cette fonction.</span><span class="sxs-lookup"><span data-stu-id="bcda4-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="bcda4-113">Le `FunctionTailcall3WithInfo` fonction est un rappel ; vous devez l’implémenter.</span><span class="sxs-lookup"><span data-stu-id="bcda4-113">The `FunctionTailcall3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="bcda4-114">L’implémentation doit utiliser le `__declspec(naked)` attribut de classe de stockage.</span><span class="sxs-lookup"><span data-stu-id="bcda4-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="bcda4-115">Le moteur d’exécution n’enregistre pas les registres avant d’appeler cette fonction.</span><span class="sxs-lookup"><span data-stu-id="bcda4-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="bcda4-116">À l’entrée, vous devez enregistrer tous les registres que vous utilisez, y compris celles dans l’unité de virgule flottante (FPU).</span><span class="sxs-lookup"><span data-stu-id="bcda4-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="bcda4-117">À la sortie, vous devez restaurer la pile en dépilant tous les paramètres qui ont été envoyés par son appelant.</span><span class="sxs-lookup"><span data-stu-id="bcda4-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="bcda4-118">L’implémentation de `FunctionTailcall3WithInfo` ne doivent pas bloquer, car il sera retarder le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="bcda4-118">The implementation of `FunctionTailcall3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="bcda4-119">L’implémentation ne doit pas tenter un garbage collection, car la pile est peut-être pas dans un état de la collection convivial garbage.</span><span class="sxs-lookup"><span data-stu-id="bcda4-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="bcda4-120">Si un garbage collection est tenté, le runtime bloque jusqu'à ce que `FunctionTailcall3WithInfo` retourne.</span><span class="sxs-lookup"><span data-stu-id="bcda4-120">If a garbage collection is attempted, the runtime will block until `FunctionTailcall3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="bcda4-121">En outre, la fonction FunctionTailcall3WithInfo ne doit pas appeler dans du code managé ou provoquer une allocation de mémoire managée en aucune façon.</span><span class="sxs-lookup"><span data-stu-id="bcda4-121">Also, the FunctionTailcall3WithInfo function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bcda4-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="bcda4-122">Requirements</span></span>  
 <span data-ttu-id="bcda4-123">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bcda4-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bcda4-124">**En-tête :** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="bcda4-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="bcda4-125">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bcda4-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bcda4-126">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bcda4-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcda4-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bcda4-127">See also</span></span>

- [<span data-ttu-id="bcda4-128">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="bcda4-128">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="bcda4-129">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="bcda4-129">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="bcda4-130">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="bcda4-130">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="bcda4-131">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="bcda4-131">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="bcda4-132">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="bcda4-132">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="bcda4-133">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="bcda4-133">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="bcda4-134">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="bcda4-134">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="bcda4-135">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="bcda4-135">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="bcda4-136">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="bcda4-136">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="bcda4-137">Fonctions statiques globales de profilage</span><span class="sxs-lookup"><span data-stu-id="bcda4-137">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
