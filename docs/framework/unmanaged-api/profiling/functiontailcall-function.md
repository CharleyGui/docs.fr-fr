---
title: FunctionTailcall (fonction)
ms.date: 03/30/2017
api_name:
- FunctionTailcall
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall
helpviewer_keywords:
- FunctionTailcall function [.NET Framework profiling]
ms.assetid: 66347e03-9a97-41e8-8f9d-89b80803f7b5
topic_type:
- apiref
ms.openlocfilehash: 02bc6f4bbb6754bd160fe2694f27563908f3a759
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722217"
---
# <a name="functiontailcall-function"></a><span data-ttu-id="6a217-102">FunctionTailcall (fonction)</span><span class="sxs-lookup"><span data-stu-id="6a217-102">FunctionTailcall Function</span></span>

<span data-ttu-id="6a217-103">Indique au profileur que la fonction en cours d’exécution est sur le paragraphe d’effectuer un appel tail à une autre fonction.</span><span class="sxs-lookup"><span data-stu-id="6a217-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6a217-104">La `FunctionTailcall` fonction est déconseillée dans la version 2,0 de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6a217-104">The `FunctionTailcall` function is deprecated in the .NET Framework version 2.0.</span></span> <span data-ttu-id="6a217-105">Il continuera à fonctionner, mais entraînera une baisse des performances.</span><span class="sxs-lookup"><span data-stu-id="6a217-105">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="6a217-106">Utilisez à la place la fonction [FunctionTailcall2](functiontailcall2-function.md) .</span><span class="sxs-lookup"><span data-stu-id="6a217-106">Use the [FunctionTailcall2](functiontailcall2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a217-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a217-107">Syntax</span></span>  
  
```cpp
void __stdcall FunctionTailcall (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a217-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6a217-108">Parameters</span></span>

- `funcID`

  <span data-ttu-id="6a217-109">\[in] identificateur de la fonction en cours d’exécution qui est sur le paragraphe d’effectuer un appel tail.</span><span class="sxs-lookup"><span data-stu-id="6a217-109">\[in] The identifier of the currently executing function that is about to make a tail call.</span></span>

## <a name="remarks"></a><span data-ttu-id="6a217-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="6a217-110">Remarks</span></span>  

 <span data-ttu-id="6a217-111">La fonction cible de l’appel tail utilise le frame de pile actuel et retourne directement à l’appelant de la fonction qui a effectué l’appel tail.</span><span class="sxs-lookup"><span data-stu-id="6a217-111">The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call.</span></span> <span data-ttu-id="6a217-112">Cela signifie qu’un rappel [FunctionLeave](functionleave-function.md) ne sera pas émis pour une fonction qui est la cible d’un appel tail.</span><span class="sxs-lookup"><span data-stu-id="6a217-112">This means that a [FunctionLeave](functionleave-function.md) callback will not be issued for a function that is the target of a tail call.</span></span>  
  
 <span data-ttu-id="6a217-113">La `FunctionTailcall` fonction est un rappel ; vous devez l’implémenter.</span><span class="sxs-lookup"><span data-stu-id="6a217-113">The `FunctionTailcall` function is a callback; you must implement it.</span></span> <span data-ttu-id="6a217-114">L’implémentation doit utiliser l' `__declspec` `naked` attribut de classe de stockage ().</span><span class="sxs-lookup"><span data-stu-id="6a217-114">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="6a217-115">Le moteur d’exécution n’enregistre aucun registre avant d’appeler cette fonction.</span><span class="sxs-lookup"><span data-stu-id="6a217-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="6a217-116">À l’entrée, vous devez enregistrer tous les registres que vous utilisez, y compris ceux de l’unité à virgule flottante (FPU).</span><span class="sxs-lookup"><span data-stu-id="6a217-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="6a217-117">À la sortie, vous devez restaurer la pile en dépilant tous les paramètres qui ont été envoyés par son appelant.</span><span class="sxs-lookup"><span data-stu-id="6a217-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="6a217-118">L’implémentation de ne `FunctionTailcall` doit pas être bloquée, car elle retardera garbage collection.</span><span class="sxs-lookup"><span data-stu-id="6a217-118">The implementation of `FunctionTailcall` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="6a217-119">L’implémentation ne doit pas essayer un garbage collection, car la pile n’est peut-être pas dans un État garbage collection.</span><span class="sxs-lookup"><span data-stu-id="6a217-119">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="6a217-120">Si une garbage collection est tentée, le runtime se bloque jusqu’à ce que `FunctionTailcall` retourne la valeur.</span><span class="sxs-lookup"><span data-stu-id="6a217-120">If a garbage collection is attempted, the runtime will block until `FunctionTailcall` returns.</span></span>  
  
 <span data-ttu-id="6a217-121">En outre, la `FunctionTailcall` fonction ne doit pas appeler dans du code managé ou de quelque manière provoquer une allocation de mémoire managée.</span><span class="sxs-lookup"><span data-stu-id="6a217-121">Also, the `FunctionTailcall` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a217-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6a217-122">Requirements</span></span>  

 <span data-ttu-id="6a217-123">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a217-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a217-124">**En-tête :** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="6a217-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="6a217-125">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6a217-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a217-126">**Versions de .NET Framework :** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="6a217-126">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a217-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6a217-127">See also</span></span>

- [<span data-ttu-id="6a217-128">FunctionEnter2 (fonction)</span><span class="sxs-lookup"><span data-stu-id="6a217-128">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="6a217-129">FunctionLeave2 (fonction)</span><span class="sxs-lookup"><span data-stu-id="6a217-129">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="6a217-130">SetEnterLeaveFunctionHooks2, méthode</span><span class="sxs-lookup"><span data-stu-id="6a217-130">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="6a217-131">Fonctions statiques globales du profilage</span><span class="sxs-lookup"><span data-stu-id="6a217-131">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
