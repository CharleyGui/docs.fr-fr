---
title: ICorProfilerCallback::JITCachedFunctionSearchStarted, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCachedFunctionSearchStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCachedFunctionSearchStarted
helpviewer_keywords:
- JITCachedFunctionSearchStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchStarted method [.NET Framework profiling]
ms.assetid: 5cba642c-0d80-48ee-889d-198c5044d821
topic_type:
- apiref
ms.openlocfilehash: 938da4e3b7cc45c24dcac872ab504755116197a0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684016"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchstarted-method"></a><span data-ttu-id="17955-102">ICorProfilerCallback::JITCachedFunctionSearchStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="17955-102">ICorProfilerCallback::JITCachedFunctionSearchStarted Method</span></span>

<span data-ttu-id="17955-103">Notifie le profileur qu’une recherche a démarré pour une fonction qui a été compilée précédemment à l’aide du générateur d’images natives (NGen.exe).</span><span class="sxs-lookup"><span data-stu-id="17955-103">Notifies the profiler that a search has started for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17955-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="17955-104">Syntax</span></span>  
  
```cpp  
HRESULT JITCachedFunctionSearchStarted(  
    [in]  FunctionID functionId,  
    [out] BOOL *pbUseCachedFunction);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17955-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="17955-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="17955-106">\[in] ID de la fonction pour laquelle la recherche est effectuée.</span><span class="sxs-lookup"><span data-stu-id="17955-106">\[in] The ID of the function for which the search is being performed.</span></span>

- `pbUseCachedFunction`

  <span data-ttu-id="17955-107">\[out] `true` si le moteur d’exécution doit utiliser la version mise en cache d’une fonction (si disponible); sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="17955-107">\[out] `true` if the execution engine should use the cached version of a function (if available); otherwise `false`.</span></span> <span data-ttu-id="17955-108">Si la valeur est `false` , le moteur d’exécution exécute une compilation JIT de la fonction au lieu d’une version qui n’est pas compilée juste-à-temps.</span><span class="sxs-lookup"><span data-stu-id="17955-108">If the value is `false`, the execution engine JIT-compiles the function instead of using a version that is not JIT-compiled.</span></span>

## <a name="remarks"></a><span data-ttu-id="17955-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="17955-109">Remarks</span></span>  

 <span data-ttu-id="17955-110">Dans la version de .NET Framework 2,0, les `JITCachedFunctionSearchStarted` rappels de [méthode et ICorProfilerCallback :: JITCachedFunctionSearchFinished](icorprofilercallback-jitcachedfunctionsearchfinished-method.md) ne seront pas effectués pour toutes les fonctions dans les images NGen normales.</span><span class="sxs-lookup"><span data-stu-id="17955-110">In the .NET Framework version 2.0, the `JITCachedFunctionSearchStarted` and [ICorProfilerCallback::JITCachedFunctionSearchFinished Method](icorprofilercallback-jitcachedfunctionsearchfinished-method.md) callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="17955-111">Seules les images NGen optimisées pour un profil génèrent des rappels pour toutes les fonctions dans l’image.</span><span class="sxs-lookup"><span data-stu-id="17955-111">Only NGen images optimized for a profile will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="17955-112">Toutefois, en raison de la surcharge supplémentaire, un profileur doit demander des images NGen optimisées par le profileur uniquement s’il envisage d’utiliser ces rappels pour forcer une fonction à être compilée juste-à-temps (JIT).</span><span class="sxs-lookup"><span data-stu-id="17955-112">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="17955-113">Dans le cas contraire, le profileur doit utiliser une stratégie paresseuse pour la collecte d’informations sur les fonctions.</span><span class="sxs-lookup"><span data-stu-id="17955-113">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
 <span data-ttu-id="17955-114">Les profileurs doivent prendre en charge les cas où plusieurs threads d’une application profilée appellent la même méthode simultanément.</span><span class="sxs-lookup"><span data-stu-id="17955-114">Profilers must support cases where multiple threads of a profiled application are calling the same method simultaneously.</span></span> <span data-ttu-id="17955-115">Par exemple, le thread A appelle `JITCachedFunctionSearchStarted` et le profileur répond en affectant à *pbUseCachedFunction* la valeur false pour forcer la compilation JIT.</span><span class="sxs-lookup"><span data-stu-id="17955-115">For example, thread A calls `JITCachedFunctionSearchStarted` and the profiler responds by setting *pbUseCachedFunction* to FALSE to force JIT compilation.</span></span> <span data-ttu-id="17955-116">Le thread A appelle ensuite [ICorProfilerCallback :: JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) et [ICorProfilerCallback :: JITCompilationFinished](icorprofilercallback-jitcompilationfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="17955-116">Thread A then calls [ICorProfilerCallback::JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) and [ICorProfilerCallback::JITCompilationFinished](icorprofilercallback-jitcompilationfinished-method.md).</span></span>  
  
 <span data-ttu-id="17955-117">Désormais, le thread B appelle `JITCachedFunctionSearchStarted` pour la même fonction.</span><span class="sxs-lookup"><span data-stu-id="17955-117">Now thread B calls `JITCachedFunctionSearchStarted` for the same function.</span></span> <span data-ttu-id="17955-118">Même si le profileur a indiqué son intention de compiler la fonction juste-à-temps, le profileur reçoit le deuxième rappel, car le thread B envoie le rappel avant que le profileur ait répondu à l’appel de thread A à `JITCachedFunctionSearchStarted` .</span><span class="sxs-lookup"><span data-stu-id="17955-118">Even though the profiler has stated its intention to JIT-compile the function, the profiler receives the second callback because thread B sends the callback before the profiler has responded to thread A's call to `JITCachedFunctionSearchStarted`.</span></span> <span data-ttu-id="17955-119">L’ordre dans lequel les threads effectuent des appels dépend de la façon dont les threads sont planifiés.</span><span class="sxs-lookup"><span data-stu-id="17955-119">The order in which the threads make calls depends on how the threads are scheduled.</span></span>  
  
 <span data-ttu-id="17955-120">Quand le profileur reçoit des rappels en double, il doit définir la valeur référencée par `pbUseCachedFunction` à la même valeur pour tous les rappels en double.</span><span class="sxs-lookup"><span data-stu-id="17955-120">When the profiler receives duplicate callbacks, it must set the value referenced by `pbUseCachedFunction` to the same value for all the duplicate callbacks.</span></span> <span data-ttu-id="17955-121">Autrement dit, lorsque `JITCachedFunctionSearchStarted` est appelé plusieurs fois avec la même `functionId` valeur, le profileur doit répondre de la même façon à chaque fois.</span><span class="sxs-lookup"><span data-stu-id="17955-121">That is, when `JITCachedFunctionSearchStarted` is called multiple times with the same `functionId` value, the profiler must respond the same each time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17955-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="17955-122">Requirements</span></span>  

 <span data-ttu-id="17955-123">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17955-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17955-124">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="17955-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="17955-125">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17955-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17955-126">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17955-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17955-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="17955-127">See also</span></span>

- [<span data-ttu-id="17955-128">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="17955-128">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
