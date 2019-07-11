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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f4d35179b8ae35c03370cc3798609d6ed430cde3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782855"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchstarted-method"></a><span data-ttu-id="11818-102">ICorProfilerCallback::JITCachedFunctionSearchStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="11818-102">ICorProfilerCallback::JITCachedFunctionSearchStarted Method</span></span>
<span data-ttu-id="11818-103">Notifie le profileur qu’une recherche a démarré pour une fonction qui a été compilée précédemment à l’aide de Native Image Generator (NGen.exe).</span><span class="sxs-lookup"><span data-stu-id="11818-103">Notifies the profiler that a search has started for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11818-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11818-104">Syntax</span></span>  
  
```cpp  
HRESULT JITCachedFunctionSearchStarted(  
    [in]  FunctionID functionId,  
    [out] BOOL *pbUseCachedFunction);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11818-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="11818-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="11818-106">[in] L’ID de la fonction pour laquelle la recherche est effectuée.</span><span class="sxs-lookup"><span data-stu-id="11818-106">[in] The ID of the function for which the search is being performed.</span></span>  
  
 `pbUseCachedFunction`  
 <span data-ttu-id="11818-107">[out] `true` si le moteur d’exécution doit utiliser la version mise en cache d’une fonction (si disponible) ; sinon `false`.</span><span class="sxs-lookup"><span data-stu-id="11818-107">[out] `true` if the execution engine should use the cached version of a function (if available); otherwise `false`.</span></span> <span data-ttu-id="11818-108">Si la valeur est `false`, le moteur d’exécution JIT-compile la fonction au lieu d’utiliser une version qui n’est pas compilé par JIT.</span><span class="sxs-lookup"><span data-stu-id="11818-108">If the value is `false`, the execution engine JIT-compiles the function instead of using a version that is not JIT-compiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11818-109">Notes</span><span class="sxs-lookup"><span data-stu-id="11818-109">Remarks</span></span>  
 <span data-ttu-id="11818-110">Dans le .NET Framework version 2.0, le `JITCachedFunctionSearchStarted` et [ICorProfilerCallback::JITCachedFunctionSearchFinished, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md) rappels ne sont pas effectués pour toutes les fonctions dans les images NGen.</span><span class="sxs-lookup"><span data-stu-id="11818-110">In the .NET Framework version 2.0, the `JITCachedFunctionSearchStarted` and [ICorProfilerCallback::JITCachedFunctionSearchFinished Method](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md) callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="11818-111">Seules les images NGen optimisées pour un profil généreront des rappels pour toutes les fonctions dans l’image.</span><span class="sxs-lookup"><span data-stu-id="11818-111">Only NGen images optimized for a profile will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="11818-112">Toutefois, en raison de la charge supplémentaire, un profileur doit demander les images NGen optimisées sur le profileur uniquement si elle envisage d’utiliser ces rappels pour forcer une fonction compilée juste-à-temps (JIT).</span><span class="sxs-lookup"><span data-stu-id="11818-112">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="11818-113">Sinon, le profileur doit utiliser une stratégie minimale pour la collecte des informations sur la fonction.</span><span class="sxs-lookup"><span data-stu-id="11818-113">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
 <span data-ttu-id="11818-114">Les profileurs doivent prendre en charge les cas où plusieurs threads d’une application profilée appellent simultanément la même méthode.</span><span class="sxs-lookup"><span data-stu-id="11818-114">Profilers must support cases where multiple threads of a profiled application are calling the same method simultaneously.</span></span> <span data-ttu-id="11818-115">Par exemple, le thread A appelle `JITCachedFunctionSearchStarted` et le profileur répond en définissant *pbUseCachedFunction*sur FALSE pour forcer la compilation JIT.</span><span class="sxs-lookup"><span data-stu-id="11818-115">For example, thread A calls `JITCachedFunctionSearchStarted` and the profiler responds by setting *pbUseCachedFunction*to FALSE to force JIT compilation.</span></span> <span data-ttu-id="11818-116">Thread appelle un puis [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) et [ICorProfilerCallback::JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="11818-116">Thread A then calls [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) and [ICorProfilerCallback::JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md).</span></span>  
  
 <span data-ttu-id="11818-117">Maintenant, le thread B appelle `JITCachedFunctionSearchStarted` pour la même fonction.</span><span class="sxs-lookup"><span data-stu-id="11818-117">Now thread B calls `JITCachedFunctionSearchStarted` for the same function.</span></span> <span data-ttu-id="11818-118">Bien que le profileur a annoncé son intention juste-à la fonction, le profileur reçoit le deuxième rappel, car le thread B envoie le rappel avant que le profileur a répondu à l’appel de thread de A à `JITCachedFunctionSearchStarted`.</span><span class="sxs-lookup"><span data-stu-id="11818-118">Even though the profiler has stated its intention to JIT-compile the function, the profiler receives the second callback because thread B sends the callback before the profiler has responded to thread A's call to `JITCachedFunctionSearchStarted`.</span></span> <span data-ttu-id="11818-119">L’ordre dans lequel les threads effectuent des appels dépend de la façon dont les threads sont planifiés.</span><span class="sxs-lookup"><span data-stu-id="11818-119">The order in which the threads make calls depends on how the threads are scheduled.</span></span>  
  
 <span data-ttu-id="11818-120">Lorsque le profileur reçoit des rappels en double, il doit définir la valeur référencée par `pbUseCachedFunction` sur la même valeur pour tous les rappels en double.</span><span class="sxs-lookup"><span data-stu-id="11818-120">When the profiler receives duplicate callbacks, it must set the value referenced by `pbUseCachedFunction` to the same value for all the duplicate callbacks.</span></span> <span data-ttu-id="11818-121">Autrement dit, lorsque `JITCachedFunctionSearchStarted` est appelée plusieurs fois avec le même `functionId` valeur, le profileur doit répondre de la même chaque fois.</span><span class="sxs-lookup"><span data-stu-id="11818-121">That is, when `JITCachedFunctionSearchStarted` is called multiple times with the same `functionId` value, the profiler must respond the same each time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11818-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="11818-122">Requirements</span></span>  
 <span data-ttu-id="11818-123">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11818-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11818-124">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="11818-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="11818-125">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11818-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11818-126">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11818-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11818-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="11818-127">See also</span></span>

- [<span data-ttu-id="11818-128">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="11818-128">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
