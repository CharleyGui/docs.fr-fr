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
ms.openlocfilehash: 3bedb2c5f55f608b1153272437c0f55b730c2dfc
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866854"
---
# <a name="functiontailcall3-function"></a><span data-ttu-id="f1bbe-102">FunctionTailcall3, fonction</span><span class="sxs-lookup"><span data-stu-id="f1bbe-102">FunctionTailcall3 Function</span></span>
<span data-ttu-id="f1bbe-103">Indique au profileur que la fonction en cours d’exécution est sur le paragraphe d’effectuer un appel tail à une autre fonction.</span><span class="sxs-lookup"><span data-stu-id="f1bbe-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1bbe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f1bbe-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionTailcall3 (FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1bbe-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="f1bbe-105">Parameters</span></span>

- `functionOrRemappedID`

  <span data-ttu-id="f1bbe-106">\[in] identificateur de la fonction en cours d’exécution qui est sur le paragraphe d’effectuer un appel tail.</span><span class="sxs-lookup"><span data-stu-id="f1bbe-106">\[in] The identifier of the currently executing function that is about to make a tail call.</span></span>

## <a name="remarks"></a><span data-ttu-id="f1bbe-107">Notes</span><span class="sxs-lookup"><span data-stu-id="f1bbe-107">Remarks</span></span>  
 <span data-ttu-id="f1bbe-108">La fonction de rappel `FunctionTailcall3` notifie le profileur lorsque des fonctions sont appelées.</span><span class="sxs-lookup"><span data-stu-id="f1bbe-108">The `FunctionTailcall3` callback function notifies the profiler as functions are being called.</span></span> <span data-ttu-id="f1bbe-109">Utilisez la [méthode ICorProfilerInfo3 :: SetEnterLeaveFunctionHooks3,](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) pour inscrire votre implémentation de cette fonction.</span><span class="sxs-lookup"><span data-stu-id="f1bbe-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="f1bbe-110">La fonction `FunctionTailcall3` est un rappel ; vous devez l’implémenter.</span><span class="sxs-lookup"><span data-stu-id="f1bbe-110">The `FunctionTailcall3` function is a callback; you must implement it.</span></span> <span data-ttu-id="f1bbe-111">L’implémentation doit utiliser l’attribut de classe de stockage `__declspec(naked)`.</span><span class="sxs-lookup"><span data-stu-id="f1bbe-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="f1bbe-112">Le moteur d’exécution n’enregistre aucun registre avant d’appeler cette fonction.</span><span class="sxs-lookup"><span data-stu-id="f1bbe-112">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="f1bbe-113">À l’entrée, vous devez enregistrer tous les registres que vous utilisez, y compris ceux de l’unité à virgule flottante (FPU).</span><span class="sxs-lookup"><span data-stu-id="f1bbe-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="f1bbe-114">À la sortie, vous devez restaurer la pile en dépilant tous les paramètres qui ont été envoyés par son appelant.</span><span class="sxs-lookup"><span data-stu-id="f1bbe-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="f1bbe-115">L’implémentation de `FunctionTailcall3` ne doit pas être bloquée, car elle retardera garbage collection.</span><span class="sxs-lookup"><span data-stu-id="f1bbe-115">The implementation of `FunctionTailcall3` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="f1bbe-116">L’implémentation ne doit pas essayer un garbage collection, car la pile n’est peut-être pas dans un État garbage collection.</span><span class="sxs-lookup"><span data-stu-id="f1bbe-116">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="f1bbe-117">Si une garbage collection est tentée, le runtime se bloque jusqu’à ce que `FunctionTailcall3` retourne.</span><span class="sxs-lookup"><span data-stu-id="f1bbe-117">If a garbage collection is attempted, the runtime will block until `FunctionTailcall3` returns.</span></span>  
  
 <span data-ttu-id="f1bbe-118">La fonction `FunctionTailcall3` ne doit pas appeler dans du code managé ou provoquer une allocation de mémoire managée de quelque manière que ce soit.</span><span class="sxs-lookup"><span data-stu-id="f1bbe-118">The `FunctionTailcall3` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1bbe-119">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="f1bbe-119">Requirements</span></span>  
 <span data-ttu-id="f1bbe-120">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1bbe-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1bbe-121">**En-tête :** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="f1bbe-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="f1bbe-122">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f1bbe-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1bbe-123">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1bbe-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1bbe-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f1bbe-124">See also</span></span>

- [<span data-ttu-id="f1bbe-125">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="f1bbe-125">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="f1bbe-126">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="f1bbe-126">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="f1bbe-127">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="f1bbe-127">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="f1bbe-128">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="f1bbe-128">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="f1bbe-129">FunctionTailcall3WithInfo, fonction</span><span class="sxs-lookup"><span data-stu-id="f1bbe-129">FunctionTailcall3WithInfo Function</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="f1bbe-130">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="f1bbe-130">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="f1bbe-131">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="f1bbe-131">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="f1bbe-132">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="f1bbe-132">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="f1bbe-133">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="f1bbe-133">SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="f1bbe-134">Fonctions statiques globales de profilage</span><span class="sxs-lookup"><span data-stu-id="f1bbe-134">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
