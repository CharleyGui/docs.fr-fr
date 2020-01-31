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
ms.openlocfilehash: ad155c4efb9f11565eeed8bc0a3540311aca4eb7
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866271"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchfinished-method"></a><span data-ttu-id="21366-102">ICorProfilerCallback::JITCachedFunctionSearchFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="21366-102">ICorProfilerCallback::JITCachedFunctionSearchFinished Method</span></span>
<span data-ttu-id="21366-103">Notifie le profileur qu’une recherche est terminée pour une fonction qui a été compilée précédemment à l’aide du générateur d’images natives (NGen. exe).</span><span class="sxs-lookup"><span data-stu-id="21366-103">Notifies the profiler that a search has finished for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21366-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21366-104">Syntax</span></span>  
  
```cpp  
HRESULT JITCachedFunctionSearchFinished(  
    [in] FunctionID        functionId,  
    [in] COR_PRF_JIT_CACHE result);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21366-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="21366-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="21366-106">\[in] ID de la fonction pour laquelle la recherche a été effectuée.</span><span class="sxs-lookup"><span data-stu-id="21366-106">\[in] The ID of the function for which the search was performed.</span></span>

- `result`

  <span data-ttu-id="21366-107">\[in] valeur de l’énumération [COR_PRF_JIT_CACHE](cor-prf-jit-cache-enumeration.md) qui indique le résultat de la recherche.</span><span class="sxs-lookup"><span data-stu-id="21366-107">\[in] A value of the [COR_PRF_JIT_CACHE](cor-prf-jit-cache-enumeration.md) enumeration that indicates the result of the search.</span></span>

## <a name="remarks"></a><span data-ttu-id="21366-108">Notes</span><span class="sxs-lookup"><span data-stu-id="21366-108">Remarks</span></span>  
 <span data-ttu-id="21366-109">Dans la version .NET Framework 2,0, les rappels [ICorProfilerCallback :: JITCachedFunctionSearchStarted](icorprofilercallback-jitcachedfunctionsearchstarted-method.md) et `JITCachedFunctionSearchFinished` ne seront pas effectués pour toutes les fonctions dans les images NGen normales.</span><span class="sxs-lookup"><span data-stu-id="21366-109">In the .NET Framework version 2.0, the [ICorProfilerCallback::JITCachedFunctionSearchStarted](icorprofilercallback-jitcachedfunctionsearchstarted-method.md) and `JITCachedFunctionSearchFinished` callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="21366-110">Seules les images NGen optimisées pour un profileur génèrent des rappels pour toutes les fonctions dans l’image.</span><span class="sxs-lookup"><span data-stu-id="21366-110">Only NGen images optimized for a profiler will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="21366-111">Toutefois, en raison de la surcharge supplémentaire, un profileur doit demander des images NGen optimisées par le profileur uniquement s’il envisage d’utiliser ces rappels pour forcer une fonction à être compilée juste-à-temps (JIT).</span><span class="sxs-lookup"><span data-stu-id="21366-111">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="21366-112">Dans le cas contraire, le profileur doit utiliser une stratégie paresseuse pour la collecte d’informations sur les fonctions.</span><span class="sxs-lookup"><span data-stu-id="21366-112">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21366-113">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="21366-113">Requirements</span></span>  
 <span data-ttu-id="21366-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21366-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21366-115">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="21366-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="21366-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21366-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21366-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21366-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21366-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21366-118">See also</span></span>

- [<span data-ttu-id="21366-119">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="21366-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
