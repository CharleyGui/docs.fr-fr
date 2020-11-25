---
title: ICorProfilerInfo3::SetFunctionIDMapper2, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.SetFunctionIDMapper2 Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::SetFunctionIDMapper2
helpviewer_keywords:
- SetFunctionIDMapper2 method [.NET Framework profiling]
- ICorProfilerInfo3::SetFunctionIDMapper2 method [.NET Framework profiling]
ms.assetid: 8cdb1188-952a-4ba8-9f05-bfebc18cdd29
topic_type:
- apiref
ms.openlocfilehash: 26c26cf204f1a2743f46cfcfdfadbf2c3e3df38e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721567"
---
# <a name="icorprofilerinfo3setfunctionidmapper2-method"></a><span data-ttu-id="45ead-102">ICorProfilerInfo3::SetFunctionIDMapper2, méthode</span><span class="sxs-lookup"><span data-stu-id="45ead-102">ICorProfilerInfo3::SetFunctionIDMapper2 Method</span></span>

<span data-ttu-id="45ead-103">Spécifie la fonction implémentée par le profileur qui sera appelée pour mapper des valeurs `FunctionID` sur d'autres valeurs, qui sont passées aux raccordements d'entrée/sortie de fonction du profileur.</span><span class="sxs-lookup"><span data-stu-id="45ead-103">Specifies the profiler-implemented function that will be called to map `FunctionID` values to alternative values, which are passed to the profiler's function entry/exit hooks.</span></span> <span data-ttu-id="45ead-104">Cette méthode étend la méthode [ICorProfilerInfo :: SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) avec un paramètre de données supplémentaire, que les profileurs peuvent utiliser pour lever l’ambiguïté entre les runtimes.</span><span class="sxs-lookup"><span data-stu-id="45ead-104">This method extends the [ICorProfilerInfo::SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) method with an additional data parameter, which profilers may use to disambiguate among runtimes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45ead-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="45ead-105">Syntax</span></span>  
  
```cpp  
HRESULT SetFunctionIDMapper2(  
       [in] FunctionIDMapper2 *pFunc,  
       [in] void *clientData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="45ead-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="45ead-106">Parameters</span></span>  

 `pFunc`  
 <span data-ttu-id="45ead-107">dans Pointeur vers une implémentation de [FunctionIDMapper2,](functionidmapper2-function.md) qui sera appelée pour mapper les `FunctionID` valeurs à leurs autres valeurs.</span><span class="sxs-lookup"><span data-stu-id="45ead-107">[in] A pointer to a [FunctionIDMapper2](functionidmapper2-function.md) implementation that will be called to map the `FunctionID` values to their alternative values.</span></span>  
  
 `clientData`  
 <span data-ttu-id="45ead-108">dans Pointeur qui est passé à chaque appel de fonction [FunctionIDMapper2,](functionidmapper2-function.md) effectué par le runtime actuel.</span><span class="sxs-lookup"><span data-stu-id="45ead-108">[in] A pointer that is passed to every [FunctionIDMapper2](functionidmapper2-function.md) function call made by the current runtime.</span></span> <span data-ttu-id="45ead-109">Le profileur peut utiliser ces informations pour lever l’ambiguïté entre les runtimes.</span><span class="sxs-lookup"><span data-stu-id="45ead-109">The profiler can use this information to disambiguate among runtimes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="45ead-110">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="45ead-110">Return Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45ead-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="45ead-111">Remarks</span></span>  

 <span data-ttu-id="45ead-112">Les alternatives pour les valeurs FunctionID seront passées aux raccordements d’entrée/sortie de fonction du profileur ([FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md)et [FunctionTailcall3](functiontailcall3-function.md); ou [FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md)et [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)) qui sont spécifiés par la méthode [SetEnterLeaveFunctionHooks3,](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) ou [SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) .</span><span class="sxs-lookup"><span data-stu-id="45ead-112">The alternatives for the FunctionID values will be passed to the profiler's function entry/exit hooks ([FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md), and [FunctionTailcall3](functiontailcall3-function.md); or [FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)) that are specified by the [SetEnterLeaveFunctionHooks3](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) or [SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) method.</span></span>  
  
 <span data-ttu-id="45ead-113">La `FunctionIDMapper2` méthode ne peut être définie qu’une seule fois ; nous vous recommandons de la définir dans le rappel [ICorProfilerCallback :: Initialize](icorprofilercallback-initialize-method.md) .</span><span class="sxs-lookup"><span data-stu-id="45ead-113">The `FunctionIDMapper2` method can be set only once; we recommend that you set it in the [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45ead-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="45ead-114">Requirements</span></span>  

 <span data-ttu-id="45ead-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45ead-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45ead-116">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="45ead-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="45ead-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45ead-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45ead-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45ead-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45ead-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="45ead-119">See also</span></span>

- [<span data-ttu-id="45ead-120">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="45ead-120">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="45ead-121">ICorProfilerInfo3, interface</span><span class="sxs-lookup"><span data-stu-id="45ead-121">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="45ead-122">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="45ead-122">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="45ead-123">Profilage</span><span class="sxs-lookup"><span data-stu-id="45ead-123">Profiling</span></span>](index.md)
