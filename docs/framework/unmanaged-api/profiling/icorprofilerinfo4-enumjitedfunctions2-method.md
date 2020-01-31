---
title: ICorProfilerInfo4::EnumJITedFunctions2, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.EnumJITedFunctions2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::EnumJITedFunctions2
helpviewer_keywords:
- EnumJITedFunctions2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::EnumJITedFunctions2 method [.NET Framework profiling]
ms.assetid: 40e9a1be-9bd2-4fad-9921-34a84b61c1e3
topic_type:
- apiref
ms.openlocfilehash: 3903ebf1ad35bd7eb1ba49b4f1acda9024678423
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862202"
---
# <a name="icorprofilerinfo4enumjitedfunctions2-method"></a><span data-ttu-id="577db-102">ICorProfilerInfo4::EnumJITedFunctions2, méthode</span><span class="sxs-lookup"><span data-stu-id="577db-102">ICorProfilerInfo4::EnumJITedFunctions2 Method</span></span>
<span data-ttu-id="577db-103">Retourne un énumérateur pour toutes les fonctions qui ont été précédemment compilées juste-à-temps et qui ont été recompilées juste-à-temps.</span><span class="sxs-lookup"><span data-stu-id="577db-103">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span> <span data-ttu-id="577db-104">Cette méthode remplace la méthode [ICorProfilerInfo3 :: EnumJITedFunctions,](icorprofilerinfo3-enumjitedfunctions-method.md) , qui n’énumère pas les ID recompilés juste-à-temps.</span><span class="sxs-lookup"><span data-stu-id="577db-104">This method replaces the [ICorProfilerInfo3::EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) method, which does not enumerate JIT-recompiled IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="577db-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="577db-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="577db-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="577db-106">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="577db-107">à Pointeur vers l’énumérateur [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="577db-107">[out] A pointer to the [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="577db-108">Notes</span><span class="sxs-lookup"><span data-stu-id="577db-108">Remarks</span></span>  
 <span data-ttu-id="577db-109">Cette méthode peut se chevaucher avec des rappels `JITCompilation` tels que la méthode [ICorProfilerCallback :: JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="577db-109">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="577db-110">L’énumération retournée comprend des valeurs pour le champ `COR_PRF_FUNCTION::reJitId`.</span><span class="sxs-lookup"><span data-stu-id="577db-110">The returned enumeration includes values for the `COR_PRF_FUNCTION::reJitId` field.</span></span> <span data-ttu-id="577db-111">La méthode [ICorProfilerInfo3 :: EnumJITedFunctions,](icorprofilerinfo3-enumjitedfunctions-method.md) , que cette méthode remplace, n’énumère pas les ID recompilés juste-à-temps, car le champ `COR_PRF_FUNCTION::reJitId` a toujours la valeur 0.</span><span class="sxs-lookup"><span data-stu-id="577db-111">The [ICorProfilerInfo3::EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) method, which this method replaces, does not enumerate JIT-recompiled IDs, because the `COR_PRF_FUNCTION::reJitId` field is always set to 0.</span></span> <span data-ttu-id="577db-112">La méthode `ICorProfilerInfo4::EnumJITedFunctions` énumère les ID recompilés juste-à-temps, car le champ `COR_PRF_FUNCTION::reJitId` est correctement défini.</span><span class="sxs-lookup"><span data-stu-id="577db-112">The `ICorProfilerInfo4::EnumJITedFunctions` method does enumerate JIT-recompiled IDs, because the `COR_PRF_FUNCTION::reJitId` field is set properly.</span></span> <span data-ttu-id="577db-113">Notez que la méthode [ICorProfilerInfo4 :: enumjitedfunctions2,](icorprofilerinfo4-enumjitedfunctions2-method.md) peut déclencher un garbage collection, contrairement à la [méthode ICorProfilerInfo3 :: EnumJITedFunctions,](icorprofilerinfo3-enumjitedfunctions-method.md) .</span><span class="sxs-lookup"><span data-stu-id="577db-113">Note that the [ICorProfilerInfo4::EnumJITedFunctions2](icorprofilerinfo4-enumjitedfunctions2-method.md) method can trigger a garbage collection, whereas [ICorProfilerInfo3::EnumJITedFunctions method](icorprofilerinfo3-enumjitedfunctions-method.md) will not.</span></span>  <span data-ttu-id="577db-114">Pour plus d’informations, consultez [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md).</span><span class="sxs-lookup"><span data-stu-id="577db-114">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="577db-115">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="577db-115">Requirements</span></span>  
 <span data-ttu-id="577db-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="577db-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="577db-117">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="577db-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="577db-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="577db-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="577db-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="577db-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="577db-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="577db-120">See also</span></span>

- [<span data-ttu-id="577db-121">EnumJITedFunctions, méthode</span><span class="sxs-lookup"><span data-stu-id="577db-121">EnumJITedFunctions Method</span></span>](icorprofilerinfo3-enumjitedfunctions-method.md)
- [<span data-ttu-id="577db-122">ICorProfilerInfo4, interface</span><span class="sxs-lookup"><span data-stu-id="577db-122">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="577db-123">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="577db-123">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="577db-124">Profilage</span><span class="sxs-lookup"><span data-stu-id="577db-124">Profiling</span></span>](index.md)
