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
ms.openlocfilehash: dfe1a530ea009300e7cfbf002053d2e2b6034845
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719279"
---
# <a name="functiontailcall3-function"></a><span data-ttu-id="293be-102">FunctionTailcall3, fonction</span><span class="sxs-lookup"><span data-stu-id="293be-102">FunctionTailcall3 Function</span></span>

<span data-ttu-id="293be-103">Indique au profileur que la fonction en cours d’exécution est sur le paragraphe d’effectuer un appel tail à une autre fonction.</span><span class="sxs-lookup"><span data-stu-id="293be-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="293be-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="293be-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionTailcall3 (FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="293be-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="293be-105">Parameters</span></span>

- `functionOrRemappedID`

  <span data-ttu-id="293be-106">\[in] identificateur de la fonction en cours d’exécution qui est sur le paragraphe d’effectuer un appel tail.</span><span class="sxs-lookup"><span data-stu-id="293be-106">\[in] The identifier of the currently executing function that is about to make a tail call.</span></span>

## <a name="remarks"></a><span data-ttu-id="293be-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="293be-107">Remarks</span></span>  

 <span data-ttu-id="293be-108">La `FunctionTailcall3` fonction de rappel indique au profileur que les fonctions sont appelées.</span><span class="sxs-lookup"><span data-stu-id="293be-108">The `FunctionTailcall3` callback function notifies the profiler as functions are being called.</span></span> <span data-ttu-id="293be-109">Utilisez la [méthode ICorProfilerInfo3 :: SetEnterLeaveFunctionHooks3,](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) pour inscrire votre implémentation de cette fonction.</span><span class="sxs-lookup"><span data-stu-id="293be-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="293be-110">La `FunctionTailcall3` fonction est un rappel ; vous devez l’implémenter.</span><span class="sxs-lookup"><span data-stu-id="293be-110">The `FunctionTailcall3` function is a callback; you must implement it.</span></span> <span data-ttu-id="293be-111">L’implémentation doit utiliser l' `__declspec(naked)` attribut de classe de stockage.</span><span class="sxs-lookup"><span data-stu-id="293be-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="293be-112">Le moteur d’exécution n’enregistre aucun registre avant d’appeler cette fonction.</span><span class="sxs-lookup"><span data-stu-id="293be-112">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="293be-113">À l’entrée, vous devez enregistrer tous les registres que vous utilisez, y compris ceux de l’unité à virgule flottante (FPU).</span><span class="sxs-lookup"><span data-stu-id="293be-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="293be-114">À la sortie, vous devez restaurer la pile en dépilant tous les paramètres qui ont été envoyés par son appelant.</span><span class="sxs-lookup"><span data-stu-id="293be-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="293be-115">L’implémentation de ne `FunctionTailcall3` doit pas se bloquer, car elle retardera garbage collection.</span><span class="sxs-lookup"><span data-stu-id="293be-115">The implementation of `FunctionTailcall3` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="293be-116">L’implémentation ne doit pas essayer un garbage collection, car la pile n’est peut-être pas dans un État garbage collection.</span><span class="sxs-lookup"><span data-stu-id="293be-116">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="293be-117">Si une garbage collection est tentée, le runtime se bloque jusqu’à ce que `FunctionTailcall3` retourne la valeur.</span><span class="sxs-lookup"><span data-stu-id="293be-117">If a garbage collection is attempted, the runtime will block until `FunctionTailcall3` returns.</span></span>  
  
 <span data-ttu-id="293be-118">La `FunctionTailcall3` fonction ne doit pas appeler dans du code managé ou provoquer une allocation de mémoire managée de quelque manière que ce soit.</span><span class="sxs-lookup"><span data-stu-id="293be-118">The `FunctionTailcall3` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="293be-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="293be-119">Requirements</span></span>  

 <span data-ttu-id="293be-120">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="293be-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="293be-121">**En-tête :** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="293be-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="293be-122">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="293be-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="293be-123">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="293be-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="293be-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="293be-124">See also</span></span>

- [<span data-ttu-id="293be-125">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="293be-125">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="293be-126">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="293be-126">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="293be-127">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="293be-127">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="293be-128">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="293be-128">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="293be-129">FunctionTailcall3WithInfo, fonction</span><span class="sxs-lookup"><span data-stu-id="293be-129">FunctionTailcall3WithInfo Function</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="293be-130">Setenterleavefunctionhooks3,</span><span class="sxs-lookup"><span data-stu-id="293be-130">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="293be-131">Setenterleavefunctionhooks3withinfo,</span><span class="sxs-lookup"><span data-stu-id="293be-131">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="293be-132">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="293be-132">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="293be-133">Setfunctionidmapper2,</span><span class="sxs-lookup"><span data-stu-id="293be-133">SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="293be-134">Fonctions statiques globales du profilage</span><span class="sxs-lookup"><span data-stu-id="293be-134">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
