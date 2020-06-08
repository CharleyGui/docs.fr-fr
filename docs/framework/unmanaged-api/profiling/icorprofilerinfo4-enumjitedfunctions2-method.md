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
ms.openlocfilehash: 2c4a89d5f96ef572518f25bf58a0005454f8e3f0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496124"
---
# <a name="icorprofilerinfo4enumjitedfunctions2-method"></a><span data-ttu-id="d4467-102">ICorProfilerInfo4::EnumJITedFunctions2, méthode</span><span class="sxs-lookup"><span data-stu-id="d4467-102">ICorProfilerInfo4::EnumJITedFunctions2 Method</span></span>
<span data-ttu-id="d4467-103">Retourne un énumérateur pour toutes les fonctions qui ont été précédemment compilées juste-à-temps et qui ont été recompilées juste-à-temps.</span><span class="sxs-lookup"><span data-stu-id="d4467-103">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span> <span data-ttu-id="d4467-104">Cette méthode remplace la méthode [ICorProfilerInfo3 :: EnumJITedFunctions,](icorprofilerinfo3-enumjitedfunctions-method.md) , qui n’énumère pas les ID recompilés juste-à-temps.</span><span class="sxs-lookup"><span data-stu-id="d4467-104">This method replaces the [ICorProfilerInfo3::EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) method, which does not enumerate JIT-recompiled IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4467-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4467-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4467-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d4467-106">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="d4467-107">à Pointeur vers l’énumérateur [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="d4467-107">[out] A pointer to the [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4467-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="d4467-108">Remarks</span></span>  
 <span data-ttu-id="d4467-109">Cette méthode peut se chevaucher avec `JITCompilation` les rappels tels que la méthode [ICorProfilerCallback :: JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d4467-109">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="d4467-110">L’énumération retournée comprend des valeurs pour le `COR_PRF_FUNCTION::reJitId` champ.</span><span class="sxs-lookup"><span data-stu-id="d4467-110">The returned enumeration includes values for the `COR_PRF_FUNCTION::reJitId` field.</span></span> <span data-ttu-id="d4467-111">La méthode [ICorProfilerInfo3 :: EnumJITedFunctions,](icorprofilerinfo3-enumjitedfunctions-method.md) , que cette méthode remplace, n’énumère pas les ID recompilés juste-à-temps, car le `COR_PRF_FUNCTION::reJitId` champ a toujours la valeur 0.</span><span class="sxs-lookup"><span data-stu-id="d4467-111">The [ICorProfilerInfo3::EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) method, which this method replaces, does not enumerate JIT-recompiled IDs, because the `COR_PRF_FUNCTION::reJitId` field is always set to 0.</span></span> <span data-ttu-id="d4467-112">La `ICorProfilerInfo4::EnumJITedFunctions` méthode énumère les ID recompilés juste-à-temps, car le `COR_PRF_FUNCTION::reJitId` champ est défini correctement.</span><span class="sxs-lookup"><span data-stu-id="d4467-112">The `ICorProfilerInfo4::EnumJITedFunctions` method does enumerate JIT-recompiled IDs, because the `COR_PRF_FUNCTION::reJitId` field is set properly.</span></span> <span data-ttu-id="d4467-113">Notez que la méthode [ICorProfilerInfo4 :: enumjitedfunctions2,](icorprofilerinfo4-enumjitedfunctions2-method.md) peut déclencher un garbage collection, contrairement à la [méthode ICorProfilerInfo3 :: EnumJITedFunctions,](icorprofilerinfo3-enumjitedfunctions-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d4467-113">Note that the [ICorProfilerInfo4::EnumJITedFunctions2](icorprofilerinfo4-enumjitedfunctions2-method.md) method can trigger a garbage collection, whereas [ICorProfilerInfo3::EnumJITedFunctions method](icorprofilerinfo3-enumjitedfunctions-method.md) will not.</span></span>  <span data-ttu-id="d4467-114">Pour plus d’informations, consultez [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md).</span><span class="sxs-lookup"><span data-stu-id="d4467-114">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4467-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d4467-115">Requirements</span></span>  
 <span data-ttu-id="d4467-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4467-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4467-117">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d4467-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d4467-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d4467-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4467-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4467-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4467-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d4467-120">See also</span></span>

- [<span data-ttu-id="d4467-121">EnumJITedFunctions, méthode</span><span class="sxs-lookup"><span data-stu-id="d4467-121">EnumJITedFunctions Method</span></span>](icorprofilerinfo3-enumjitedfunctions-method.md)
- [<span data-ttu-id="d4467-122">ICorProfilerInfo4, interface</span><span class="sxs-lookup"><span data-stu-id="d4467-122">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="d4467-123">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="d4467-123">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="d4467-124">Profilage</span><span class="sxs-lookup"><span data-stu-id="d4467-124">Profiling</span></span>](index.md)
