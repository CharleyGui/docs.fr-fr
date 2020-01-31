---
title: ICorProfilerInfo::SetEnterLeaveFunctionHooks, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetEnterLeaveFunctionHooks
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetEnterLeaveFunctionHooks
helpviewer_keywords:
- SetEnterLeaveFunctionHooks method [.NET Framework profiling]
- ICorProfilerInfo::SetEnterLeaveFunctionHooks method [.NET Framework profiling]
ms.assetid: 72399636-c219-4ffd-8ac8-39432c9d4641
topic_type:
- apiref
ms.openlocfilehash: f7bc1954d11134a4515d2e29e9e0eb1626ae5d26
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863426"
---
# <a name="icorprofilerinfosetenterleavefunctionhooks-method"></a><span data-ttu-id="83275-102">ICorProfilerInfo::SetEnterLeaveFunctionHooks, méthode</span><span class="sxs-lookup"><span data-stu-id="83275-102">ICorProfilerInfo::SetEnterLeaveFunctionHooks Method</span></span>
<span data-ttu-id="83275-103">Spécifie les fonctions implémentées par le profileur à appeler sur les raccordements « Enter », « Leave » et « tailcall » des fonctions managées.</span><span class="sxs-lookup"><span data-stu-id="83275-103">Specifies profiler-implemented functions to be called on "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83275-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83275-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks(  
    [in] FunctionEnter    *pFuncEnter,  
    [in] FunctionLeave    *pFuncLeave,  
    [in] FunctionTailcall *pFuncTailcall);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83275-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="83275-105">Parameters</span></span>  
 `pFuncEnter`  
 <span data-ttu-id="83275-106">dans Pointeur vers l’implémentation à utiliser comme rappel [FunctionEnter](functionenter-function.md) .</span><span class="sxs-lookup"><span data-stu-id="83275-106">[in] A pointer to the implementation to be used as the [FunctionEnter](functionenter-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="83275-107">dans Pointeur vers l’implémentation à utiliser comme rappel [FunctionLeave](functionleave-function.md) .</span><span class="sxs-lookup"><span data-stu-id="83275-107">[in] A pointer to the implementation to be used as the [FunctionLeave](functionleave-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="83275-108">dans Pointeur vers l’implémentation à utiliser comme rappel [FunctionTailcall (](functiontailcall-function.md) .</span><span class="sxs-lookup"><span data-stu-id="83275-108">[in] A pointer to the implementation to be used as the [FunctionTailcall](functiontailcall-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83275-109">Notes</span><span class="sxs-lookup"><span data-stu-id="83275-109">Remarks</span></span>  
 <span data-ttu-id="83275-110">Dans la version de .NET Framework 1,0, chaque pointeur de fonction peut avoir la valeur null pour désactiver ce rappel correspondant.</span><span class="sxs-lookup"><span data-stu-id="83275-110">In the .NET Framework version 1.0, each function pointer can be null to disable that corresponding callback.</span></span>  
  
 <span data-ttu-id="83275-111">Un seul ensemble de rappels peut être actif à la fois.</span><span class="sxs-lookup"><span data-stu-id="83275-111">Only one set of callbacks can be active at a time.</span></span> <span data-ttu-id="83275-112">Ainsi, si un profileur appelle à la fois `SetEnterLeaveFunctionHooks` et [ICorProfilerInfo2 :: SetEnterLeaveFunctionHooks2,](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), `SetEnterLeaveFunctionHooks2` est prioritaire.</span><span class="sxs-lookup"><span data-stu-id="83275-112">Thus, if a profiler calls both `SetEnterLeaveFunctionHooks` and [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), then `SetEnterLeaveFunctionHooks2` takes precedence.</span></span>  
  
 <span data-ttu-id="83275-113">La méthode `SetEnterLeaveFunctionHooks` peut être appelée uniquement à partir du rappel [ICorProfilerCallback :: Initialize](icorprofilercallback-initialize-method.md) du profileur.</span><span class="sxs-lookup"><span data-stu-id="83275-113">The `SetEnterLeaveFunctionHooks` method can be called only from the profiler's [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83275-114">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="83275-114">Requirements</span></span>  
 <span data-ttu-id="83275-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83275-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83275-116">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="83275-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="83275-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83275-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83275-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83275-118">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83275-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="83275-119">See also</span></span>

- [<span data-ttu-id="83275-120">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="83275-120">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
