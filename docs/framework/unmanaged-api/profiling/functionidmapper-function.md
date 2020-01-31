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
ms.openlocfilehash: d5bf6626e2c6ba15fa9a5da08bcf2d9052866750
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866942"
---
# <a name="functionidmapper-function"></a><span data-ttu-id="dd5ff-102">FunctionIDMapper (fonction)</span><span class="sxs-lookup"><span data-stu-id="dd5ff-102">FunctionIDMapper Function</span></span>
<span data-ttu-id="dd5ff-103">Notifie le profileur que l’identificateur donné d’une fonction peut être remappé à un autre ID à utiliser dans les rappels [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md)et [FunctionTailcall2](functiontailcall2-function.md) pour cette fonction.</span><span class="sxs-lookup"><span data-stu-id="dd5ff-103">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md), and [FunctionTailcall2](functiontailcall2-function.md) callbacks for that function.</span></span> <span data-ttu-id="dd5ff-104">`FunctionIDMapper` permet également au profileur d'indiquer s'il souhaite recevoir des rappels pour cette fonction.</span><span class="sxs-lookup"><span data-stu-id="dd5ff-104">`FunctionIDMapper` also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd5ff-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dd5ff-105">Syntax</span></span>  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,   
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dd5ff-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="dd5ff-106">Parameters</span></span>

- `funcId`

  <span data-ttu-id="dd5ff-107">\[dans] identificateur de fonction à remapper.</span><span class="sxs-lookup"><span data-stu-id="dd5ff-107">\[in] The function identifier to be remapped.</span></span>

- `pbHookFunction`

  <span data-ttu-id="dd5ff-108">\[out] pointeur vers une valeur que le profileur définit pour `true` s’il souhaite recevoir des rappels `FunctionEnter2`, `FunctionLeave2`et `FunctionTailcall2` ; dans le cas contraire, elle définit cette valeur sur `false`.</span><span class="sxs-lookup"><span data-stu-id="dd5ff-108">\[out] A pointer to a value that the profiler sets to `true` if it wants to receive `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks; otherwise, it sets this value to `false`.</span></span>

## <a name="return-value"></a><span data-ttu-id="dd5ff-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="dd5ff-109">Return Value</span></span>  
 <span data-ttu-id="dd5ff-110">Le profileur retourne une valeur que le moteur d'exécution utilise comme autre identificateur de fonction.</span><span class="sxs-lookup"><span data-stu-id="dd5ff-110">The profiler returns a value that the execution engine uses as an alternative function identifier.</span></span> <span data-ttu-id="dd5ff-111">La valeur de retour ne peut pas être null, sauf si `false` est retourné dans `pbHookFunction`.</span><span class="sxs-lookup"><span data-stu-id="dd5ff-111">The return value cannot be null unless `false` is returned in `pbHookFunction`.</span></span> <span data-ttu-id="dd5ff-112">Sinon, une valeur de retour NULL produira des résultats imprévisibles, y compris éventuellement l’arrêt du processus.</span><span class="sxs-lookup"><span data-stu-id="dd5ff-112">Otherwise, a null return value will produce unpredictable results, including possibly halting the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd5ff-113">Notes</span><span class="sxs-lookup"><span data-stu-id="dd5ff-113">Remarks</span></span>  
 <span data-ttu-id="dd5ff-114">La fonction `FunctionIDMapper` est un rappel.</span><span class="sxs-lookup"><span data-stu-id="dd5ff-114">The `FunctionIDMapper` function is a callback.</span></span> <span data-ttu-id="dd5ff-115">Elle est implémentée par le profileur pour remapper un ID de fonction à un autre identificateur qui est plus utile pour le profileur.</span><span class="sxs-lookup"><span data-stu-id="dd5ff-115">It is implemented by the profiler to remap a function ID to some other identifier that is more useful for the profiler.</span></span> <span data-ttu-id="dd5ff-116">Le `FunctionIDMapper` retourne l’ID de remplacement à utiliser pour toute fonction donnée.</span><span class="sxs-lookup"><span data-stu-id="dd5ff-116">The `FunctionIDMapper` returns the alternate ID to be used for any given function.</span></span> <span data-ttu-id="dd5ff-117">Le moteur d’exécution honore ensuite la requête du profileur en passant cet ID alternatif, en plus de l’ID de fonction traditionnel, dans le profileur dans le paramètre `clientData` des crochets `FunctionEnter2`, `FunctionLeave2`et `FunctionTailcall2`, afin d’identifier la fonction pour laquelle le hook est appelé.</span><span class="sxs-lookup"><span data-stu-id="dd5ff-117">The execution engine then honors the profiler's request by passing this alternate ID, in addition to the traditional function ID, back to the profiler in the `clientData` parameter of the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` hooks, to identify the function for which the hook is being called.</span></span>  
  
 <span data-ttu-id="dd5ff-118">Vous pouvez utiliser la méthode [ICorProfilerInfo :: SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) pour spécifier l’implémentation de la fonction `FunctionIDMapper`.</span><span class="sxs-lookup"><span data-stu-id="dd5ff-118">You can use the [ICorProfilerInfo::SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) method to specify the implementation of the `FunctionIDMapper` function.</span></span> <span data-ttu-id="dd5ff-119">Vous pouvez appeler la méthode `ICorProfilerInfo::SetFunctionIDMapper` une seule fois, et nous vous recommandons de le faire dans le rappel [ICorProfilerCallback :: Initialize](icorprofilercallback-initialize-method.md) .</span><span class="sxs-lookup"><span data-stu-id="dd5ff-119">You can call the `ICorProfilerInfo::SetFunctionIDMapper` method only once, and we recommend that you do so in the [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
 <span data-ttu-id="dd5ff-120">Par défaut, il est supposé qu’un profileur qui définit l’indicateur COR_PRF_MONITOR_ENTERLEAVE à l’aide de [ICorProfilerInfo :: SetEventMask](icorprofilerinfo-seteventmask-method.md)et qui définit des raccordements via [ICorProfilerInfo :: SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md) ou [ICorProfilerInfo2 :: SetEnterLeaveFunctionHooks2,](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), doit recevoir les rappels `FunctionEnter2`, `FunctionLeave2`et `FunctionTailcall2` pour chaque fonction.</span><span class="sxs-lookup"><span data-stu-id="dd5ff-120">By default, it is assumed that a profiler that sets the COR_PRF_MONITOR_ENTERLEAVE flag by using [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md), and which sets hooks via [ICorProfilerInfo::SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md) or [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), should receive the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks for every function.</span></span> <span data-ttu-id="dd5ff-121">Toutefois, les profileurs peuvent implémenter `FunctionIDMapper` pour ne pas recevoir de manière sélective ces rappels pour certaines fonctions en définissant `pbHookFunction` sur `false`.</span><span class="sxs-lookup"><span data-stu-id="dd5ff-121">However, profilers may implement `FunctionIDMapper` to selectively avoid receiving these callbacks for certain functions by setting `pbHookFunction` to `false`.</span></span>  
  
 <span data-ttu-id="dd5ff-122">Les profileurs doivent être tolérants dans les cas où plusieurs threads d’une application profilée appellent la même méthode/fonction simultanément.</span><span class="sxs-lookup"><span data-stu-id="dd5ff-122">Profilers should be tolerant of cases where multiple threads of a profiled application are calling the same method/function simultaneously.</span></span> <span data-ttu-id="dd5ff-123">Dans ce cas, le profileur peut recevoir plusieurs rappels de `FunctionIDMapper` pour le même `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="dd5ff-123">In such cases, the profiler may receive multiple `FunctionIDMapper` callbacks for the same `FunctionID`.</span></span> <span data-ttu-id="dd5ff-124">Le profileur doit être certain de retourner les mêmes valeurs à partir de ce rappel lorsqu’il est appelé plusieurs fois avec le même `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="dd5ff-124">The profiler should be certain to return the same values from this callback when it is called multiple times with the same `FunctionID`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd5ff-125">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="dd5ff-125">Requirements</span></span>  
 <span data-ttu-id="dd5ff-126">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd5ff-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd5ff-127">**En-tête :** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="dd5ff-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="dd5ff-128">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dd5ff-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dd5ff-129">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd5ff-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd5ff-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dd5ff-130">See also</span></span>

- [<span data-ttu-id="dd5ff-131">SetFunctionIDMapper, méthode</span><span class="sxs-lookup"><span data-stu-id="dd5ff-131">SetFunctionIDMapper Method</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="dd5ff-132">FunctionIDMapper2, fonction</span><span class="sxs-lookup"><span data-stu-id="dd5ff-132">FunctionIDMapper2 Function</span></span>](functionidmapper2-function.md)
- [<span data-ttu-id="dd5ff-133">FunctionEnter2, fonction</span><span class="sxs-lookup"><span data-stu-id="dd5ff-133">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="dd5ff-134">FunctionLeave2, fonction</span><span class="sxs-lookup"><span data-stu-id="dd5ff-134">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="dd5ff-135">FunctionTailcall2, fonction</span><span class="sxs-lookup"><span data-stu-id="dd5ff-135">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="dd5ff-136">Fonctions statiques globales de profilage</span><span class="sxs-lookup"><span data-stu-id="dd5ff-136">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
