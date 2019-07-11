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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 80d82e26fe54c5422d1140bba84830879f0b5c2d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781286"
---
# <a name="functionleave-function"></a><span data-ttu-id="b6d0d-102">FunctionLeave (fonction)</span><span class="sxs-lookup"><span data-stu-id="b6d0d-102">FunctionLeave Function</span></span>
<span data-ttu-id="b6d0d-103">Notifie le profileur qu’une fonction est sur le point de retourner à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="b6d0d-103">Notifies the profiler that a function is about to return to the caller.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b6d0d-104">Le `FunctionLeave` fonction est déconseillée dans le .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="b6d0d-104">The `FunctionLeave` function is deprecated in the .NET Framework 2.0.</span></span> <span data-ttu-id="b6d0d-105">Il continue de fonctionner, mais entraîne une baisse des performances.</span><span class="sxs-lookup"><span data-stu-id="b6d0d-105">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="b6d0d-106">Utilisez le [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) fonctionner à la place.</span><span class="sxs-lookup"><span data-stu-id="b6d0d-106">Use the [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6d0d-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6d0d-107">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6d0d-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b6d0d-108">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="b6d0d-109">[in] L’identificateur de la fonction qui retourne.</span><span class="sxs-lookup"><span data-stu-id="b6d0d-109">[in] The identifier of the function that is returning.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6d0d-110">Notes</span><span class="sxs-lookup"><span data-stu-id="b6d0d-110">Remarks</span></span>  
 <span data-ttu-id="b6d0d-111">Le `FunctionLeave` fonction est un rappel ; vous devez l’implémenter.</span><span class="sxs-lookup"><span data-stu-id="b6d0d-111">The `FunctionLeave` function is a callback; you must implement it.</span></span> <span data-ttu-id="b6d0d-112">L’implémentation doit utiliser le `__declspec`(`naked`) attribut de classe de stockage.</span><span class="sxs-lookup"><span data-stu-id="b6d0d-112">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="b6d0d-113">Le moteur d’exécution n’enregistre pas les registres avant d’appeler cette fonction.</span><span class="sxs-lookup"><span data-stu-id="b6d0d-113">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="b6d0d-114">À l’entrée, vous devez enregistrer tous les registres que vous utilisez, y compris celles dans l’unité de virgule flottante (FPU).</span><span class="sxs-lookup"><span data-stu-id="b6d0d-114">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="b6d0d-115">À la sortie, vous devez restaurer la pile en dépilant tous les paramètres qui ont été envoyés par son appelant.</span><span class="sxs-lookup"><span data-stu-id="b6d0d-115">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="b6d0d-116">L’implémentation de `FunctionLeave` ne doivent pas bloquer, car il sera retarder le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="b6d0d-116">The implementation of `FunctionLeave` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="b6d0d-117">L’implémentation ne doit pas tenter un garbage collection, car la pile est peut-être pas à l’état garbage collection convivial.</span><span class="sxs-lookup"><span data-stu-id="b6d0d-117">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="b6d0d-118">Si un garbage collection est tenté, le runtime bloque jusqu'à ce que `FunctionLeave` retourne.</span><span class="sxs-lookup"><span data-stu-id="b6d0d-118">If a garbage collection is attempted, the runtime will block until `FunctionLeave` returns.</span></span>  
  
 <span data-ttu-id="b6d0d-119">En outre, le `FunctionLeave` (fonction) ne doit pas appeler dans du code managé ou de quelque manière qu’une allocation de mémoire managée.</span><span class="sxs-lookup"><span data-stu-id="b6d0d-119">Also, the `FunctionLeave` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6d0d-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b6d0d-120">Requirements</span></span>  
 <span data-ttu-id="b6d0d-121">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6d0d-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6d0d-122">**En-tête :** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="b6d0d-122">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="b6d0d-123">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6d0d-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6d0d-124">**Versions du .NET framework :** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="b6d0d-124">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6d0d-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6d0d-125">See also</span></span>

- [<span data-ttu-id="b6d0d-126">FunctionEnter2, fonction</span><span class="sxs-lookup"><span data-stu-id="b6d0d-126">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="b6d0d-127">FunctionLeave2, fonction</span><span class="sxs-lookup"><span data-stu-id="b6d0d-127">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [<span data-ttu-id="b6d0d-128">FunctionTailcall2, fonction</span><span class="sxs-lookup"><span data-stu-id="b6d0d-128">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [<span data-ttu-id="b6d0d-129">SetEnterLeaveFunctionHooks2, méthode</span><span class="sxs-lookup"><span data-stu-id="b6d0d-129">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="b6d0d-130">Fonctions statiques globales de profilage</span><span class="sxs-lookup"><span data-stu-id="b6d0d-130">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
