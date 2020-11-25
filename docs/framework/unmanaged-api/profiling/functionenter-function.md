---
title: FunctionEnter (fonction)
ms.date: 03/30/2017
api_name:
- FunctionEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter
helpviewer_keywords:
- FunctionEnter function [.NET Framework profiling]
ms.assetid: bf4ffa50-4506-4dd4-aa13-a0457b47ca74
topic_type:
- apiref
ms.openlocfilehash: 9bc88d7dd5b00213da634dc9f511cfe0d39b42f1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729835"
---
# <a name="functionenter-function"></a><span data-ttu-id="b9a8d-102">FunctionEnter (fonction)</span><span class="sxs-lookup"><span data-stu-id="b9a8d-102">FunctionEnter Function</span></span>

<span data-ttu-id="b9a8d-103">Indique au profileur que le contrôle est passé à une fonction.</span><span class="sxs-lookup"><span data-stu-id="b9a8d-103">Notifies the profiler that control is being passed to a function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b9a8d-104">La `FunctionEnter` fonction est déconseillée dans la version 2,0 de .NET Framework, et son utilisation entraîne une baisse des performances.</span><span class="sxs-lookup"><span data-stu-id="b9a8d-104">The `FunctionEnter` function is deprecated in the .NET Framework version 2.0, and its use will incur a performance penalty.</span></span> <span data-ttu-id="b9a8d-105">Utilisez la fonction [FunctionEnter2](functionenter2-function.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="b9a8d-105">Use the [FunctionEnter2](functionenter2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9a8d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b9a8d-106">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter (  
    [in]  FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9a8d-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b9a8d-107">Parameters</span></span>

- `funcID`

  <span data-ttu-id="b9a8d-108">\[in] identificateur de la fonction vers laquelle le contrôle est passé.</span><span class="sxs-lookup"><span data-stu-id="b9a8d-108">\[in] The identifier of the function to which control is passed.</span></span>

## <a name="remarks"></a><span data-ttu-id="b9a8d-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="b9a8d-109">Remarks</span></span>  

 <span data-ttu-id="b9a8d-110">La `FunctionEnter` fonction est un rappel ; vous devez l’implémenter.</span><span class="sxs-lookup"><span data-stu-id="b9a8d-110">The `FunctionEnter` function is a callback; you must implement it.</span></span> <span data-ttu-id="b9a8d-111">L’implémentation doit utiliser l' `__declspec` `naked` attribut de classe de stockage ().</span><span class="sxs-lookup"><span data-stu-id="b9a8d-111">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="b9a8d-112">Le moteur d’exécution n’enregistre aucun registre avant d’appeler cette fonction.</span><span class="sxs-lookup"><span data-stu-id="b9a8d-112">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="b9a8d-113">À l’entrée, vous devez enregistrer tous les registres que vous utilisez, y compris ceux de l’unité à virgule flottante (FPU).</span><span class="sxs-lookup"><span data-stu-id="b9a8d-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="b9a8d-114">À la sortie, vous devez restaurer la pile en dépilant tous les paramètres qui ont été envoyés par son appelant.</span><span class="sxs-lookup"><span data-stu-id="b9a8d-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="b9a8d-115">L’implémentation de ne `FunctionEnter` doit pas être bloquée, car elle retardera garbage collection.</span><span class="sxs-lookup"><span data-stu-id="b9a8d-115">The implementation of `FunctionEnter` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="b9a8d-116">L’implémentation ne doit pas essayer un garbage collection, car la pile n’est peut-être pas dans un État garbage collection.</span><span class="sxs-lookup"><span data-stu-id="b9a8d-116">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="b9a8d-117">Si une garbage collection est tentée, le runtime se bloque jusqu’à ce que `FunctionEnter` retourne la valeur.</span><span class="sxs-lookup"><span data-stu-id="b9a8d-117">If a garbage collection is attempted, the runtime will block until `FunctionEnter` returns.</span></span>  
  
 <span data-ttu-id="b9a8d-118">En outre, la `FunctionEnter` fonction ne doit pas appeler dans du code managé ou de quelque manière provoquer une allocation de mémoire managée.</span><span class="sxs-lookup"><span data-stu-id="b9a8d-118">Also, the `FunctionEnter` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9a8d-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b9a8d-119">Requirements</span></span>  

 <span data-ttu-id="b9a8d-120">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9a8d-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9a8d-121">**En-tête :** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="b9a8d-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="b9a8d-122">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9a8d-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9a8d-123">**Versions de .NET Framework :** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="b9a8d-123">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9a8d-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b9a8d-124">See also</span></span>

- [<span data-ttu-id="b9a8d-125">FunctionEnter2 (fonction)</span><span class="sxs-lookup"><span data-stu-id="b9a8d-125">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="b9a8d-126">FunctionLeave2 (fonction)</span><span class="sxs-lookup"><span data-stu-id="b9a8d-126">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="b9a8d-127">FunctionTailcall2 (fonction)</span><span class="sxs-lookup"><span data-stu-id="b9a8d-127">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="b9a8d-128">SetEnterLeaveFunctionHooks2, méthode</span><span class="sxs-lookup"><span data-stu-id="b9a8d-128">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="b9a8d-129">Fonctions statiques globales du profilage</span><span class="sxs-lookup"><span data-stu-id="b9a8d-129">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
