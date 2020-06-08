---
title: ICorProfilerInfo3::GetFunctionTailcall3Info, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionTailcall3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionTailcall3Info
helpviewer_keywords:
- ICorProfilerInfo3::GetFunctionTailcall3Info method [.NET Framework profiling]
- GetFunctionTailcall3Info method [.NET Framework profiling]
ms.assetid: afdb5ac9-5bf5-4b91-b7cb-f81db23d7da3
topic_type:
- apiref
ms.openlocfilehash: e4d0d9ed07c707e51e5833483b71079f2c330505
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496527"
---
# <a name="icorprofilerinfo3getfunctiontailcall3info-method"></a><span data-ttu-id="a9152-102">ICorProfilerInfo3::GetFunctionTailcall3Info, méthode</span><span class="sxs-lookup"><span data-stu-id="a9152-102">ICorProfilerInfo3::GetFunctionTailcall3Info Method</span></span>
<span data-ttu-id="a9152-103">Fournit le frame de pile de la fonction qui est signalée au profileur par la fonction [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) .</span><span class="sxs-lookup"><span data-stu-id="a9152-103">Provides the stack frame of the function that is being reported to the profiler by the [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) function.</span></span> <span data-ttu-id="a9152-104">Cette méthode peut être appelée uniquement pendant le rappel de `FunctionTailcall3WithInfo`.</span><span class="sxs-lookup"><span data-stu-id="a9152-104">This method can be called only during the `FunctionTailcall3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9152-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a9152-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionTailcall3Info(
            [in]  FunctionID functionId,
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9152-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a9152-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="a9152-107">dans `FunctionID`De la fonction qui retourne.</span><span class="sxs-lookup"><span data-stu-id="a9152-107">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="a9152-108">[in] Handle opaque qui représente des informations sur un frame de pile donné.</span><span class="sxs-lookup"><span data-stu-id="a9152-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="a9152-109">Le profileur doit fournir la même `eltInfo` valeur que celle donnée au profileur par la `FunctionTailcall3WithInfo` fonction.</span><span class="sxs-lookup"><span data-stu-id="a9152-109">The profiler should provide the same `eltInfo` that was given to the profiler by the `FunctionTailcall3WithInfo` function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="a9152-110">[out] Handle opaque qui représente des informations génériques sur un frame de pile donné.</span><span class="sxs-lookup"><span data-stu-id="a9152-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="a9152-111">Ce handle est uniquement valide pendant le rappel `FunctionTailcall3WithInfo` au cours duquel le profileur a appelé la méthode `GetFunctionTailcall3Info`.</span><span class="sxs-lookup"><span data-stu-id="a9152-111">This handle is valid only during the `FunctionTailcall3WithInfo` callback in which the profiler called the `GetFunctionTailcall3Info` method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9152-112">Notes</span><span class="sxs-lookup"><span data-stu-id="a9152-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9152-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a9152-113">Requirements</span></span>  
 <span data-ttu-id="a9152-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9152-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9152-115">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a9152-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a9152-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a9152-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a9152-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9152-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9152-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a9152-118">See also</span></span>

- [<span data-ttu-id="a9152-119">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="a9152-119">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="a9152-120">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="a9152-120">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="a9152-121">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="a9152-121">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="a9152-122">ICorProfilerInfo3, interface</span><span class="sxs-lookup"><span data-stu-id="a9152-122">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="a9152-123">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="a9152-123">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="a9152-124">Profilage</span><span class="sxs-lookup"><span data-stu-id="a9152-124">Profiling</span></span>](index.md)
