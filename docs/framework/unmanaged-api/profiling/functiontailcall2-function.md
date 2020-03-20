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
ms.openlocfilehash: 60276327617ae24e9bdcebf958613c21d3808429
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175185"
---
# <a name="functiontailcall2-function"></a><span data-ttu-id="a823f-102">FunctionTailcall2 (fonction)</span><span class="sxs-lookup"><span data-stu-id="a823f-102">FunctionTailcall2 Function</span></span>
<span data-ttu-id="a823f-103">Informe le profileur que la fonction d’exécution actuelle est sur le point d’effectuer un appel de queue à une autre fonction et fournit des informations sur le cadre de pile.</span><span class="sxs-lookup"><span data-stu-id="a823f-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function and provides information about the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a823f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a823f-104">Syntax</span></span>  
  
```cpp
void __stdcall FunctionTailcall2 (  
    [in] FunctionID         funcId,
    [in] UINT_PTR           clientData,
    [in] COR_PRF_FRAME_INFO func  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a823f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a823f-105">Parameters</span></span>

- `funcId`

  <span data-ttu-id="a823f-106">\[dans] L’identifiant de la fonction d’exécution actuelle qui est sur le point de faire un appel de queue.</span><span class="sxs-lookup"><span data-stu-id="a823f-106">\[in] The identifier of the currently executing function that is about to make a tail call.</span></span>

- `clientData`

  <span data-ttu-id="a823f-107">\[dans] L’identifiant de fonction remapped, que le profileur précédemment spécifié via [FunctionIDMapper](functionidmapper-function.md), de la fonction d’exécution actuellement qui est sur le point de faire un appel de queue.</span><span class="sxs-lookup"><span data-stu-id="a823f-107">\[in] The remapped function identifier, which the profiler previously specified via [FunctionIDMapper](functionidmapper-function.md), of the currently executing function that is about to make a tail call.</span></span>
  
- `func`

  <span data-ttu-id="a823f-108">\[dans] `COR_PRF_FRAME_INFO` Une valeur qui indique des informations sur le cadre de pile.</span><span class="sxs-lookup"><span data-stu-id="a823f-108">\[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>

  <span data-ttu-id="a823f-109">Le profileur doit traiter cela comme une poignée opaque qui peut être transmis au moteur d’exécution dans la méthode [ICorProfilerInfo2::GetFunctionInfo2.](icorprofilerinfo2-getfunctioninfo2-method.md)</span><span class="sxs-lookup"><span data-stu-id="a823f-109">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>

## <a name="remarks"></a><span data-ttu-id="a823f-110">Notes </span><span class="sxs-lookup"><span data-stu-id="a823f-110">Remarks</span></span>  
 <span data-ttu-id="a823f-111">La fonction cible de l’appel de queue utilisera le cadre de pile actuel, et retournera directement à l’appelant de la fonction qui a fait l’appel de queue.</span><span class="sxs-lookup"><span data-stu-id="a823f-111">The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call.</span></span> <span data-ttu-id="a823f-112">Cela signifie qu’un rappel [FunctionLeave2](functionleave2-function.md) ne sera pas émis pour une fonction qui est la cible d’un appel de queue.</span><span class="sxs-lookup"><span data-stu-id="a823f-112">This means that a [FunctionLeave2](functionleave2-function.md) callback will not be issued for a function that is the target of a tail call.</span></span>  
  
 <span data-ttu-id="a823f-113">La valeur `func` du paramètre n’est pas valide après le retour de la `FunctionTailcall2` fonction parce que la valeur peut changer ou être détruite.</span><span class="sxs-lookup"><span data-stu-id="a823f-113">The value of the `func` parameter is not valid after the `FunctionTailcall2` function returns because the value may change or be destroyed.</span></span>  
  
 <span data-ttu-id="a823f-114">La `FunctionTailcall2` fonction est un rappel; vous devez le mettre en œuvre.</span><span class="sxs-lookup"><span data-stu-id="a823f-114">The `FunctionTailcall2` function is a callback; you must implement it.</span></span> <span data-ttu-id="a823f-115">La mise en `__declspec``naked`œuvre doit utiliser l’attribut de la classe de stockage.</span><span class="sxs-lookup"><span data-stu-id="a823f-115">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="a823f-116">Le moteur d’exécution n’enregistre aucun registre avant d’appeler cette fonction.</span><span class="sxs-lookup"><span data-stu-id="a823f-116">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="a823f-117">À l’entrée, vous devez enregistrer tous les registres que vous utilisez, y compris ceux de l’unité à point flottant (FPU).</span><span class="sxs-lookup"><span data-stu-id="a823f-117">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="a823f-118">À la sortie, vous devez restaurer la pile en sortant de tous les paramètres qui ont été poussés par son appelant.</span><span class="sxs-lookup"><span data-stu-id="a823f-118">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="a823f-119">La mise `FunctionTailcall2` en œuvre de ne devrait pas bloquer parce qu’elle retardera la collecte des ordures.</span><span class="sxs-lookup"><span data-stu-id="a823f-119">The implementation of `FunctionTailcall2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="a823f-120">La mise en œuvre ne devrait pas tenter une collecte des ordures parce que la pile peut ne pas être dans un état de collecte des ordures.</span><span class="sxs-lookup"><span data-stu-id="a823f-120">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="a823f-121">Si une collecte d’ordures est tentée, le temps d’exécution se bloque jusqu’à ce que `FunctionTailcall2` le retour.</span><span class="sxs-lookup"><span data-stu-id="a823f-121">If a garbage collection is attempted, the runtime will block until `FunctionTailcall2` returns.</span></span>  
  
 <span data-ttu-id="a823f-122">En outre, la `FunctionTailcall2` fonction ne doit pas appeler dans le code géré ou en aucune façon provoquer une allocation de mémoire gérée.</span><span class="sxs-lookup"><span data-stu-id="a823f-122">Also, the `FunctionTailcall2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a823f-123">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a823f-123">Requirements</span></span>  
 <span data-ttu-id="a823f-124">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a823f-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a823f-125">**En-tête:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="a823f-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="a823f-126">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a823f-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a823f-127">**.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a823f-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a823f-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a823f-128">See also</span></span>

- [<span data-ttu-id="a823f-129">FunctionEnter2 (fonction)</span><span class="sxs-lookup"><span data-stu-id="a823f-129">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="a823f-130">FunctionLeave2 (fonction)</span><span class="sxs-lookup"><span data-stu-id="a823f-130">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="a823f-131">SetEnterLeaveFunctionHooks2, méthode</span><span class="sxs-lookup"><span data-stu-id="a823f-131">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="a823f-132">Fonctions statiques globales du profilage</span><span class="sxs-lookup"><span data-stu-id="a823f-132">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
