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
ms.openlocfilehash: 50d16b8036144d6ede349149fa4ae37344064d8b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177018"
---
# <a name="icorprofilerinfo3getfunctionenter3info-method"></a><span data-ttu-id="dac8f-102">ICorProfilerInfo3::GetFunctionEnter3Info, méthode</span><span class="sxs-lookup"><span data-stu-id="dac8f-102">ICorProfilerInfo3::GetFunctionEnter3Info Method</span></span>
<span data-ttu-id="dac8f-103">Fournit le cadre de pile et les informations d’argument de la fonction qui est signalée au profileur par la fonction [FunctionEnter3WithInfo.](functionenter3withinfo-function.md)</span><span class="sxs-lookup"><span data-stu-id="dac8f-103">Provides the stack frame and argument information of the function that is being reported to the profiler by the [FunctionEnter3WithInfo](functionenter3withinfo-function.md) function.</span></span> <span data-ttu-id="dac8f-104">Cette méthode peut être appelée uniquement pendant le rappel de `FunctionEnter3WithInfo`.</span><span class="sxs-lookup"><span data-stu-id="dac8f-104">This method can be called only during the `FunctionEnter3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dac8f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dac8f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionEnter3Info(  
            [in]  FunctionID functionId,
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [in, out] ULONG *pcbArgumentInfo,  
            [out, size_is(*pcbArgumentInfo)]  
                  COR_PRF_FUNCTION_ARGUMENT_INFO *pArgumentInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dac8f-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="dac8f-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="dac8f-107">[in] `FunctionID` de la fonction entrée.</span><span class="sxs-lookup"><span data-stu-id="dac8f-107">[in] The `FunctionID` of the function that is being entered.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="dac8f-108">[in] Handle opaque qui représente des informations sur un frame de pile donné.</span><span class="sxs-lookup"><span data-stu-id="dac8f-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="dac8f-109">Le profileur doit `eltInfo` fournir le même qu’il a été donné par la fonction [FunctionEnter3WithInfo.](functionenter3withinfo-function.md)</span><span class="sxs-lookup"><span data-stu-id="dac8f-109">The profiler should provide the same `eltInfo` that it was given by the [FunctionEnter3WithInfo](functionenter3withinfo-function.md) function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="dac8f-110">[out] Handle opaque qui représente des informations génériques sur un frame de pile donné.</span><span class="sxs-lookup"><span data-stu-id="dac8f-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="dac8f-111">Ce handle est uniquement valide pendant le rappel `FunctionEnter3WithInfo` au cours duquel le profileur a appelé la méthode `GetFunctionEnter3Info`.</span><span class="sxs-lookup"><span data-stu-id="dac8f-111">This handle is valid only during the `FunctionEnter3WithInfo` callback in which the profiler called the `GetFunctionEnter3Info` method.</span></span>  
  
 `pcbArgumentInfo`  
 <span data-ttu-id="dac8f-112">[dans, dehors] Un pointeur sur la taille totale, dans les octets, de la structure [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) (plus toute `pArgumentInfo`structure [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) supplémentaire pour les gammes d’arguments pointées par ).</span><span class="sxs-lookup"><span data-stu-id="dac8f-112">[in, out] A pointer to the total size, in bytes, of the [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) structure (plus any additional [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) structures for the argument ranges pointed to by `pArgumentInfo`).</span></span> <span data-ttu-id="dac8f-113">Si la taille spécifiée est insuffisante, ERROR_INSUFFICIENT_BUFFER est retourné et la taille attendue est stockée dans `pcbArgumentInfo`.</span><span class="sxs-lookup"><span data-stu-id="dac8f-113">If the specified size is not enough, ERROR_INSUFFICIENT_BUFFER is returned and the expected size is stored in `pcbArgumentInfo`.</span></span> <span data-ttu-id="dac8f-114">Pour appeler `GetFunctionEnter3Info` pour récupérer uniquement la valeur attendue pour `*pcbArgumentInfo`, affectez à `*pcbArgumentInfo` la valeur 0 et à `pArgumentInfo` la valeur NULL.</span><span class="sxs-lookup"><span data-stu-id="dac8f-114">To call `GetFunctionEnter3Info` just to retrieve the expected value for `*pcbArgumentInfo`, set `*pcbArgumentInfo`=0 and `pArgumentInfo`=NULL.</span></span>  
  
 `pArgumentInfo`  
 <span data-ttu-id="dac8f-115">[out] Pointeur d’une structure [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) qui décrit l’emplacement des arguments de la fonction en mémoire, dans l’ordre de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="dac8f-115">[out] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) structure that describes the locations of the function's arguments in memory, in left-to-right order.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dac8f-116">Notes </span><span class="sxs-lookup"><span data-stu-id="dac8f-116">Remarks</span></span>  
 <span data-ttu-id="dac8f-117">Le profileur doit allouer suffisamment d'espace à la structure `COR_PRF_FUNCTION_ARGUMENT_INFO` de la fonction inspectée et indiquer la taille dans le paramètre `pcbArgumentInfo`.</span><span class="sxs-lookup"><span data-stu-id="dac8f-117">The profiler must allocate sufficient space for the `COR_PRF_FUNCTION_ARGUMENT_INFO` structure of the function that is being inspected, and must indicate the size in the `pcbArgumentInfo` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dac8f-118">Spécifications</span><span class="sxs-lookup"><span data-stu-id="dac8f-118">Requirements</span></span>  
 <span data-ttu-id="dac8f-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dac8f-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dac8f-120">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dac8f-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dac8f-121">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dac8f-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dac8f-122">**.NET Versions-cadre:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dac8f-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dac8f-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dac8f-123">See also</span></span>

- [<span data-ttu-id="dac8f-124">FonctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="dac8f-124">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="dac8f-125">FonctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="dac8f-125">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="dac8f-126">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="dac8f-126">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="dac8f-127">ICorProfilerInfo3, interface</span><span class="sxs-lookup"><span data-stu-id="dac8f-127">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="dac8f-128">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="dac8f-128">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="dac8f-129">Profilage</span><span class="sxs-lookup"><span data-stu-id="dac8f-129">Profiling</span></span>](index.md)
