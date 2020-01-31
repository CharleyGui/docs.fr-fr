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
ms.openlocfilehash: bd03eccc923049c4a49062d18bd11659f3316e8a
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866821"
---
# <a name="functiontailcall-function"></a><span data-ttu-id="3af5c-102">FunctionTailcall (fonction)</span><span class="sxs-lookup"><span data-stu-id="3af5c-102">FunctionTailcall Function</span></span>
<span data-ttu-id="3af5c-103">Indique au profileur que la fonction en cours d’exécution est sur le paragraphe d’effectuer un appel tail à une autre fonction.</span><span class="sxs-lookup"><span data-stu-id="3af5c-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3af5c-104">La fonction `FunctionTailcall` est déconseillée dans la version .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="3af5c-104">The `FunctionTailcall` function is deprecated in the .NET Framework version 2.0.</span></span> <span data-ttu-id="3af5c-105">Il continuera à fonctionner, mais entraînera une baisse des performances.</span><span class="sxs-lookup"><span data-stu-id="3af5c-105">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="3af5c-106">Utilisez à la place la fonction [FunctionTailcall2](functiontailcall2-function.md) .</span><span class="sxs-lookup"><span data-stu-id="3af5c-106">Use the [FunctionTailcall2](functiontailcall2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3af5c-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3af5c-107">Syntax</span></span>  
  
```cpp
void __stdcall FunctionTailcall (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3af5c-108">Parameters</span><span class="sxs-lookup"><span data-stu-id="3af5c-108">Parameters</span></span>

- `funcID`

  <span data-ttu-id="3af5c-109">\[in] identificateur de la fonction en cours d’exécution qui est sur le paragraphe d’effectuer un appel tail.</span><span class="sxs-lookup"><span data-stu-id="3af5c-109">\[in] The identifier of the currently executing function that is about to make a tail call.</span></span>

## <a name="remarks"></a><span data-ttu-id="3af5c-110">Notes</span><span class="sxs-lookup"><span data-stu-id="3af5c-110">Remarks</span></span>  
 <span data-ttu-id="3af5c-111">La fonction cible de l’appel tail utilise le frame de pile actuel et retourne directement à l’appelant de la fonction qui a effectué l’appel tail.</span><span class="sxs-lookup"><span data-stu-id="3af5c-111">The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call.</span></span> <span data-ttu-id="3af5c-112">Cela signifie qu’un rappel [FunctionLeave](functionleave-function.md) ne sera pas émis pour une fonction qui est la cible d’un appel tail.</span><span class="sxs-lookup"><span data-stu-id="3af5c-112">This means that a [FunctionLeave](functionleave-function.md) callback will not be issued for a function that is the target of a tail call.</span></span>  
  
 <span data-ttu-id="3af5c-113">La fonction `FunctionTailcall` est un rappel ; vous devez l’implémenter.</span><span class="sxs-lookup"><span data-stu-id="3af5c-113">The `FunctionTailcall` function is a callback; you must implement it.</span></span> <span data-ttu-id="3af5c-114">L’implémentation doit utiliser l’attribut de classe de stockage `__declspec`(`naked`).</span><span class="sxs-lookup"><span data-stu-id="3af5c-114">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="3af5c-115">Le moteur d’exécution n’enregistre aucun registre avant d’appeler cette fonction.</span><span class="sxs-lookup"><span data-stu-id="3af5c-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="3af5c-116">À l’entrée, vous devez enregistrer tous les registres que vous utilisez, y compris ceux de l’unité à virgule flottante (FPU).</span><span class="sxs-lookup"><span data-stu-id="3af5c-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="3af5c-117">À la sortie, vous devez restaurer la pile en dépilant tous les paramètres qui ont été envoyés par son appelant.</span><span class="sxs-lookup"><span data-stu-id="3af5c-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="3af5c-118">L’implémentation de `FunctionTailcall` ne doit pas être bloquée, car elle retardera garbage collection.</span><span class="sxs-lookup"><span data-stu-id="3af5c-118">The implementation of `FunctionTailcall` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="3af5c-119">L’implémentation ne doit pas essayer un garbage collection, car la pile n’est peut-être pas dans un État garbage collection.</span><span class="sxs-lookup"><span data-stu-id="3af5c-119">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="3af5c-120">Si une garbage collection est tentée, le runtime se bloque jusqu’à ce que `FunctionTailcall` retourne.</span><span class="sxs-lookup"><span data-stu-id="3af5c-120">If a garbage collection is attempted, the runtime will block until `FunctionTailcall` returns.</span></span>  
  
 <span data-ttu-id="3af5c-121">En outre, la fonction `FunctionTailcall` ne doit pas appeler dans du code managé ou de quelque manière qu’elle génère une allocation de mémoire managée.</span><span class="sxs-lookup"><span data-stu-id="3af5c-121">Also, the `FunctionTailcall` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3af5c-122">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="3af5c-122">Requirements</span></span>  
 <span data-ttu-id="3af5c-123">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3af5c-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3af5c-124">**En-tête :** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="3af5c-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="3af5c-125">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3af5c-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3af5c-126">**Versions de .NET Framework :** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="3af5c-126">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3af5c-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3af5c-127">See also</span></span>

- [<span data-ttu-id="3af5c-128">FunctionEnter2, fonction</span><span class="sxs-lookup"><span data-stu-id="3af5c-128">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="3af5c-129">FunctionLeave2, fonction</span><span class="sxs-lookup"><span data-stu-id="3af5c-129">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="3af5c-130">SetEnterLeaveFunctionHooks2, méthode</span><span class="sxs-lookup"><span data-stu-id="3af5c-130">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="3af5c-131">Fonctions statiques globales de profilage</span><span class="sxs-lookup"><span data-stu-id="3af5c-131">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
