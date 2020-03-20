---
title: FunctionIDMapper (fonction)
ms.date: 03/30/2017
api_name:
- FunctionIDMapper
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionIDMapper
helpviewer_keywords:
- FunctionIDMapper function [.NET Framework profiling]
ms.assetid: b8205b60-1893-4303-8cff-7ac5a00892aa
topic_type:
- apiref
ms.openlocfilehash: 0cf2014d7007593c51868eff0b488fdab136e362
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175172"
---
# <a name="functionidmapper-function"></a><span data-ttu-id="2e2c1-102">FunctionIDMapper (fonction)</span><span class="sxs-lookup"><span data-stu-id="2e2c1-102">FunctionIDMapper Function</span></span>
<span data-ttu-id="2e2c1-103">Informe le profileur que l’identifiant donné d’une fonction peut être remapped à un ID alternatif à utiliser dans le [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md), et [FunctionTailcall2](functiontailcall2-function.md) rappels pour cette fonction.</span><span class="sxs-lookup"><span data-stu-id="2e2c1-103">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md), and [FunctionTailcall2](functiontailcall2-function.md) callbacks for that function.</span></span> <span data-ttu-id="2e2c1-104">`FunctionIDMapper` permet également au profileur d'indiquer s'il souhaite recevoir des rappels pour cette fonction.</span><span class="sxs-lookup"><span data-stu-id="2e2c1-104">`FunctionIDMapper` also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e2c1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e2c1-105">Syntax</span></span>  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e2c1-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2e2c1-106">Parameters</span></span>

- `funcId`

  <span data-ttu-id="2e2c1-107">\[dans] L’identifiant de fonction à remapped.</span><span class="sxs-lookup"><span data-stu-id="2e2c1-107">\[in] The function identifier to be remapped.</span></span>

- `pbHookFunction`

  <span data-ttu-id="2e2c1-108">\[out] Un pointeur à une valeur `true` que le `FunctionEnter2`profileur fixe à s’il veut recevoir , `FunctionLeave2`, et `FunctionTailcall2` les rappels; autrement, il définit `false`cette valeur à .</span><span class="sxs-lookup"><span data-stu-id="2e2c1-108">\[out] A pointer to a value that the profiler sets to `true` if it wants to receive `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks; otherwise, it sets this value to `false`.</span></span>

## <a name="return-value"></a><span data-ttu-id="2e2c1-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="2e2c1-109">Return Value</span></span>  
 <span data-ttu-id="2e2c1-110">Le profileur retourne une valeur que le moteur d'exécution utilise comme autre identificateur de fonction.</span><span class="sxs-lookup"><span data-stu-id="2e2c1-110">The profiler returns a value that the execution engine uses as an alternative function identifier.</span></span> <span data-ttu-id="2e2c1-111">La valeur de retour ne peut pas être null, sauf si `false` est retourné dans `pbHookFunction`.</span><span class="sxs-lookup"><span data-stu-id="2e2c1-111">The return value cannot be null unless `false` is returned in `pbHookFunction`.</span></span> <span data-ttu-id="2e2c1-112">Dans le cas contraire, une valeur de rendement nul produira des résultats imprévisibles, y compris peut-être arrêter le processus.</span><span class="sxs-lookup"><span data-stu-id="2e2c1-112">Otherwise, a null return value will produce unpredictable results, including possibly halting the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e2c1-113">Notes </span><span class="sxs-lookup"><span data-stu-id="2e2c1-113">Remarks</span></span>  
 <span data-ttu-id="2e2c1-114">La `FunctionIDMapper` fonction est un rappel.</span><span class="sxs-lookup"><span data-stu-id="2e2c1-114">The `FunctionIDMapper` function is a callback.</span></span> <span data-ttu-id="2e2c1-115">Il est implémenté par le profileur pour remap une id de fonction à un autre identifiant qui est plus utile pour le profileur.</span><span class="sxs-lookup"><span data-stu-id="2e2c1-115">It is implemented by the profiler to remap a function ID to some other identifier that is more useful for the profiler.</span></span> <span data-ttu-id="2e2c1-116">Le `FunctionIDMapper` renvoi de l’ID alternatif à utiliser pour une fonction donnée.</span><span class="sxs-lookup"><span data-stu-id="2e2c1-116">The `FunctionIDMapper` returns the alternate ID to be used for any given function.</span></span> <span data-ttu-id="2e2c1-117">Le moteur d’exécution honore alors la demande du profileur en passant cette pièce d’identité `clientData` alternative, `FunctionEnter2` `FunctionLeave2`en `FunctionTailcall2` plus de l’ID de fonction traditionnelle, de retour au profileur dans le paramètre de la , , et les crochets, pour identifier la fonction pour laquelle le crochet est appelé.</span><span class="sxs-lookup"><span data-stu-id="2e2c1-117">The execution engine then honors the profiler's request by passing this alternate ID, in addition to the traditional function ID, back to the profiler in the `clientData` parameter of the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` hooks, to identify the function for which the hook is being called.</span></span>  
  
 <span data-ttu-id="2e2c1-118">Vous pouvez utiliser la méthode [ICorProfilerInfo::SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) `FunctionIDMapper` pour spécifier la mise en œuvre de la fonction.</span><span class="sxs-lookup"><span data-stu-id="2e2c1-118">You can use the [ICorProfilerInfo::SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) method to specify the implementation of the `FunctionIDMapper` function.</span></span> <span data-ttu-id="2e2c1-119">Vous ne `ICorProfilerInfo::SetFunctionIDMapper` pouvez appeler la méthode qu’une seule fois, et nous vous recommandons de le faire dans [l’ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span><span class="sxs-lookup"><span data-stu-id="2e2c1-119">You can call the `ICorProfilerInfo::SetFunctionIDMapper` method only once, and we recommend that you do so in the [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
 <span data-ttu-id="2e2c1-120">Par défaut, on suppose qu’un profileur qui fixe le drapeau COR_PRF_MONITOR_ENTERLEAVE en utilisant [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md), et qui définit les crochets via [ICorProfilerInfo::SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md) ou [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), devrait recevoir le `FunctionEnter2`, `FunctionLeave2`, et `FunctionTailcall2` les rappels pour chaque fonction.</span><span class="sxs-lookup"><span data-stu-id="2e2c1-120">By default, it is assumed that a profiler that sets the COR_PRF_MONITOR_ENTERLEAVE flag by using [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md), and which sets hooks via [ICorProfilerInfo::SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md) or [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), should receive the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks for every function.</span></span> <span data-ttu-id="2e2c1-121">Cependant, les profileurs peuvent mettre en œuvre `FunctionIDMapper` pour éviter `pbHookFunction` `false`sélectivement de recevoir ces rappels pour certaines fonctions en définissant à .</span><span class="sxs-lookup"><span data-stu-id="2e2c1-121">However, profilers may implement `FunctionIDMapper` to selectively avoid receiving these callbacks for certain functions by setting `pbHookFunction` to `false`.</span></span>  
  
 <span data-ttu-id="2e2c1-122">Les profileurs doivent tolérer les cas où plusieurs threads d’une application profilée appellent la même méthode/fonction simultanément.</span><span class="sxs-lookup"><span data-stu-id="2e2c1-122">Profilers should be tolerant of cases where multiple threads of a profiled application are calling the same method/function simultaneously.</span></span> <span data-ttu-id="2e2c1-123">Dans de tels cas, le `FunctionIDMapper` profileur peut `FunctionID`recevoir plusieurs rappels pour la même .</span><span class="sxs-lookup"><span data-stu-id="2e2c1-123">In such cases, the profiler may receive multiple `FunctionIDMapper` callbacks for the same `FunctionID`.</span></span> <span data-ttu-id="2e2c1-124">Le profileur devrait être certain de retourner les mêmes valeurs de ce `FunctionID`rappel quand il est appelé plusieurs fois avec le même .</span><span class="sxs-lookup"><span data-stu-id="2e2c1-124">The profiler should be certain to return the same values from this callback when it is called multiple times with the same `FunctionID`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e2c1-125">Spécifications</span><span class="sxs-lookup"><span data-stu-id="2e2c1-125">Requirements</span></span>  
 <span data-ttu-id="2e2c1-126">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e2c1-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e2c1-127">**En-tête:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="2e2c1-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="2e2c1-128">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2e2c1-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e2c1-129">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e2c1-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e2c1-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e2c1-130">See also</span></span>

- [<span data-ttu-id="2e2c1-131">SetFunctionIDMapper, méthode</span><span class="sxs-lookup"><span data-stu-id="2e2c1-131">SetFunctionIDMapper Method</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="2e2c1-132">FunctionIDMapper2, fonction</span><span class="sxs-lookup"><span data-stu-id="2e2c1-132">FunctionIDMapper2 Function</span></span>](functionidmapper2-function.md)
- [<span data-ttu-id="2e2c1-133">FunctionEnter2 (fonction)</span><span class="sxs-lookup"><span data-stu-id="2e2c1-133">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="2e2c1-134">FunctionLeave2 (fonction)</span><span class="sxs-lookup"><span data-stu-id="2e2c1-134">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="2e2c1-135">FunctionTailcall2 (fonction)</span><span class="sxs-lookup"><span data-stu-id="2e2c1-135">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="2e2c1-136">Fonctions statiques globales du profilage</span><span class="sxs-lookup"><span data-stu-id="2e2c1-136">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
