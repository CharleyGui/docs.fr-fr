---
title: FunctionTailcall2 (fonction)
ms.date: 03/30/2017
api_name:
- FunctionTailcall2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall2
helpviewer_keywords:
- FunctionTailcall2 function [.NET Framework profiling]
ms.assetid: 249f9892-b5a9-41e1-b329-28a925904df6
topic_type:
- apiref
ms.openlocfilehash: e1cd3ef78d303aaa325699e1bcdec95f077fef21
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703978"
---
# <a name="functiontailcall2-function"></a><span data-ttu-id="bd286-102">FunctionTailcall2 (fonction)</span><span class="sxs-lookup"><span data-stu-id="bd286-102">FunctionTailcall2 Function</span></span>

<span data-ttu-id="bd286-103">Indique au profileur que la fonction en cours d’exécution est sur le paragraphe d’effectuer un appel tail à une autre fonction et fournit des informations sur le frame de pile.</span><span class="sxs-lookup"><span data-stu-id="bd286-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function and provides information about the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd286-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bd286-104">Syntax</span></span>  
  
```cpp
void __stdcall FunctionTailcall2 (  
    [in] FunctionID         funcId,
    [in] UINT_PTR           clientData,
    [in] COR_PRF_FRAME_INFO func  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd286-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bd286-105">Parameters</span></span>

- `funcId`

  <span data-ttu-id="bd286-106">\[in] identificateur de la fonction en cours d’exécution qui est sur le paragraphe d’effectuer un appel tail.</span><span class="sxs-lookup"><span data-stu-id="bd286-106">\[in] The identifier of the currently executing function that is about to make a tail call.</span></span>

- `clientData`

  <span data-ttu-id="bd286-107">\[dans] identificateur de fonction remappée, que le profileur a précédemment spécifié via le [FunctionIDMapper](functionidmapper-function.md), de la fonction en cours d’exécution qui est sur le paragraphe d’effectuer un appel tail.</span><span class="sxs-lookup"><span data-stu-id="bd286-107">\[in] The remapped function identifier, which the profiler previously specified via [FunctionIDMapper](functionidmapper-function.md), of the currently executing function that is about to make a tail call.</span></span>
  
- `func`

  <span data-ttu-id="bd286-108">\[in] `COR_PRF_FRAME_INFO` valeur qui pointe vers les informations sur le frame de pile.</span><span class="sxs-lookup"><span data-stu-id="bd286-108">\[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>

  <span data-ttu-id="bd286-109">Le profileur doit traiter ceci comme un handle opaque qui peut être retourné au moteur d’exécution dans la méthode [ICorProfilerInfo2 :: GetFunctionInfo2,](icorprofilerinfo2-getfunctioninfo2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="bd286-109">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>

## <a name="remarks"></a><span data-ttu-id="bd286-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="bd286-110">Remarks</span></span>  

 <span data-ttu-id="bd286-111">La fonction cible de l’appel tail utilise le frame de pile actuel et retourne directement à l’appelant de la fonction qui a effectué l’appel tail.</span><span class="sxs-lookup"><span data-stu-id="bd286-111">The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call.</span></span> <span data-ttu-id="bd286-112">Cela signifie qu’un rappel [FunctionLeave2](functionleave2-function.md) ne sera pas émis pour une fonction qui est la cible d’un appel tail.</span><span class="sxs-lookup"><span data-stu-id="bd286-112">This means that a [FunctionLeave2](functionleave2-function.md) callback will not be issued for a function that is the target of a tail call.</span></span>  
  
 <span data-ttu-id="bd286-113">La valeur du `func` paramètre n’est pas valide après le `FunctionTailcall2` retour de la fonction, car la valeur peut changer ou être détruite.</span><span class="sxs-lookup"><span data-stu-id="bd286-113">The value of the `func` parameter is not valid after the `FunctionTailcall2` function returns because the value may change or be destroyed.</span></span>  
  
 <span data-ttu-id="bd286-114">La `FunctionTailcall2` fonction est un rappel ; vous devez l’implémenter.</span><span class="sxs-lookup"><span data-stu-id="bd286-114">The `FunctionTailcall2` function is a callback; you must implement it.</span></span> <span data-ttu-id="bd286-115">L’implémentation doit utiliser l' `__declspec` `naked` attribut de classe de stockage ().</span><span class="sxs-lookup"><span data-stu-id="bd286-115">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="bd286-116">Le moteur d’exécution n’enregistre aucun registre avant d’appeler cette fonction.</span><span class="sxs-lookup"><span data-stu-id="bd286-116">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="bd286-117">À l’entrée, vous devez enregistrer tous les registres que vous utilisez, y compris ceux de l’unité à virgule flottante (FPU).</span><span class="sxs-lookup"><span data-stu-id="bd286-117">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="bd286-118">À la sortie, vous devez restaurer la pile en dépilant tous les paramètres qui ont été envoyés par son appelant.</span><span class="sxs-lookup"><span data-stu-id="bd286-118">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="bd286-119">L’implémentation de ne `FunctionTailcall2` doit pas être bloquée, car elle retardera garbage collection.</span><span class="sxs-lookup"><span data-stu-id="bd286-119">The implementation of `FunctionTailcall2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="bd286-120">L’implémentation ne doit pas essayer un garbage collection, car la pile n’est peut-être pas dans un État garbage collection.</span><span class="sxs-lookup"><span data-stu-id="bd286-120">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="bd286-121">Si une garbage collection est tentée, le runtime se bloque jusqu’à ce que `FunctionTailcall2` retourne la valeur.</span><span class="sxs-lookup"><span data-stu-id="bd286-121">If a garbage collection is attempted, the runtime will block until `FunctionTailcall2` returns.</span></span>  
  
 <span data-ttu-id="bd286-122">En outre, la `FunctionTailcall2` fonction ne doit pas appeler dans du code managé ou de quelque manière provoquer une allocation de mémoire managée.</span><span class="sxs-lookup"><span data-stu-id="bd286-122">Also, the `FunctionTailcall2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd286-123">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="bd286-123">Requirements</span></span>  

 <span data-ttu-id="bd286-124">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd286-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd286-125">**En-tête :** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="bd286-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="bd286-126">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bd286-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd286-127">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd286-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd286-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bd286-128">See also</span></span>

- [<span data-ttu-id="bd286-129">FunctionEnter2 (fonction)</span><span class="sxs-lookup"><span data-stu-id="bd286-129">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="bd286-130">FunctionLeave2 (fonction)</span><span class="sxs-lookup"><span data-stu-id="bd286-130">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="bd286-131">SetEnterLeaveFunctionHooks2, méthode</span><span class="sxs-lookup"><span data-stu-id="bd286-131">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="bd286-132">Fonctions statiques globales du profilage</span><span class="sxs-lookup"><span data-stu-id="bd286-132">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
