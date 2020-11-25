---
title: FunctionEnter3, fonction
ms.date: 03/30/2017
api_name:
- FunctionEnter3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter3
helpviewer_keywords:
- FunctionEnter3 function [.NET Framework profiling]
ms.assetid: ef782c53-dae7-4990-b4ad-fddb1e690d4e
topic_type:
- apiref
ms.openlocfilehash: 98a821eabb393d8b5042647e6ef6ffce7ab10783
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722880"
---
# <a name="functionenter3-function"></a><span data-ttu-id="95104-102">FunctionEnter3, fonction</span><span class="sxs-lookup"><span data-stu-id="95104-102">FunctionEnter3 Function</span></span>

<span data-ttu-id="95104-103">Indique au profileur que le contrôle est passé à une fonction.</span><span class="sxs-lookup"><span data-stu-id="95104-103">Notifies the profiler that control is being passed to a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95104-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95104-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95104-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="95104-105">Parameters</span></span>

- `functionOrRemappedID`

  <span data-ttu-id="95104-106">\[in] identificateur de la fonction vers laquelle le contrôle est passé.</span><span class="sxs-lookup"><span data-stu-id="95104-106">\[in] The identifier of the function to which control is passed.</span></span>

## <a name="remarks"></a><span data-ttu-id="95104-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="95104-107">Remarks</span></span>  

 <span data-ttu-id="95104-108">La `FunctionEnter3` fonction de rappel indique au profileur que les fonctions sont appelées, mais ne prend pas en charge l’inspection des arguments.</span><span class="sxs-lookup"><span data-stu-id="95104-108">The `FunctionEnter3` callback function notifies the profiler as functions are being called, but does not support argument inspection.</span></span> <span data-ttu-id="95104-109">Utilisez la [méthode ICorProfilerInfo3 :: SetEnterLeaveFunctionHooks3,](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) pour inscrire votre implémentation de cette fonction.</span><span class="sxs-lookup"><span data-stu-id="95104-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="95104-110">La `FunctionEnter3` fonction est un rappel ; vous devez l’implémenter.</span><span class="sxs-lookup"><span data-stu-id="95104-110">The `FunctionEnter3` function is a callback; you must implement it.</span></span> <span data-ttu-id="95104-111">L’implémentation doit utiliser l' `__declspec(naked)` attribut de classe de stockage.</span><span class="sxs-lookup"><span data-stu-id="95104-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="95104-112">Le moteur d’exécution n’enregistre aucun registre avant d’appeler cette fonction.</span><span class="sxs-lookup"><span data-stu-id="95104-112">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="95104-113">À l’entrée, vous devez enregistrer tous les registres que vous utilisez, y compris ceux de l’unité à virgule flottante (FPU).</span><span class="sxs-lookup"><span data-stu-id="95104-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="95104-114">À la sortie, vous devez restaurer la pile en dépilant tous les paramètres qui ont été envoyés par son appelant.</span><span class="sxs-lookup"><span data-stu-id="95104-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95104-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="95104-115">Requirements</span></span>  

 <span data-ttu-id="95104-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95104-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95104-117">**En-tête :** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="95104-117">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="95104-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="95104-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="95104-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95104-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95104-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95104-120">See also</span></span>

- [<span data-ttu-id="95104-121">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="95104-121">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="95104-122">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="95104-122">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="95104-123">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="95104-123">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="95104-124">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="95104-124">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="95104-125">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="95104-125">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="95104-126">Setenterleavefunctionhooks3,</span><span class="sxs-lookup"><span data-stu-id="95104-126">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="95104-127">Setenterleavefunctionhooks3withinfo,</span><span class="sxs-lookup"><span data-stu-id="95104-127">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="95104-128">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="95104-128">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="95104-129">Setfunctionidmapper2,</span><span class="sxs-lookup"><span data-stu-id="95104-129">SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="95104-130">Fonctions statiques globales du profilage</span><span class="sxs-lookup"><span data-stu-id="95104-130">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
