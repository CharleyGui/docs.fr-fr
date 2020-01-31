---
title: ICorProfilerInfo2::SetEnterLeaveFunctionHooks2, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.SetEnterLeaveFunctionHooks2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2
helpviewer_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
- SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
ms.assetid: 3c26b3e7-f72b-48a5-bf8c-edc122523a4b
topic_type:
- apiref
ms.openlocfilehash: 7eac42e1d8132ca9e6d6c6b43efd43b88c1e5d3d
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868575"
---
# <a name="icorprofilerinfo2setenterleavefunctionhooks2-method"></a><span data-ttu-id="6c9dc-102">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2, méthode</span><span class="sxs-lookup"><span data-stu-id="6c9dc-102">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 Method</span></span>
<span data-ttu-id="6c9dc-103">Spécifie les fonctions implémentées par le profileur à appeler sur les versions mises à jour des raccordements « Enter », « Leave » et « tailcall » des fonctions managées.</span><span class="sxs-lookup"><span data-stu-id="6c9dc-103">Specifies profiler-implemented functions to be called on the updated versions of the "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c9dc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c9dc-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks2(  
    [in] FunctionEnter2    *pFuncEnter,  
    [in] FunctionLeave2    *pFuncLeave,  
    [in] FunctionTailcall2 *pFuncTailcall);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c9dc-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="6c9dc-105">Parameters</span></span>  
 `pFuncEnter`  
 <span data-ttu-id="6c9dc-106">dans Pointeur vers l’implémentation à utiliser comme rappel [FunctionEnter2](functionenter2-function.md) .</span><span class="sxs-lookup"><span data-stu-id="6c9dc-106">[in] A pointer to the implementation to be used as the [FunctionEnter2](functionenter2-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="6c9dc-107">dans Pointeur vers l’implémentation à utiliser comme rappel [FunctionLeave2](functionleave2-function.md) .</span><span class="sxs-lookup"><span data-stu-id="6c9dc-107">[in] A pointer to the implementation to be used as the [FunctionLeave2](functionleave2-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="6c9dc-108">dans Pointeur vers l’implémentation à utiliser comme rappel [FunctionTailcall2](functiontailcall2-function.md) .</span><span class="sxs-lookup"><span data-stu-id="6c9dc-108">[in] A pointer to the implementation to be used as the [FunctionTailcall2](functiontailcall2-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c9dc-109">Notes</span><span class="sxs-lookup"><span data-stu-id="6c9dc-109">Remarks</span></span>  
 <span data-ttu-id="6c9dc-110">La méthode `SetEnterLeaveFunctionHooks2` est semblable à la méthode [ICorProfilerInfo :: SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6c9dc-110">The `SetEnterLeaveFunctionHooks2` method is similar to the [ICorProfilerInfo::SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md) method.</span></span> <span data-ttu-id="6c9dc-111">Utilisez la première pour spécifier les fonctions à utiliser comme versions plus récentes des rappels entrée/sortie/tailcall, et la seconde pour spécifier les fonctions à utiliser comme versions antérieures des rappels entrée/sortie/tailcall.</span><span class="sxs-lookup"><span data-stu-id="6c9dc-111">Use the former to specify functions to be used as the newer versions of the enter/leave/tailcall callbacks, and the latter to specify functions to be used as the older versions of the enter/leave/tailcall callbacks.</span></span>  
  
 <span data-ttu-id="6c9dc-112">Un seul ensemble de rappels peut être actif à la fois.</span><span class="sxs-lookup"><span data-stu-id="6c9dc-112">Only one set of callbacks may be active at a time.</span></span> <span data-ttu-id="6c9dc-113">Ainsi, si un profileur appelle à la fois `ICorProfilerInfo::SetEnterLeaveFunctionHooks` et `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="6c9dc-113">Thus, if a profiler calls both `ICorProfilerInfo::SetEnterLeaveFunctionHooks` and `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` is used.</span></span>  
  
 <span data-ttu-id="6c9dc-114">La méthode `SetEnterLeaveFunctionHooks2` peut être appelée uniquement à partir du rappel [ICorProfilerCallback :: Initialize](icorprofilercallback-initialize-method.md) du profileur.</span><span class="sxs-lookup"><span data-stu-id="6c9dc-114">The `SetEnterLeaveFunctionHooks2` method may be called only from the profiler's [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c9dc-115">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="6c9dc-115">Requirements</span></span>  
 <span data-ttu-id="6c9dc-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c9dc-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c9dc-117">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6c9dc-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6c9dc-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c9dc-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c9dc-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c9dc-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c9dc-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6c9dc-120">See also</span></span>

- [<span data-ttu-id="6c9dc-121">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="6c9dc-121">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="6c9dc-122">ICorProfilerInfo2, interface</span><span class="sxs-lookup"><span data-stu-id="6c9dc-122">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
