---
title: FunctionIDMapper2, fonction
ms.date: 03/30/2017
api_name:
- FunctionIDMapper2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionIDMapper2
helpviewer_keywords:
- FunctionIDMapper2 function [.NET Framework profiling]
ms.assetid: 466ad51b-8f0c-41d9-81f7-371aac3374cb
topic_type:
- apiref
ms.openlocfilehash: 7aa90b92d129f1269d901f1cbb5c6a0750de9a90
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728535"
---
# <a name="functionidmapper2-function"></a><span data-ttu-id="db833-102">FunctionIDMapper2, fonction</span><span class="sxs-lookup"><span data-stu-id="db833-102">FunctionIDMapper2 Function</span></span>

<span data-ttu-id="db833-103">Notifie le profileur que l’identificateur donné d’une fonction peut être remappé à un autre ID à utiliser dans les rappels [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md)et [FunctionTailcall3](functiontailcall3-function.md), ou[FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md)et [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) pour cette fonction.</span><span class="sxs-lookup"><span data-stu-id="db833-103">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md), and [FunctionTailcall3](functiontailcall3-function.md), or[FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) callbacks for that function.</span></span> <span data-ttu-id="db833-104">`FunctionIDMapper2` permet également au profileur d'indiquer s'il souhaite recevoir des rappels pour cette fonction.</span><span class="sxs-lookup"><span data-stu-id="db833-104">`FunctionIDMapper2` also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db833-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db833-105">Syntax</span></span>  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper2 (  
    [in]  FunctionID  funcId,  
    [in]  void * clientData,  
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db833-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="db833-106">Parameters</span></span>

- `funcId`

  <span data-ttu-id="db833-107">\[in] identificateur de fonction à remapper.</span><span class="sxs-lookup"><span data-stu-id="db833-107">\[in] The function identifier to be remapped.</span></span>

- `clientData`

  <span data-ttu-id="db833-108">\[in] pointeur vers des données qui est utilisé pour lever l’ambiguïté entre les runtimes.</span><span class="sxs-lookup"><span data-stu-id="db833-108">\[in] A pointer to data that is used to disambiguate among runtimes.</span></span>

- `pbHookFunction`

  <span data-ttu-id="db833-109">\[out] pointeur vers une valeur à laquelle le profileur affecte `true` s’il souhaite recevoir `FunctionEnter3` des `FunctionLeave3` rappels,, et `FunctionTailcall3` , ou, `FunctionEnter3WithInfo` `FunctionLeave3WithInfo` et `FunctionTailcall3WithInfo` . sinon, il définit cette valeur sur `false` .</span><span class="sxs-lookup"><span data-stu-id="db833-109">\[out] A pointer to a value that the profiler sets to `true` if it wants to receive `FunctionEnter3`, `FunctionLeave3`, and `FunctionTailcall3`, or `FunctionEnter3WithInfo`, `FunctionLeave3WithInfo`, and `FunctionTailcall3WithInfo` callbacks; otherwise, it sets this value to `false`.</span></span>

## <a name="return-value"></a><span data-ttu-id="db833-110">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="db833-110">Return Value</span></span>  

 <span data-ttu-id="db833-111">Le profileur retourne une valeur que le moteur d'exécution utilise comme autre identificateur de fonction.</span><span class="sxs-lookup"><span data-stu-id="db833-111">The profiler returns a value that the execution engine uses as an alternative function identifier.</span></span> <span data-ttu-id="db833-112">La valeur de retour ne peut pas être null, sauf si `false` est retourné dans `pbHookFunction`.</span><span class="sxs-lookup"><span data-stu-id="db833-112">The return value cannot be null unless `false` is returned in `pbHookFunction`.</span></span> <span data-ttu-id="db833-113">Sinon, une valeur de retour null génère des résultats imprévisibles pouvant aller jusqu'à l'arrêt du processus.</span><span class="sxs-lookup"><span data-stu-id="db833-113">Otherwise, a null return value produces unpredictable results, including possibly halting the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db833-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="db833-114">Remarks</span></span>  

 <span data-ttu-id="db833-115">Cette méthode étend la fonction [FunctionIDMapper](functionidmapper-function.md) avec un paramètre supplémentaire utilisé pour passer les données du client.</span><span class="sxs-lookup"><span data-stu-id="db833-115">This method extends the [FunctionIDMapper](functionidmapper-function.md) function with an additional parameter that is used to pass client data.</span></span> <span data-ttu-id="db833-116">Les données client sont utilisées pour distinguer les différents runtimes.</span><span class="sxs-lookup"><span data-stu-id="db833-116">The client data is used to disambiguate among runtimes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db833-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="db833-117">Requirements</span></span>  

 <span data-ttu-id="db833-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db833-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db833-119">**En-tête :** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="db833-119">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="db833-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="db833-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="db833-121">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db833-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db833-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="db833-122">See also</span></span>

- [<span data-ttu-id="db833-123">ICorProfilerInfo::SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="db833-123">ICorProfilerInfo::SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="db833-124">ICorProfilerInfo3::SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="db833-124">ICorProfilerInfo3::SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="db833-125">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="db833-125">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="db833-126">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="db833-126">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="db833-127">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="db833-127">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="db833-128">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="db833-128">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="db833-129">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="db833-129">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="db833-130">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="db833-130">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="db833-131">Fonctions statiques globales du profilage</span><span class="sxs-lookup"><span data-stu-id="db833-131">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
