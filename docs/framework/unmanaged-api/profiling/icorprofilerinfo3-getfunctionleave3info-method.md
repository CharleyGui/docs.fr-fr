---
title: ICorProfilerInfo3::GetFunctionLeave3Info, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionLeave3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionLeave3Info
helpviewer_keywords:
- GetFunctionLeave3Info method [.NET Framework profiling]
- ICorProfilerInfo3::GetFunctionLeave3Info method [.NET Framework profiling]
ms.assetid: df7083d2-fd43-44c7-9ce5-912c25cef0ff
topic_type:
- apiref
ms.openlocfilehash: bab52d9179d7454cab4a47e1a2bfe80a49b00c2a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502832"
---
# <a name="icorprofilerinfo3getfunctionleave3info-method"></a><span data-ttu-id="3e64d-102">ICorProfilerInfo3::GetFunctionLeave3Info, méthode</span><span class="sxs-lookup"><span data-stu-id="3e64d-102">ICorProfilerInfo3::GetFunctionLeave3Info Method</span></span>
<span data-ttu-id="3e64d-103">Fournit le frame de pile et la valeur de retour de la fonction qui est signalée au profileur par la fonction [FunctionLeave3WithInfo](functionleave3withinfo-function.md) .</span><span class="sxs-lookup"><span data-stu-id="3e64d-103">Provides the stack frame and return value of the function that is being reported to the profiler by the [FunctionLeave3WithInfo function](functionleave3withinfo-function.md) function.</span></span> <span data-ttu-id="3e64d-104">Cette méthode peut être appelée uniquement pendant le rappel de `FunctionLeave3WithInfo`.</span><span class="sxs-lookup"><span data-stu-id="3e64d-104">This method can be called only during the `FunctionLeave3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e64d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3e64d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionLeave3Info(  
            [in]  FunctionID functionId,  
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [out] COR_PRF_FUNCTION_ARGUMENT_RANGE *pRetvalRange);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e64d-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3e64d-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="3e64d-107">dans `FunctionID`De la fonction qui retourne.</span><span class="sxs-lookup"><span data-stu-id="3e64d-107">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="3e64d-108">[in] Handle opaque qui représente des informations sur un frame de pile donné.</span><span class="sxs-lookup"><span data-stu-id="3e64d-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="3e64d-109">Le profileur doit fournir le même `eltInfo` fourni au profileur par la fonction [FunctionLeave3WithInfo](functionleave3withinfo-function.md) .</span><span class="sxs-lookup"><span data-stu-id="3e64d-109">The profiler should provide the same `eltInfo` that was given to the profiler by the [FunctionLeave3WithInfo](functionleave3withinfo-function.md) function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="3e64d-110">[out] Handle opaque qui représente des informations génériques sur un frame de pile donné.</span><span class="sxs-lookup"><span data-stu-id="3e64d-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="3e64d-111">Ce handle est uniquement valide pendant le rappel `FunctionLeave3WithInfo` au cours duquel le profileur a appelé la méthode `GetFunctionLeave3Info`.</span><span class="sxs-lookup"><span data-stu-id="3e64d-111">This handle is valid only during the `FunctionLeave3WithInfo` callback in which the profiler called the `GetFunctionLeave3Info` method.</span></span>  
  
 `pRetvalRange`  
 <span data-ttu-id="3e64d-112">à Pointeur vers une structure [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) qui contient la valeur retournée par la fonction.</span><span class="sxs-lookup"><span data-stu-id="3e64d-112">[out] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) structure that contains the value that is returned from the function.</span></span> <span data-ttu-id="3e64d-113">Pour accéder aux informations de valeur de retour, l' `COR_PRF_ENABLE_FUNCTION_RETVAL` indicateur doit être défini.</span><span class="sxs-lookup"><span data-stu-id="3e64d-113">To access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span></span> <span data-ttu-id="3e64d-114">Le profileur peut utiliser la [méthode ICorProfilerInfo :: SetEventMask](icorprofilerinfo-seteventmask-method.md) pour définir les indicateurs d’événement.</span><span class="sxs-lookup"><span data-stu-id="3e64d-114">The profiler can use the [ICorProfilerInfo::SetEventMask method](icorprofilerinfo-seteventmask-method.md) to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3e64d-115">Notes</span><span class="sxs-lookup"><span data-stu-id="3e64d-115">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e64d-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3e64d-116">Requirements</span></span>  
 <span data-ttu-id="3e64d-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e64d-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e64d-118">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3e64d-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3e64d-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3e64d-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e64d-120">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e64d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e64d-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3e64d-121">See also</span></span>

- [<span data-ttu-id="3e64d-122">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="3e64d-122">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="3e64d-123">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="3e64d-123">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="3e64d-124">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="3e64d-124">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="3e64d-125">ICorProfilerInfo3, interface</span><span class="sxs-lookup"><span data-stu-id="3e64d-125">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="3e64d-126">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="3e64d-126">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="3e64d-127">Profilage</span><span class="sxs-lookup"><span data-stu-id="3e64d-127">Profiling</span></span>](index.md)
