---
title: FunctionTailcall3, fonction
ms.date: 03/30/2017
api_name:
- FunctionTailcall3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall3
helpviewer_keywords:
- FunctionTailcall3 function [.NET Framework profiling]
ms.assetid: 1e48243f-5de6-4bd6-a1d0-e1d248bca4b8
topic_type:
- apiref
ms.openlocfilehash: 8d7c226d26d677a8b10df29e0343b71682c46699
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427372"
---
# <a name="functiontailcall3-function"></a><span data-ttu-id="a6beb-102">FunctionTailcall3, fonction</span><span class="sxs-lookup"><span data-stu-id="a6beb-102">FunctionTailcall3 Function</span></span>
<span data-ttu-id="a6beb-103">Indique au profileur que la fonction en cours d’exécution est sur le paragraphe d’effectuer un appel tail à une autre fonction.</span><span class="sxs-lookup"><span data-stu-id="a6beb-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6beb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a6beb-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionTailcall3 (FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6beb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a6beb-105">Parameters</span></span>  
 `functionOrRemappedID`  
 <span data-ttu-id="a6beb-106">dans Identificateur de la fonction en cours d’exécution qui va effectuer un appel tail.</span><span class="sxs-lookup"><span data-stu-id="a6beb-106">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6beb-107">Notes</span><span class="sxs-lookup"><span data-stu-id="a6beb-107">Remarks</span></span>  
 <span data-ttu-id="a6beb-108">La fonction de rappel `FunctionTailcall3` notifie le profileur lorsque des fonctions sont appelées.</span><span class="sxs-lookup"><span data-stu-id="a6beb-108">The `FunctionTailcall3` callback function notifies the profiler as functions are being called.</span></span> <span data-ttu-id="a6beb-109">Utilisez la [méthode ICorProfilerInfo3 :: SetEnterLeaveFunctionHooks3,](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) pour inscrire votre implémentation de cette fonction.</span><span class="sxs-lookup"><span data-stu-id="a6beb-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="a6beb-110">La fonction `FunctionTailcall3` est un rappel ; vous devez l’implémenter.</span><span class="sxs-lookup"><span data-stu-id="a6beb-110">The `FunctionTailcall3` function is a callback; you must implement it.</span></span> <span data-ttu-id="a6beb-111">L’implémentation doit utiliser l’attribut de classe de stockage `__declspec(naked)`.</span><span class="sxs-lookup"><span data-stu-id="a6beb-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="a6beb-112">Le moteur d’exécution n’enregistre aucun registre avant d’appeler cette fonction.</span><span class="sxs-lookup"><span data-stu-id="a6beb-112">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="a6beb-113">À l’entrée, vous devez enregistrer tous les registres que vous utilisez, y compris ceux de l’unité à virgule flottante (FPU).</span><span class="sxs-lookup"><span data-stu-id="a6beb-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="a6beb-114">À la sortie, vous devez restaurer la pile en dépilant tous les paramètres qui ont été envoyés par son appelant.</span><span class="sxs-lookup"><span data-stu-id="a6beb-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="a6beb-115">L’implémentation de `FunctionTailcall3` ne doit pas être bloquée, car elle retardera garbage collection.</span><span class="sxs-lookup"><span data-stu-id="a6beb-115">The implementation of `FunctionTailcall3` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="a6beb-116">L’implémentation ne doit pas essayer un garbage collection, car la pile n’est peut-être pas dans un État garbage collection.</span><span class="sxs-lookup"><span data-stu-id="a6beb-116">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="a6beb-117">Si une garbage collection est tentée, le runtime se bloque jusqu’à ce que `FunctionTailcall3` retourne.</span><span class="sxs-lookup"><span data-stu-id="a6beb-117">If a garbage collection is attempted, the runtime will block until `FunctionTailcall3` returns.</span></span>  
  
 <span data-ttu-id="a6beb-118">La fonction `FunctionTailcall3` ne doit pas appeler dans du code managé ou provoquer une allocation de mémoire managée de quelque manière que ce soit.</span><span class="sxs-lookup"><span data-stu-id="a6beb-118">The `FunctionTailcall3` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6beb-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a6beb-119">Requirements</span></span>  
 <span data-ttu-id="a6beb-120">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6beb-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6beb-121">**En-tête :** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="a6beb-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="a6beb-122">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a6beb-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6beb-123">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6beb-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6beb-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6beb-124">See also</span></span>

- [<span data-ttu-id="a6beb-125">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="a6beb-125">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="a6beb-126">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="a6beb-126">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="a6beb-127">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="a6beb-127">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="a6beb-128">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="a6beb-128">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="a6beb-129">FunctionTailcall3WithInfo, fonction</span><span class="sxs-lookup"><span data-stu-id="a6beb-129">FunctionTailcall3WithInfo Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="a6beb-130">Setenterleavefunctionhooks3,</span><span class="sxs-lookup"><span data-stu-id="a6beb-130">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="a6beb-131">Setenterleavefunctionhooks3withinfo,</span><span class="sxs-lookup"><span data-stu-id="a6beb-131">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="a6beb-132">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="a6beb-132">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="a6beb-133">Setfunctionidmapper2,</span><span class="sxs-lookup"><span data-stu-id="a6beb-133">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="a6beb-134">Fonctions statiques globales de profilage</span><span class="sxs-lookup"><span data-stu-id="a6beb-134">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
