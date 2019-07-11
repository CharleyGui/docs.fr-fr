---
title: ICorProfilerCallback::JITCachedFunctionSearchFinished, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCachedFunctionSearchFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCachedFunctionSearchFinished
helpviewer_keywords:
- JITCachedFunctionSearchFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchFinished method [.NET Framework profiling]
ms.assetid: 3c325c82-cddd-4b00-b3da-e450c36abf62
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 882d3b3c359724688c0fb8fe5e2b567f1d575e76
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782871"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchfinished-method"></a><span data-ttu-id="87c65-102">ICorProfilerCallback::JITCachedFunctionSearchFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="87c65-102">ICorProfilerCallback::JITCachedFunctionSearchFinished Method</span></span>
<span data-ttu-id="87c65-103">Notifie le profileur qu’une recherche est terminée pour une fonction qui a été compilée précédemment à l’aide de Native Image Generator (NGen.exe).</span><span class="sxs-lookup"><span data-stu-id="87c65-103">Notifies the profiler that a search has finished for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87c65-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="87c65-104">Syntax</span></span>  
  
```cpp  
HRESULT JITCachedFunctionSearchFinished(  
    [in] FunctionID        functionId,  
    [in] COR_PRF_JIT_CACHE result);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87c65-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="87c65-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="87c65-106">[in] L’ID de la fonction pour laquelle la recherche a été effectuée.</span><span class="sxs-lookup"><span data-stu-id="87c65-106">[in] The ID of the function for which the search was performed.</span></span>  
  
 `result`  
 <span data-ttu-id="87c65-107">[in] Une valeur de la [COR_PRF_JIT_CACHE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md) énumération qui indique le résultat de la recherche.</span><span class="sxs-lookup"><span data-stu-id="87c65-107">[in] A value of the [COR_PRF_JIT_CACHE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md) enumeration that indicates the result of the search.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87c65-108">Notes</span><span class="sxs-lookup"><span data-stu-id="87c65-108">Remarks</span></span>  
 <span data-ttu-id="87c65-109">Dans le .NET Framework version 2.0, le [ICorProfilerCallback::JITCachedFunctionSearchStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md) et `JITCachedFunctionSearchFinished` rappels ne sont pas effectués pour toutes les fonctions dans les images NGen.</span><span class="sxs-lookup"><span data-stu-id="87c65-109">In the .NET Framework version 2.0, the [ICorProfilerCallback::JITCachedFunctionSearchStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md) and `JITCachedFunctionSearchFinished` callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="87c65-110">Seules les images NGen optimisées pour un profileur généreront des rappels pour toutes les fonctions dans l’image.</span><span class="sxs-lookup"><span data-stu-id="87c65-110">Only NGen images optimized for a profiler will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="87c65-111">Toutefois, en raison de la charge supplémentaire, un profileur doit demander les images NGen optimisées sur le profileur uniquement si elle envisage d’utiliser ces rappels pour forcer une fonction compilée juste-à-temps (JIT).</span><span class="sxs-lookup"><span data-stu-id="87c65-111">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="87c65-112">Sinon, le profileur doit utiliser une stratégie minimale pour la collecte des informations sur la fonction.</span><span class="sxs-lookup"><span data-stu-id="87c65-112">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87c65-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="87c65-113">Requirements</span></span>  
 <span data-ttu-id="87c65-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87c65-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87c65-115">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="87c65-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="87c65-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="87c65-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87c65-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87c65-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87c65-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="87c65-118">See also</span></span>

- [<span data-ttu-id="87c65-119">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="87c65-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
