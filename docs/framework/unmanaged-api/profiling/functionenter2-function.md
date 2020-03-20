---
title: FunctionEnter2 (fonction)
ms.date: 03/30/2017
api_name:
- FunctionEnter2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter2
helpviewer_keywords:
- FunctionEnter2 function [.NET Framework profiling]
ms.assetid: ce7a21f9-0ca3-4b92-bc4b-bb803cae3f51
topic_type:
- apiref
ms.openlocfilehash: 9aeb7a294beb10f9c2968e6161c72fdc362c4991
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177057"
---
# <a name="functionenter2-function"></a><span data-ttu-id="68302-102">FunctionEnter2 (fonction)</span><span class="sxs-lookup"><span data-stu-id="68302-102">FunctionEnter2 Function</span></span>
<span data-ttu-id="68302-103">Informe le profileur que le contrôle est passé à une fonction et fournit des informations sur le cadre de pile et les arguments de fonction.</span><span class="sxs-lookup"><span data-stu-id="68302-103">Notifies the profiler that control is being passed to a function and provides information about the stack frame and function arguments.</span></span> <span data-ttu-id="68302-104">Cette fonction remplace la fonction [FunctionEnter.](functionenter-function.md)</span><span class="sxs-lookup"><span data-stu-id="68302-104">This function supersedes the [FunctionEnter](functionenter-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68302-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68302-105">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter2 (  
    [in]  FunctionID                       funcId,
    [in]  UINT_PTR                         clientData,
    [in]  COR_PRF_FRAME_INFO               func,
    [in]  COR_PRF_FUNCTION_ARGUMENT_INFO  *argumentInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68302-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="68302-106">Parameters</span></span>

- `funcId`

  <span data-ttu-id="68302-107">\[dans] l’identifiant de la fonction à laquelle le contrôle est passé.</span><span class="sxs-lookup"><span data-stu-id="68302-107">\[in] The identifier of the function to which control is passed.</span></span>

- `clientData`

  <span data-ttu-id="68302-108">\[dans] L’identifiant de fonction remapped, que le profileur a précédemment spécifié en utilisant la fonction [FunctionIDMapper.](functionidmapper-function.md)</span><span class="sxs-lookup"><span data-stu-id="68302-108">\[in] The remapped function identifier, which the profiler previously specified by using the [FunctionIDMapper](functionidmapper-function.md) function.</span></span>
  
- `func`

  <span data-ttu-id="68302-109">\[dans] `COR_PRF_FRAME_INFO` Une valeur qui indique des informations sur le cadre de pile.</span><span class="sxs-lookup"><span data-stu-id="68302-109">\[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>
  
  <span data-ttu-id="68302-110">Le profileur doit traiter cela comme une poignée opaque qui peut être transmis au moteur d’exécution dans la méthode [ICorProfilerInfo2::GetFunctionInfo2.](icorprofilerinfo2-getfunctioninfo2-method.md)</span><span class="sxs-lookup"><span data-stu-id="68302-110">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
- `argumentInfo`

  <span data-ttu-id="68302-111">\[dans] Un pointeur vers une structure [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) qui spécifie les emplacements en mémoire des arguments de la fonction.</span><span class="sxs-lookup"><span data-stu-id="68302-111">\[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) structure that specifies the locations in memory of the function's arguments.</span></span>

  <span data-ttu-id="68302-112">Afin d’accéder aux `COR_PRF_ENABLE_FUNCTION_ARGS` informations d’argumentation, le drapeau doit être fixé.</span><span class="sxs-lookup"><span data-stu-id="68302-112">In order to access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag must be set.</span></span> <span data-ttu-id="68302-113">Le profileur peut utiliser la méthode [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) pour définir les drapeaux de l’événement.</span><span class="sxs-lookup"><span data-stu-id="68302-113">The profiler can use the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>

## <a name="remarks"></a><span data-ttu-id="68302-114">Notes </span><span class="sxs-lookup"><span data-stu-id="68302-114">Remarks</span></span>  
 <span data-ttu-id="68302-115">Les valeurs `func` et `argumentInfo` les paramètres ne `FunctionEnter2` sont pas valides après le retour de la fonction parce que les valeurs peuvent changer ou être détruites.</span><span class="sxs-lookup"><span data-stu-id="68302-115">The values of the `func` and `argumentInfo` parameters are not valid after the `FunctionEnter2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="68302-116">La `FunctionEnter2` fonction est un rappel; vous devez le mettre en œuvre.</span><span class="sxs-lookup"><span data-stu-id="68302-116">The `FunctionEnter2` function is a callback; you must implement it.</span></span> <span data-ttu-id="68302-117">La mise en `__declspec``naked`œuvre doit utiliser l’attribut de la classe de stockage.</span><span class="sxs-lookup"><span data-stu-id="68302-117">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="68302-118">Le moteur d’exécution n’enregistre aucun registre avant d’appeler cette fonction.</span><span class="sxs-lookup"><span data-stu-id="68302-118">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="68302-119">À l’entrée, vous devez enregistrer tous les registres que vous utilisez, y compris ceux de l’unité à point flottant (FPU).</span><span class="sxs-lookup"><span data-stu-id="68302-119">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="68302-120">À la sortie, vous devez restaurer la pile en sortant de tous les paramètres qui ont été poussés par son appelant.</span><span class="sxs-lookup"><span data-stu-id="68302-120">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="68302-121">La mise `FunctionEnter2` en œuvre de ne devrait pas bloquer parce qu’elle retardera la collecte des ordures.</span><span class="sxs-lookup"><span data-stu-id="68302-121">The implementation of `FunctionEnter2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="68302-122">La mise en œuvre ne devrait pas tenter une collecte des ordures parce que la pile peut ne pas être dans un état de collecte des ordures.</span><span class="sxs-lookup"><span data-stu-id="68302-122">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="68302-123">Si une collecte d’ordures est tentée, le temps d’exécution se bloque jusqu’à ce que `FunctionEnter2` le retour.</span><span class="sxs-lookup"><span data-stu-id="68302-123">If a garbage collection is attempted, the runtime will block until `FunctionEnter2` returns.</span></span>  
  
 <span data-ttu-id="68302-124">En outre, la `FunctionEnter2` fonction ne doit pas appeler dans le code géré ou en aucune façon provoquer une allocation de mémoire gérée.</span><span class="sxs-lookup"><span data-stu-id="68302-124">Also, the `FunctionEnter2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68302-125">Spécifications</span><span class="sxs-lookup"><span data-stu-id="68302-125">Requirements</span></span>  
 <span data-ttu-id="68302-126">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68302-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68302-127">**En-tête:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="68302-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="68302-128">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68302-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68302-129">**.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68302-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68302-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="68302-130">See also</span></span>

- [<span data-ttu-id="68302-131">FunctionLeave2 (fonction)</span><span class="sxs-lookup"><span data-stu-id="68302-131">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="68302-132">FunctionTailcall2 (fonction)</span><span class="sxs-lookup"><span data-stu-id="68302-132">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="68302-133">SetEnterLeaveFunctionHooks2, méthode</span><span class="sxs-lookup"><span data-stu-id="68302-133">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="68302-134">Fonctions statiques globales du profilage</span><span class="sxs-lookup"><span data-stu-id="68302-134">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
