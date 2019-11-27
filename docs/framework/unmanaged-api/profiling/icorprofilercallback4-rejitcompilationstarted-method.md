---
title: ICorProfilerCallback4::ReJITCompilationStarted, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITCompilationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITCompilationStarted
helpviewer_keywords:
- ReJITCompilationStarted method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITCompilationStarted method [.NET Framework profiling]
ms.assetid: 512fdd00-262a-4456-a075-365ef4133c4d
topic_type:
- apiref
ms.openlocfilehash: 074b0b11a822d2b8bcb9588484557e3e5eba69dd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430197"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a><span data-ttu-id="d231a-102">ICorProfilerCallback4::ReJITCompilationStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="d231a-102">ICorProfilerCallback4::ReJITCompilationStarted Method</span></span>
<span data-ttu-id="d231a-103">Notifie le profileur que le compilateur juste-à-temps (JIT) a commencé à recompiler une fonction.</span><span class="sxs-lookup"><span data-stu-id="d231a-103">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d231a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d231a-104">Syntax</span></span>  
  
```cpp  
HRESULT ReJITCompilationStarted(   
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d231a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d231a-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="d231a-106">dans ID de la fonction que le compilateur JIT a commencé à recompiler.</span><span class="sxs-lookup"><span data-stu-id="d231a-106">[in] The ID of the function that the JIT compiler has started to recompile.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="d231a-107">dans ID de recompilation de la nouvelle version de la fonction.</span><span class="sxs-lookup"><span data-stu-id="d231a-107">[in] The recompilation ID of the new version of the function.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="d231a-108">[in] `true` pour indiquer que le blocage peut amener le runtime à attendre que le thread appelant retourne à partir de ce rappel ; `false` pour indiquer que le blocage n’affectera pas le fonctionnement du Runtime.</span><span class="sxs-lookup"><span data-stu-id="d231a-108">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span> <span data-ttu-id="d231a-109">Une valeur de `true` n’endommage pas le runtime, mais peut affecter les résultats de profilage.</span><span class="sxs-lookup"><span data-stu-id="d231a-109">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d231a-110">Notes</span><span class="sxs-lookup"><span data-stu-id="d231a-110">Remarks</span></span>  
 <span data-ttu-id="d231a-111">Il est possible de recevoir plus d’une paire de `ReJITCompilationStarted` et d’appels de méthode [rejitcompilationfinished,](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) pour chaque fonction en raison de la façon dont le Runtime gère les constructeurs de classe.</span><span class="sxs-lookup"><span data-stu-id="d231a-111">It is possible to receive more than one pair of `ReJITCompilationStarted` and [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) method calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="d231a-112">Par exemple, le runtime commence à recompiler la méthode A, mais le constructeur de classe pour la classe B doit être exécuté.</span><span class="sxs-lookup"><span data-stu-id="d231a-112">For example, the runtime starts to recompile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="d231a-113">Par conséquent, le runtime RECOMPILE le constructeur pour la classe B et l’exécute.</span><span class="sxs-lookup"><span data-stu-id="d231a-113">Therefore, the runtime recompiles the constructor for class B and runs it.</span></span> <span data-ttu-id="d231a-114">Pendant que le constructeur est en cours d’exécution, il effectue un appel à la méthode A, ce qui entraîne la recompilation de la méthode A.</span><span class="sxs-lookup"><span data-stu-id="d231a-114">While the constructor is running, it makes a call to method A, which causes method A to be recompiled again.</span></span> <span data-ttu-id="d231a-115">Dans ce scénario, la première recompilation de la méthode A est arrêtée.</span><span class="sxs-lookup"><span data-stu-id="d231a-115">In this scenario, the first recompilation of method A is halted.</span></span> <span data-ttu-id="d231a-116">Toutefois, les deux tentatives de recompilation de la méthode A sont signalées avec les événements de recompilation JIT.</span><span class="sxs-lookup"><span data-stu-id="d231a-116">However, both attempts to recompile method A are reported with JIT recompilation events.</span></span>  
  
 <span data-ttu-id="d231a-117">Les profileurs doivent prendre en charge la séquence de rappels de recompilation JIT dans les cas où deux threads effectuent simultanément des rappels.</span><span class="sxs-lookup"><span data-stu-id="d231a-117">Profilers must support the sequence of JIT recompilation callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="d231a-118">Par exemple, le thread A appelle `ReJITCompilationStarted`; Toutefois, avant que le thread A appelle [rejitcompilationfinished,](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md), thread B appelle [ICorProfilerCallback :: EXCEPTIONSEARCHFUNCTIONENTER,](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) avec l’ID de fonction du rappel `ReJITCompilationStarted` pour le thread A. Il peut sembler que l’ID de fonction ne soit pas encore valide, car un appel à [rejitcompilationfinished,](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) n’a pas encore été reçu par le profileur.</span><span class="sxs-lookup"><span data-stu-id="d231a-118">For example, thread A calls `ReJITCompilationStarted`; however, before thread A calls [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md), thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from the `ReJITCompilationStarted` callback for thread A. It might appear that the function ID should not yet be valid because a call to [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) had not yet been received by the profiler.</span></span> <span data-ttu-id="d231a-119">Toutefois, dans ce cas, l’ID de fonction est valide.</span><span class="sxs-lookup"><span data-stu-id="d231a-119">However, in this case, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d231a-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d231a-120">Requirements</span></span>  
 <span data-ttu-id="d231a-121">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d231a-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d231a-122">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d231a-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d231a-123">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d231a-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d231a-124">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d231a-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d231a-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d231a-125">See also</span></span>

- [<span data-ttu-id="d231a-126">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="d231a-126">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="d231a-127">ICorProfilerCallback4, interface</span><span class="sxs-lookup"><span data-stu-id="d231a-127">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [<span data-ttu-id="d231a-128">JITCompilationFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="d231a-128">JITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)
- [<span data-ttu-id="d231a-129">ReJITCompilationFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="d231a-129">ReJITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)
