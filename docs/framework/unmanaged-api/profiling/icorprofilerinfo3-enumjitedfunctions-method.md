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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c1b088d138948ed7e9ae5514fb62e37c324427dd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782192"
---
# <a name="icorprofilerinfo3enumjitedfunctions-method"></a><span data-ttu-id="413b9-102">ICorProfilerInfo3::EnumJITedFunctions, méthode</span><span class="sxs-lookup"><span data-stu-id="413b9-102">ICorProfilerInfo3::EnumJITedFunctions Method</span></span>
<span data-ttu-id="413b9-103">Retourne un énumérateur pour toutes les fonctions qui ont été précédemment compilé par JIT.</span><span class="sxs-lookup"><span data-stu-id="413b9-103">Returns an enumerator for all functions that were previously JIT-compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="413b9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="413b9-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="413b9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="413b9-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="413b9-106">[out] Un pointeur vers le [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) énumérateur.</span><span class="sxs-lookup"><span data-stu-id="413b9-106">[out] A pointer to the [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="413b9-107">Notes</span><span class="sxs-lookup"><span data-stu-id="413b9-107">Remarks</span></span>  
 <span data-ttu-id="413b9-108">Cette méthode peut se chevaucher avec `JITCompilation` rappels comme le [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="413b9-108">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="413b9-109">L’énumérateur retourné par cette méthode n’inclut pas les fonctions qui sont chargées à partir d’images natives générées avec Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="413b9-109">The enumerator returned by this method does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="413b9-110">L’énumération retournée inclut uniquement « 0 » pour la valeur de la `COR_PRF_FUNCTION::reJitId` champ.</span><span class="sxs-lookup"><span data-stu-id="413b9-110">The returned enumeration includes only "0" for the value of the `COR_PRF_FUNCTION::reJitId` field.</span></span>  <span data-ttu-id="413b9-111">Si vous avez besoin valide `COR_PRF_FUNCTION::reJitId` valeurs, utilisez le [ICorProfilerInfo4::EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="413b9-111">If you require valid `COR_PRF_FUNCTION::reJitId` values, use the [ICorProfilerInfo4::EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="413b9-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="413b9-112">Requirements</span></span>  
 <span data-ttu-id="413b9-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="413b9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="413b9-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="413b9-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="413b9-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="413b9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="413b9-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="413b9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="413b9-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="413b9-117">See also</span></span>

- [<span data-ttu-id="413b9-118">ICorProfilerInfo3, interface</span><span class="sxs-lookup"><span data-stu-id="413b9-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="413b9-119">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="413b9-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="413b9-120">Profilage</span><span class="sxs-lookup"><span data-stu-id="413b9-120">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
