---
title: FunctionLeave (fonction)
ms.date: 03/30/2017
api_name:
- FunctionLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave
helpviewer_keywords:
- FunctionLeave function [.NET Framework profiling]
ms.assetid: 18e89f45-e068-426a-be16-9f53a4346860
topic_type:
- apiref
ms.openlocfilehash: a9ab8c81c995bbec41db217c904e03dd70351aee
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866882"
---
# <a name="functionleave-function"></a><span data-ttu-id="a401c-102">FunctionLeave (fonction)</span><span class="sxs-lookup"><span data-stu-id="a401c-102">FunctionLeave Function</span></span>
<span data-ttu-id="a401c-103">Notifie le profileur qu’une fonction va retourner à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="a401c-103">Notifies the profiler that a function is about to return to the caller.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a401c-104">La fonction `FunctionLeave` est dépréciée dans le .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="a401c-104">The `FunctionLeave` function is deprecated in the .NET Framework 2.0.</span></span> <span data-ttu-id="a401c-105">Il continuera à fonctionner, mais entraînera une baisse des performances.</span><span class="sxs-lookup"><span data-stu-id="a401c-105">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="a401c-106">Utilisez la fonction [FunctionLeave2](functionleave2-function.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="a401c-106">Use the [FunctionLeave2](functionleave2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a401c-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a401c-107">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a401c-108">Parameters</span><span class="sxs-lookup"><span data-stu-id="a401c-108">Parameters</span></span>

- `funcID`

  <span data-ttu-id="a401c-109">\[in] identificateur de la fonction qui retourne.</span><span class="sxs-lookup"><span data-stu-id="a401c-109">\[in] The identifier of the function that is returning.</span></span>

## <a name="remarks"></a><span data-ttu-id="a401c-110">Notes</span><span class="sxs-lookup"><span data-stu-id="a401c-110">Remarks</span></span>  
 <span data-ttu-id="a401c-111">La fonction `FunctionLeave` est un rappel ; vous devez l’implémenter.</span><span class="sxs-lookup"><span data-stu-id="a401c-111">The `FunctionLeave` function is a callback; you must implement it.</span></span> <span data-ttu-id="a401c-112">L’implémentation doit utiliser l’attribut de classe de stockage `__declspec`(`naked`).</span><span class="sxs-lookup"><span data-stu-id="a401c-112">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="a401c-113">Le moteur d’exécution n’enregistre aucun registre avant d’appeler cette fonction.</span><span class="sxs-lookup"><span data-stu-id="a401c-113">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="a401c-114">À l’entrée, vous devez enregistrer tous les registres que vous utilisez, y compris ceux de l’unité à virgule flottante (FPU).</span><span class="sxs-lookup"><span data-stu-id="a401c-114">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="a401c-115">À la sortie, vous devez restaurer la pile en dépilant tous les paramètres qui ont été envoyés par son appelant.</span><span class="sxs-lookup"><span data-stu-id="a401c-115">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="a401c-116">L’implémentation de `FunctionLeave` ne doit pas être bloquée, car elle retardera garbage collection.</span><span class="sxs-lookup"><span data-stu-id="a401c-116">The implementation of `FunctionLeave` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="a401c-117">L’implémentation ne doit pas essayer un garbage collection, car la pile n’est peut-être pas dans un État garbage collection.</span><span class="sxs-lookup"><span data-stu-id="a401c-117">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="a401c-118">Si une garbage collection est tentée, le runtime se bloque jusqu’à ce que `FunctionLeave` retourne.</span><span class="sxs-lookup"><span data-stu-id="a401c-118">If a garbage collection is attempted, the runtime will block until `FunctionLeave` returns.</span></span>  
  
 <span data-ttu-id="a401c-119">En outre, la fonction `FunctionLeave` ne doit pas appeler dans du code managé ou de quelque manière qu’elle génère une allocation de mémoire managée.</span><span class="sxs-lookup"><span data-stu-id="a401c-119">Also, the `FunctionLeave` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a401c-120">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="a401c-120">Requirements</span></span>  
 <span data-ttu-id="a401c-121">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a401c-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a401c-122">**En-tête :** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="a401c-122">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="a401c-123">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a401c-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a401c-124">**Versions de .NET Framework :** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="a401c-124">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a401c-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a401c-125">See also</span></span>

- [<span data-ttu-id="a401c-126">FunctionEnter2, fonction</span><span class="sxs-lookup"><span data-stu-id="a401c-126">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="a401c-127">FunctionLeave2, fonction</span><span class="sxs-lookup"><span data-stu-id="a401c-127">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="a401c-128">FunctionTailcall2, fonction</span><span class="sxs-lookup"><span data-stu-id="a401c-128">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="a401c-129">SetEnterLeaveFunctionHooks2, méthode</span><span class="sxs-lookup"><span data-stu-id="a401c-129">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="a401c-130">Fonctions statiques globales de profilage</span><span class="sxs-lookup"><span data-stu-id="a401c-130">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
