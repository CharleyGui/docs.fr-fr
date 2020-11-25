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
ms.openlocfilehash: a522df8abfba1c5837e3136f966935ff1f56d8d2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721541"
---
# <a name="icorprofilerinfo4getfunctionfromip2-method"></a><span data-ttu-id="1348c-102">ICorProfilerInfo4::GetFunctionFromIP2, méthode</span><span class="sxs-lookup"><span data-stu-id="1348c-102">ICorProfilerInfo4::GetFunctionFromIP2 Method</span></span>

<span data-ttu-id="1348c-103">Mappe un pointeur d’instruction de code managé à la version recompilée juste-à-temps d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="1348c-103">Maps a managed code instruction pointer to the JIT-recompiled version of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1348c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1348c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromIP2(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId,  
    [out] ReJITID *pReJitId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1348c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1348c-105">Parameters</span></span>  

 `ip`  
 <span data-ttu-id="1348c-106">dans Pointeur d’instruction dans du code managé.</span><span class="sxs-lookup"><span data-stu-id="1348c-106">[in] The instruction pointer in managed code.</span></span>  
  
 `pFunctionId`  
 <span data-ttu-id="1348c-107">à ID de la fonction.</span><span class="sxs-lookup"><span data-stu-id="1348c-107">[out] The function ID.</span></span>  
  
 `pReJitId`  
 <span data-ttu-id="1348c-108">à Identité de la version recompilée juste-à-temps de la fonction.</span><span class="sxs-lookup"><span data-stu-id="1348c-108">[out] The identity of the JIT-recompiled version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1348c-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="1348c-109">Remarks</span></span>  

 <span data-ttu-id="1348c-110">`GetFunctionFromIP2` est semblable à `GetFunctionFromIP` , à ceci près qu’il obtient l’ID recompilé juste-à-temps au lieu de l’ID de fonction de la fonction qui contient l’adresse IP spécifiée.</span><span class="sxs-lookup"><span data-stu-id="1348c-110">`GetFunctionFromIP2` is similar to `GetFunctionFromIP`, except that it gets the JIT-recompiled ID instead of the function ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1348c-111">`GetFunctionFromIP2` peut déclencher un garbage collection, contrairement à `GetFunctionFromIP` .</span><span class="sxs-lookup"><span data-stu-id="1348c-111">`GetFunctionFromIP2` can trigger a garbage collection, whereas `GetFunctionFromIP` will not.</span></span>  <span data-ttu-id="1348c-112">Pour plus d’informations, consultez [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md).</span><span class="sxs-lookup"><span data-stu-id="1348c-112">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1348c-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1348c-113">Requirements</span></span>  

 <span data-ttu-id="1348c-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1348c-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1348c-115">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1348c-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1348c-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1348c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1348c-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1348c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1348c-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1348c-118">See also</span></span>

- [<span data-ttu-id="1348c-119">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="1348c-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
