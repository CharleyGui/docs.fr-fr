---
title: ICorProfilerInfo3::EnumJITedFunctions, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.EnumJITedFunctions Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::EnumJITedFunctions
helpviewer_keywords:
- ICorProfilerInfo3::EnumJITedFunctions method [.NET Framework profiling]
- EnumJITedFunctions method [.NET Framework profiling]
ms.assetid: e2847a36-f460-45e2-9b6c-b33b008f40d9
topic_type:
- apiref
ms.openlocfilehash: a22a0de9a20f32ce1c9818bbcf29222a4b331420
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862423"
---
# <a name="icorprofilerinfo3enumjitedfunctions-method"></a><span data-ttu-id="21c87-102">ICorProfilerInfo3::EnumJITedFunctions, méthode</span><span class="sxs-lookup"><span data-stu-id="21c87-102">ICorProfilerInfo3::EnumJITedFunctions Method</span></span>
<span data-ttu-id="21c87-103">Retourne un énumérateur pour toutes les fonctions qui ont été précédemment compilées juste-à-temps.</span><span class="sxs-lookup"><span data-stu-id="21c87-103">Returns an enumerator for all functions that were previously JIT-compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21c87-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21c87-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21c87-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="21c87-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="21c87-106">à Pointeur vers l’énumérateur [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="21c87-106">[out] A pointer to the [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21c87-107">Notes</span><span class="sxs-lookup"><span data-stu-id="21c87-107">Remarks</span></span>  
 <span data-ttu-id="21c87-108">Cette méthode peut se chevaucher avec des rappels `JITCompilation` tels que la méthode [ICorProfilerCallback :: JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="21c87-108">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="21c87-109">L’énumérateur retourné par cette méthode n’inclut pas les fonctions qui sont chargées à partir d’images natives générées avec Ngen. exe.</span><span class="sxs-lookup"><span data-stu-id="21c87-109">The enumerator returned by this method does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="21c87-110">L’énumération retournée comprend uniquement « 0 » pour la valeur du champ `COR_PRF_FUNCTION::reJitId`.</span><span class="sxs-lookup"><span data-stu-id="21c87-110">The returned enumeration includes only "0" for the value of the `COR_PRF_FUNCTION::reJitId` field.</span></span>  <span data-ttu-id="21c87-111">Si vous avez besoin de valeurs `COR_PRF_FUNCTION::reJitId` valides, utilisez la méthode [ICorProfilerInfo4 :: enumjitedfunctions2,](icorprofilerinfo4-enumjitedfunctions2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="21c87-111">If you require valid `COR_PRF_FUNCTION::reJitId` values, use the [ICorProfilerInfo4::EnumJITedFunctions2](icorprofilerinfo4-enumjitedfunctions2-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21c87-112">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="21c87-112">Requirements</span></span>  
 <span data-ttu-id="21c87-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21c87-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21c87-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="21c87-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="21c87-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21c87-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21c87-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21c87-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21c87-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21c87-117">See also</span></span>

- [<span data-ttu-id="21c87-118">ICorProfilerInfo3, interface</span><span class="sxs-lookup"><span data-stu-id="21c87-118">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="21c87-119">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="21c87-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="21c87-120">Profilage</span><span class="sxs-lookup"><span data-stu-id="21c87-120">Profiling</span></span>](index.md)
