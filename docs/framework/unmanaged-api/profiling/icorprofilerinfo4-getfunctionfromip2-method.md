---
title: ICorProfilerInfo4::GetFunctionFromIP2, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetFunctionFromIP2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2
helpviewer_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2 method [.NET Framework profiling]
- GetFunctionFromIP2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 46ff70f4-13e9-40a0-802a-0a40abcfc6a0
topic_type:
- apiref
ms.openlocfilehash: 8ad04a7a6705b961686317c9473b885fb90676ce
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861916"
---
# <a name="icorprofilerinfo4getfunctionfromip2-method"></a><span data-ttu-id="cd9c5-102">ICorProfilerInfo4::GetFunctionFromIP2, méthode</span><span class="sxs-lookup"><span data-stu-id="cd9c5-102">ICorProfilerInfo4::GetFunctionFromIP2 Method</span></span>
<span data-ttu-id="cd9c5-103">Mappe un pointeur d’instruction de code managé à la version recompilée juste-à-temps d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="cd9c5-103">Maps a managed code instruction pointer to the JIT-recompiled version of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd9c5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cd9c5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromIP2(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId,  
    [out] ReJITID *pReJitId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd9c5-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="cd9c5-105">Parameters</span></span>  
 `ip`  
 <span data-ttu-id="cd9c5-106">dans Pointeur d’instruction dans du code managé.</span><span class="sxs-lookup"><span data-stu-id="cd9c5-106">[in] The instruction pointer in managed code.</span></span>  
  
 `pFunctionId`  
 <span data-ttu-id="cd9c5-107">à ID de la fonction.</span><span class="sxs-lookup"><span data-stu-id="cd9c5-107">[out] The function ID.</span></span>  
  
 `pReJitId`  
 <span data-ttu-id="cd9c5-108">à Identité de la version recompilée juste-à-temps de la fonction.</span><span class="sxs-lookup"><span data-stu-id="cd9c5-108">[out] The identity of the JIT-recompiled version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd9c5-109">Notes</span><span class="sxs-lookup"><span data-stu-id="cd9c5-109">Remarks</span></span>  
 <span data-ttu-id="cd9c5-110">`GetFunctionFromIP2` est semblable à `GetFunctionFromIP`, à ceci près qu’elle obtient l’ID recompilé juste-à-temps au lieu de l’ID de fonction de la fonction qui contient l’adresse IP spécifiée.</span><span class="sxs-lookup"><span data-stu-id="cd9c5-110">`GetFunctionFromIP2` is similar to `GetFunctionFromIP`, except that it gets the JIT-recompiled ID instead of the function ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cd9c5-111">`GetFunctionFromIP2` pouvez déclencher un garbage collection, alors que `GetFunctionFromIP` ne le sera pas.</span><span class="sxs-lookup"><span data-stu-id="cd9c5-111">`GetFunctionFromIP2` can trigger a garbage collection, whereas `GetFunctionFromIP` will not.</span></span>  <span data-ttu-id="cd9c5-112">Pour plus d’informations, consultez [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md).</span><span class="sxs-lookup"><span data-stu-id="cd9c5-112">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd9c5-113">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="cd9c5-113">Requirements</span></span>  
 <span data-ttu-id="cd9c5-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd9c5-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd9c5-115">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cd9c5-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cd9c5-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cd9c5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd9c5-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd9c5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd9c5-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cd9c5-118">See also</span></span>

- [<span data-ttu-id="cd9c5-119">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="cd9c5-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
