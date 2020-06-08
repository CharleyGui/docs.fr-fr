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
ms.openlocfilehash: cf0726a12b0274fd7a38e82b66c33430d26b031a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497450"
---
# <a name="icorprofilerinfosetenterleavefunctionhooks-method"></a><span data-ttu-id="27a96-102">ICorProfilerInfo::SetEnterLeaveFunctionHooks, méthode</span><span class="sxs-lookup"><span data-stu-id="27a96-102">ICorProfilerInfo::SetEnterLeaveFunctionHooks Method</span></span>
<span data-ttu-id="27a96-103">Spécifie les fonctions implémentées par le profileur à appeler sur les raccordements « Enter », « Leave » et « tailcall » des fonctions managées.</span><span class="sxs-lookup"><span data-stu-id="27a96-103">Specifies profiler-implemented functions to be called on "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27a96-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27a96-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks(  
    [in] FunctionEnter    *pFuncEnter,  
    [in] FunctionLeave    *pFuncLeave,  
    [in] FunctionTailcall *pFuncTailcall);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27a96-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="27a96-105">Parameters</span></span>  
 `pFuncEnter`  
 <span data-ttu-id="27a96-106">dans Pointeur vers l’implémentation à utiliser comme rappel [FunctionEnter](functionenter-function.md) .</span><span class="sxs-lookup"><span data-stu-id="27a96-106">[in] A pointer to the implementation to be used as the [FunctionEnter](functionenter-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="27a96-107">dans Pointeur vers l’implémentation à utiliser comme rappel [FunctionLeave](functionleave-function.md) .</span><span class="sxs-lookup"><span data-stu-id="27a96-107">[in] A pointer to the implementation to be used as the [FunctionLeave](functionleave-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="27a96-108">dans Pointeur vers l’implémentation à utiliser comme rappel [FunctionTailcall (](functiontailcall-function.md) .</span><span class="sxs-lookup"><span data-stu-id="27a96-108">[in] A pointer to the implementation to be used as the [FunctionTailcall](functiontailcall-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27a96-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="27a96-109">Remarks</span></span>  
 <span data-ttu-id="27a96-110">Dans la version de .NET Framework 1,0, chaque pointeur de fonction peut avoir la valeur null pour désactiver ce rappel correspondant.</span><span class="sxs-lookup"><span data-stu-id="27a96-110">In the .NET Framework version 1.0, each function pointer can be null to disable that corresponding callback.</span></span>  
  
 <span data-ttu-id="27a96-111">Un seul ensemble de rappels peut être actif à la fois.</span><span class="sxs-lookup"><span data-stu-id="27a96-111">Only one set of callbacks can be active at a time.</span></span> <span data-ttu-id="27a96-112">Ainsi, si un profileur appelle à la fois `SetEnterLeaveFunctionHooks` et [ICorProfilerInfo2 :: SetEnterLeaveFunctionHooks2,](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), `SetEnterLeaveFunctionHooks2` est prioritaire.</span><span class="sxs-lookup"><span data-stu-id="27a96-112">Thus, if a profiler calls both `SetEnterLeaveFunctionHooks` and [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), then `SetEnterLeaveFunctionHooks2` takes precedence.</span></span>  
  
 <span data-ttu-id="27a96-113">La `SetEnterLeaveFunctionHooks` méthode peut être appelée uniquement à partir du rappel [ICorProfilerCallback :: Initialize](icorprofilercallback-initialize-method.md) du profileur.</span><span class="sxs-lookup"><span data-stu-id="27a96-113">The `SetEnterLeaveFunctionHooks` method can be called only from the profiler's [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27a96-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="27a96-114">Requirements</span></span>  
 <span data-ttu-id="27a96-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27a96-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27a96-116">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="27a96-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="27a96-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="27a96-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27a96-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27a96-118">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27a96-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="27a96-119">See also</span></span>

- [<span data-ttu-id="27a96-120">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="27a96-120">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
