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
ms.openlocfilehash: 5346792cb2a1309268cb4ba48625aa559777fbaf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176992"
---
# <a name="icorprofilerinfo3getfunctiontailcall3info-method"></a><span data-ttu-id="66c6c-102">ICorProfilerInfo3::GetFunctionTailcall3Info, méthode</span><span class="sxs-lookup"><span data-stu-id="66c6c-102">ICorProfilerInfo3::GetFunctionTailcall3Info Method</span></span>
<span data-ttu-id="66c6c-103">Fournit le cadre de pile de la fonction qui est signalé au profileur par la fonction [FunctionTailcall3WithInfo.](functiontailcall3withinfo-function.md)</span><span class="sxs-lookup"><span data-stu-id="66c6c-103">Provides the stack frame of the function that is being reported to the profiler by the [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) function.</span></span> <span data-ttu-id="66c6c-104">Cette méthode peut être appelée uniquement pendant le rappel de `FunctionTailcall3WithInfo`.</span><span class="sxs-lookup"><span data-stu-id="66c6c-104">This method can be called only during the `FunctionTailcall3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66c6c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66c6c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionTailcall3Info(
            [in]  FunctionID functionId,
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66c6c-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="66c6c-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="66c6c-107">[dans] La `FunctionID` fonction qui revient.</span><span class="sxs-lookup"><span data-stu-id="66c6c-107">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="66c6c-108">[in] Handle opaque qui représente des informations sur un frame de pile donné.</span><span class="sxs-lookup"><span data-stu-id="66c6c-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="66c6c-109">Le profileur doit `eltInfo` fournir la même chose qui `FunctionTailcall3WithInfo` a été donnée au profileur par la fonction.</span><span class="sxs-lookup"><span data-stu-id="66c6c-109">The profiler should provide the same `eltInfo` that was given to the profiler by the `FunctionTailcall3WithInfo` function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="66c6c-110">[out] Handle opaque qui représente des informations génériques sur un frame de pile donné.</span><span class="sxs-lookup"><span data-stu-id="66c6c-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="66c6c-111">Ce handle est uniquement valide pendant le rappel `FunctionTailcall3WithInfo` au cours duquel le profileur a appelé la méthode `GetFunctionTailcall3Info`.</span><span class="sxs-lookup"><span data-stu-id="66c6c-111">This handle is valid only during the `FunctionTailcall3WithInfo` callback in which the profiler called the `GetFunctionTailcall3Info` method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66c6c-112">Notes </span><span class="sxs-lookup"><span data-stu-id="66c6c-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66c6c-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="66c6c-113">Requirements</span></span>  
 <span data-ttu-id="66c6c-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66c6c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66c6c-115">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="66c6c-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="66c6c-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="66c6c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66c6c-117">**.NET Versions-cadre:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66c6c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66c6c-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="66c6c-118">See also</span></span>

- [<span data-ttu-id="66c6c-119">FonctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="66c6c-119">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="66c6c-120">FonctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="66c6c-120">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="66c6c-121">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="66c6c-121">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="66c6c-122">ICorProfilerInfo3, interface</span><span class="sxs-lookup"><span data-stu-id="66c6c-122">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="66c6c-123">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="66c6c-123">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="66c6c-124">Profilage</span><span class="sxs-lookup"><span data-stu-id="66c6c-124">Profiling</span></span>](index.md)
