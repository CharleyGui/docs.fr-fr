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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 186e85bffbc94b4dd9cdf7add010a0af5b383804
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780893"
---
# <a name="icorprofilerinfo3setfunctionidmapper2-method"></a><span data-ttu-id="fc17b-102">ICorProfilerInfo3::SetFunctionIDMapper2, méthode</span><span class="sxs-lookup"><span data-stu-id="fc17b-102">ICorProfilerInfo3::SetFunctionIDMapper2 Method</span></span>
<span data-ttu-id="fc17b-103">Spécifie la fonction implémentée par le profileur qui sera appelée pour mapper des valeurs `FunctionID` sur d'autres valeurs, qui sont passées aux raccordements d'entrée/sortie de fonction du profileur.</span><span class="sxs-lookup"><span data-stu-id="fc17b-103">Specifies the profiler-implemented function that will be called to map `FunctionID` values to alternative values, which are passed to the profiler's function entry/exit hooks.</span></span> <span data-ttu-id="fc17b-104">Cette méthode étend la [ICorProfilerInfo::SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) méthode avec un paramètre de données supplémentaire, les profileurs peuvent utiliser pour distinguer les différents runtimes.</span><span class="sxs-lookup"><span data-stu-id="fc17b-104">This method extends the [ICorProfilerInfo::SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) method with an additional data parameter, which profilers may use to disambiguate among runtimes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc17b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fc17b-105">Syntax</span></span>  
  
```cpp  
HRESULT SetFunctionIDMapper2(  
       [in] FunctionIDMapper2 *pFunc,  
       [in] void *clientData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc17b-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fc17b-106">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="fc17b-107">[in] Un pointeur vers un [FunctionIDMapper2](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md) implémentation qui sera appelée pour mapper le `FunctionID` valeurs aux autres valeurs.</span><span class="sxs-lookup"><span data-stu-id="fc17b-107">[in] A pointer to a [FunctionIDMapper2](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md) implementation that will be called to map the `FunctionID` values to their alternative values.</span></span>  
  
 `clientData`  
 <span data-ttu-id="fc17b-108">[in] Un pointeur est passé à chaque [FunctionIDMapper2](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md) appel effectué par le runtime en cours de la fonction.</span><span class="sxs-lookup"><span data-stu-id="fc17b-108">[in] A pointer that is passed to every [FunctionIDMapper2](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md) function call made by the current runtime.</span></span> <span data-ttu-id="fc17b-109">Le profileur peut utiliser ces informations pour distinguer les différents runtimes.</span><span class="sxs-lookup"><span data-stu-id="fc17b-109">The profiler can use this information to disambiguate among runtimes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fc17b-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="fc17b-110">Return Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc17b-111">Notes</span><span class="sxs-lookup"><span data-stu-id="fc17b-111">Remarks</span></span>  
 <span data-ttu-id="fc17b-112">Les alternatives pour les valeurs FunctionID seront passées aux raccordements d’entrée/sortie de la fonction du profileur ([FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), et [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) ; ou [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), et [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)) qui sont spécifiées par le [ SetEnterLeaveFunctionHooks3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) ou [SetEnterLeaveFunctionHooks3WithInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="fc17b-112">The alternatives for the FunctionID values will be passed to the profiler's function entry/exit hooks ([FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), and [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md); or [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)) that are specified by the [SetEnterLeaveFunctionHooks3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) or [SetEnterLeaveFunctionHooks3WithInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) method.</span></span>  
  
 <span data-ttu-id="fc17b-113">Le `FunctionIDMapper2` méthode peut être définie qu’une seule fois ; nous vous recommandons de définir le [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) rappel.</span><span class="sxs-lookup"><span data-stu-id="fc17b-113">The `FunctionIDMapper2` method can be set only once; we recommend that you set it in the [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc17b-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="fc17b-114">Requirements</span></span>  
 <span data-ttu-id="fc17b-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc17b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc17b-116">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fc17b-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fc17b-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc17b-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc17b-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc17b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc17b-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fc17b-119">See also</span></span>

- [<span data-ttu-id="fc17b-120">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="fc17b-120">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="fc17b-121">ICorProfilerInfo3, interface</span><span class="sxs-lookup"><span data-stu-id="fc17b-121">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="fc17b-122">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="fc17b-122">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="fc17b-123">Profilage</span><span class="sxs-lookup"><span data-stu-id="fc17b-123">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
