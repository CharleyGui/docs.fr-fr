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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 31766fed66368c044b188b5a58452a5e264a25cb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782202"
---
# <a name="icorprofilerinfo2setenterleavefunctionhooks2-method"></a><span data-ttu-id="7827e-102">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2, méthode</span><span class="sxs-lookup"><span data-stu-id="7827e-102">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 Method</span></span>
<span data-ttu-id="7827e-103">Spécifie les fonctions implémentées par le profileur à être appelée sur les versions mises à jour des « entrer », « quitter » et « tailcall » de fonctions managées.</span><span class="sxs-lookup"><span data-stu-id="7827e-103">Specifies profiler-implemented functions to be called on the updated versions of the "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7827e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7827e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks2(  
    [in] FunctionEnter2    *pFuncEnter,  
    [in] FunctionLeave2    *pFuncLeave,  
    [in] FunctionTailcall2 *pFuncTailcall);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7827e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7827e-105">Parameters</span></span>  
 `pFuncEnter`  
 <span data-ttu-id="7827e-106">[in] Un pointeur vers l’implémentation à utiliser comme la [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) rappel.</span><span class="sxs-lookup"><span data-stu-id="7827e-106">[in] A pointer to the implementation to be used as the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="7827e-107">[in] Un pointeur vers l’implémentation à utiliser comme la [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) rappel.</span><span class="sxs-lookup"><span data-stu-id="7827e-107">[in] A pointer to the implementation to be used as the [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="7827e-108">[in] Un pointeur vers l’implémentation à utiliser comme la [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) rappel.</span><span class="sxs-lookup"><span data-stu-id="7827e-108">[in] A pointer to the implementation to be used as the [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7827e-109">Notes</span><span class="sxs-lookup"><span data-stu-id="7827e-109">Remarks</span></span>  
 <span data-ttu-id="7827e-110">Le `SetEnterLeaveFunctionHooks2` méthode est similaire à la [ICorProfilerInfo::SetEnterLeaveFunctionHooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="7827e-110">The `SetEnterLeaveFunctionHooks2` method is similar to the [ICorProfilerInfo::SetEnterLeaveFunctionHooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) method.</span></span> <span data-ttu-id="7827e-111">Utilisez l’ancienne base de données pour spécifier les fonctions à utiliser comme les versions plus récentes de l’entrée/leave/tailcall les rappels et ce dernier pour spécifier les fonctions à utiliser comme les versions antérieures des rappels de l’entrée/leave/tailcall.</span><span class="sxs-lookup"><span data-stu-id="7827e-111">Use the former to specify functions to be used as the newer versions of the enter/leave/tailcall callbacks, and the latter to specify functions to be used as the older versions of the enter/leave/tailcall callbacks.</span></span>  
  
 <span data-ttu-id="7827e-112">Qu’un seul jeu de rappels peut être actif à la fois.</span><span class="sxs-lookup"><span data-stu-id="7827e-112">Only one set of callbacks may be active at a time.</span></span> <span data-ttu-id="7827e-113">Par conséquent, si un profileur appelle `ICorProfilerInfo::SetEnterLeaveFunctionHooks` et `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="7827e-113">Thus, if a profiler calls both `ICorProfilerInfo::SetEnterLeaveFunctionHooks` and `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` is used.</span></span>  
  
 <span data-ttu-id="7827e-114">Le `SetEnterLeaveFunctionHooks2` méthode peut être appelée uniquement à partir du profileur [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) rappel.</span><span class="sxs-lookup"><span data-stu-id="7827e-114">The `SetEnterLeaveFunctionHooks2` method may be called only from the profiler's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7827e-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7827e-115">Requirements</span></span>  
 <span data-ttu-id="7827e-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7827e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7827e-117">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7827e-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7827e-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7827e-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7827e-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7827e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7827e-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7827e-120">See also</span></span>

- [<span data-ttu-id="7827e-121">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="7827e-121">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="7827e-122">ICorProfilerInfo2, interface</span><span class="sxs-lookup"><span data-stu-id="7827e-122">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
