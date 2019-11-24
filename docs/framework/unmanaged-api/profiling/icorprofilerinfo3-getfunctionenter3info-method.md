---
title: ICorProfilerInfo3::GetFunctionEnter3Info, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionEnter3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionEnter3Info
helpviewer_keywords:
- GetFunctionEnter3Info method [.NET Framework profiling]
- ICorProfilerInfo3::GetFunctionEnter3Info method [.NET Framework profiling]
ms.assetid: 542c7c65-dd56-4651-b76f-5db2465e4a15
topic_type:
- apiref
ms.openlocfilehash: 7e93b92b0b0b4c44955ebc7dfb9d1eb875713c27
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449723"
---
# <a name="icorprofilerinfo3getfunctionenter3info-method"></a><span data-ttu-id="7dcbc-102">ICorProfilerInfo3::GetFunctionEnter3Info, méthode</span><span class="sxs-lookup"><span data-stu-id="7dcbc-102">ICorProfilerInfo3::GetFunctionEnter3Info Method</span></span>
<span data-ttu-id="7dcbc-103">Provides the stack frame and argument information of the function that is being reported to the profiler by the [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) function.</span><span class="sxs-lookup"><span data-stu-id="7dcbc-103">Provides the stack frame and argument information of the function that is being reported to the profiler by the [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) function.</span></span> <span data-ttu-id="7dcbc-104">Cette méthode peut être appelée uniquement pendant le rappel de `FunctionEnter3WithInfo`.</span><span class="sxs-lookup"><span data-stu-id="7dcbc-104">This method can be called only during the `FunctionEnter3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7dcbc-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7dcbc-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionEnter3Info(  
            [in]  FunctionID functionId,   
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [in, out] ULONG *pcbArgumentInfo,  
            [out, size_is(*pcbArgumentInfo)]  
                  COR_PRF_FUNCTION_ARGUMENT_INFO *pArgumentInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7dcbc-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7dcbc-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="7dcbc-107">[in] `FunctionID` de la fonction entrée.</span><span class="sxs-lookup"><span data-stu-id="7dcbc-107">[in] The `FunctionID` of the function that is being entered.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="7dcbc-108">[in] Handle opaque qui représente des informations sur un frame de pile donné.</span><span class="sxs-lookup"><span data-stu-id="7dcbc-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="7dcbc-109">The profiler should provide the same `eltInfo` that it was given by the [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) function.</span><span class="sxs-lookup"><span data-stu-id="7dcbc-109">The profiler should provide the same `eltInfo` that it was given by the [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="7dcbc-110">[out] Handle opaque qui représente des informations génériques sur un frame de pile donné.</span><span class="sxs-lookup"><span data-stu-id="7dcbc-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="7dcbc-111">Ce handle est uniquement valide pendant le rappel `FunctionEnter3WithInfo` au cours duquel le profileur a appelé la méthode `GetFunctionEnter3Info`.</span><span class="sxs-lookup"><span data-stu-id="7dcbc-111">This handle is valid only during the `FunctionEnter3WithInfo` callback in which the profiler called the `GetFunctionEnter3Info` method.</span></span>  
  
 `pcbArgumentInfo`  
 <span data-ttu-id="7dcbc-112">[in, out] A pointer to the total size, in bytes, of the [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) structure (plus any additional [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structures for the argument ranges pointed to by `pArgumentInfo`).</span><span class="sxs-lookup"><span data-stu-id="7dcbc-112">[in, out] A pointer to the total size, in bytes, of the [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) structure (plus any additional [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structures for the argument ranges pointed to by `pArgumentInfo`).</span></span> <span data-ttu-id="7dcbc-113">Si la taille spécifiée est insuffisante, ERROR_INSUFFICIENT_BUFFER est retourné et la taille attendue est stockée dans `pcbArgumentInfo`.</span><span class="sxs-lookup"><span data-stu-id="7dcbc-113">If the specified size is not enough, ERROR_INSUFFICIENT_BUFFER is returned and the expected size is stored in `pcbArgumentInfo`.</span></span> <span data-ttu-id="7dcbc-114">Pour appeler `GetFunctionEnter3Info` pour récupérer uniquement la valeur attendue pour `*pcbArgumentInfo`, affectez à `*pcbArgumentInfo` la valeur 0 et à `pArgumentInfo` la valeur NULL.</span><span class="sxs-lookup"><span data-stu-id="7dcbc-114">To call `GetFunctionEnter3Info` just to retrieve the expected value for `*pcbArgumentInfo`, set `*pcbArgumentInfo`=0 and `pArgumentInfo`=NULL.</span></span>  
  
 `pArgumentInfo`  
 <span data-ttu-id="7dcbc-115">[out] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) structure that describes the locations of the function's arguments in memory, in left-to-right order.</span><span class="sxs-lookup"><span data-stu-id="7dcbc-115">[out] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) structure that describes the locations of the function's arguments in memory, in left-to-right order.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7dcbc-116">Notes</span><span class="sxs-lookup"><span data-stu-id="7dcbc-116">Remarks</span></span>  
 <span data-ttu-id="7dcbc-117">Le profileur doit allouer suffisamment d'espace à la structure `COR_PRF_FUNCTION_ARGUMENT_INFO` de la fonction inspectée et indiquer la taille dans le paramètre `pcbArgumentInfo`.</span><span class="sxs-lookup"><span data-stu-id="7dcbc-117">The profiler must allocate sufficient space for the `COR_PRF_FUNCTION_ARGUMENT_INFO` structure of the function that is being inspected, and must indicate the size in the `pcbArgumentInfo` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7dcbc-118">spécifications</span><span class="sxs-lookup"><span data-stu-id="7dcbc-118">Requirements</span></span>  
 <span data-ttu-id="7dcbc-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7dcbc-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7dcbc-120">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7dcbc-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7dcbc-121">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7dcbc-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7dcbc-122">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7dcbc-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dcbc-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7dcbc-123">See also</span></span>

- [<span data-ttu-id="7dcbc-124">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="7dcbc-124">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="7dcbc-125">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="7dcbc-125">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="7dcbc-126">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="7dcbc-126">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="7dcbc-127">ICorProfilerInfo3, interface</span><span class="sxs-lookup"><span data-stu-id="7dcbc-127">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="7dcbc-128">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="7dcbc-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="7dcbc-129">Profilage</span><span class="sxs-lookup"><span data-stu-id="7dcbc-129">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
