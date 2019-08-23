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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: afc0929b8f1b12f4e0b4551d826b8a1d59990154
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952881"
---
# <a name="functiontailcall-function"></a><span data-ttu-id="dccd3-102">FunctionTailcall (fonction)</span><span class="sxs-lookup"><span data-stu-id="dccd3-102">FunctionTailcall Function</span></span>
<span data-ttu-id="dccd3-103">Indique au profileur que la fonction en cours d’exécution est sur le paragraphe d’effectuer un appel tail à une autre fonction.</span><span class="sxs-lookup"><span data-stu-id="dccd3-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dccd3-104">La `FunctionTailcall` fonction est déconseillée dans la version 2,0 de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dccd3-104">The `FunctionTailcall` function is deprecated in the .NET Framework version 2.0.</span></span> <span data-ttu-id="dccd3-105">Il continuera à fonctionner, mais entraînera une baisse des performances.</span><span class="sxs-lookup"><span data-stu-id="dccd3-105">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="dccd3-106">Utilisez à la place la fonction [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) .</span><span class="sxs-lookup"><span data-stu-id="dccd3-106">Use the [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dccd3-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dccd3-107">Syntax</span></span>  
  
```  
void __stdcall FunctionTailcall (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dccd3-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="dccd3-108">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="dccd3-109">dans Identificateur de la fonction en cours d’exécution qui va effectuer un appel tail.</span><span class="sxs-lookup"><span data-stu-id="dccd3-109">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dccd3-110">Notes</span><span class="sxs-lookup"><span data-stu-id="dccd3-110">Remarks</span></span>  
 <span data-ttu-id="dccd3-111">La fonction cible de l’appel tail utilise le frame de pile actuel et retourne directement à l’appelant de la fonction qui a effectué l’appel tail.</span><span class="sxs-lookup"><span data-stu-id="dccd3-111">The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call.</span></span> <span data-ttu-id="dccd3-112">Cela signifie qu’un rappel [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) ne sera pas émis pour une fonction qui est la cible d’un appel tail.</span><span class="sxs-lookup"><span data-stu-id="dccd3-112">This means that a [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) callback will not be issued for a function that is the target of a tail call.</span></span>  
  
 <span data-ttu-id="dccd3-113">La `FunctionTailcall` fonction est un rappel; vous devez l’implémenter.</span><span class="sxs-lookup"><span data-stu-id="dccd3-113">The `FunctionTailcall` function is a callback; you must implement it.</span></span> <span data-ttu-id="dccd3-114">L’implémentation doit utiliser l' `__declspec`attribut`naked`de classe de stockage ().</span><span class="sxs-lookup"><span data-stu-id="dccd3-114">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="dccd3-115">Le moteur d’exécution n’enregistre aucun registre avant d’appeler cette fonction.</span><span class="sxs-lookup"><span data-stu-id="dccd3-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="dccd3-116">À l’entrée, vous devez enregistrer tous les registres que vous utilisez, y compris ceux de l’unité à virgule flottante (FPU).</span><span class="sxs-lookup"><span data-stu-id="dccd3-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="dccd3-117">À la sortie, vous devez restaurer la pile en dépilant tous les paramètres qui ont été envoyés par son appelant.</span><span class="sxs-lookup"><span data-stu-id="dccd3-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="dccd3-118">L’implémentation de `FunctionTailcall` ne doit pas être bloquée, car elle retardera garbage collection.</span><span class="sxs-lookup"><span data-stu-id="dccd3-118">The implementation of `FunctionTailcall` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="dccd3-119">L’implémentation ne doit pas essayer un garbage collection, car la pile n’est peut-être pas dans un État garbage collection.</span><span class="sxs-lookup"><span data-stu-id="dccd3-119">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="dccd3-120">Si une garbage collection est tentée, le runtime se bloque jusqu’à ce que `FunctionTailcall` retourne la valeur.</span><span class="sxs-lookup"><span data-stu-id="dccd3-120">If a garbage collection is attempted, the runtime will block until `FunctionTailcall` returns.</span></span>  
  
 <span data-ttu-id="dccd3-121">En outre, `FunctionTailcall` la fonction ne doit pas appeler dans du code managé ou de quelque manière provoquer une allocation de mémoire managée.</span><span class="sxs-lookup"><span data-stu-id="dccd3-121">Also, the `FunctionTailcall` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dccd3-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="dccd3-122">Requirements</span></span>  
 <span data-ttu-id="dccd3-123">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dccd3-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dccd3-124">**En-tête :** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="dccd3-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="dccd3-125">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dccd3-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dccd3-126">**Versions de .NET Framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="dccd3-126">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dccd3-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dccd3-127">See also</span></span>

- [<span data-ttu-id="dccd3-128">FunctionEnter2, fonction</span><span class="sxs-lookup"><span data-stu-id="dccd3-128">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="dccd3-129">FunctionLeave2, fonction</span><span class="sxs-lookup"><span data-stu-id="dccd3-129">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [<span data-ttu-id="dccd3-130">SetEnterLeaveFunctionHooks2, méthode</span><span class="sxs-lookup"><span data-stu-id="dccd3-130">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="dccd3-131">Fonctions statiques globales de profilage</span><span class="sxs-lookup"><span data-stu-id="dccd3-131">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
