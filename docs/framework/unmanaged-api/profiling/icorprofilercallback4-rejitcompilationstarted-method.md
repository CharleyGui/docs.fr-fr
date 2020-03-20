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
ms.openlocfilehash: be257930ca0fad658afa75d6efa4573d4f888a2b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177079"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a><span data-ttu-id="cc3f1-102">ICorProfilerCallback4::ReJITCompilationStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="cc3f1-102">ICorProfilerCallback4::ReJITCompilationStarted Method</span></span>
<span data-ttu-id="cc3f1-103">Informe le profileur que le compilateur juste-à-temps (JIT) a commencé à recomposer une fonction.</span><span class="sxs-lookup"><span data-stu-id="cc3f1-103">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc3f1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc3f1-104">Syntax</span></span>  
  
```cpp  
HRESULT ReJITCompilationStarted(
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc3f1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cc3f1-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="cc3f1-106">[dans] L’ID de la fonction que le compilateur JIT a commencé à recomposer.</span><span class="sxs-lookup"><span data-stu-id="cc3f1-106">[in] The ID of the function that the JIT compiler has started to recompile.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="cc3f1-107">[dans] L’ID de recomplération de la nouvelle version de la fonction.</span><span class="sxs-lookup"><span data-stu-id="cc3f1-107">[in] The recompilation ID of the new version of the function.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="cc3f1-108">[dans] `true` pour indiquer que le blocage peut faire attendre le temps d’exécution pour que le fil d’appel revienne de ce rappel; `false` pour indiquer que le blocage n’affectera pas le fonctionnement de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="cc3f1-108">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span> <span data-ttu-id="cc3f1-109">Une valeur `true` de ne nuit pas à l’exécution, mais peut affecter les résultats de profilage.</span><span class="sxs-lookup"><span data-stu-id="cc3f1-109">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc3f1-110">Notes </span><span class="sxs-lookup"><span data-stu-id="cc3f1-110">Remarks</span></span>  
 <span data-ttu-id="cc3f1-111">Il est possible de recevoir `ReJITCompilationStarted` plus d’une paire de et [ReJITCompilationLa](icorprofilercallback4-rejitcompilationfinished-method.md) méthode définie appelle pour chaque fonction en raison de la façon dont le temps d’exécution gère les constructeurs de classe.</span><span class="sxs-lookup"><span data-stu-id="cc3f1-111">It is possible to receive more than one pair of `ReJITCompilationStarted` and [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) method calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="cc3f1-112">Par exemple, le temps d’exécution commence à recomposer la méthode A, mais le constructeur de classe pour la classe B doit être exécuté.</span><span class="sxs-lookup"><span data-stu-id="cc3f1-112">For example, the runtime starts to recompile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="cc3f1-113">Par conséquent, le temps d’exécution recompile le constructeur pour la classe B et l’exécute.</span><span class="sxs-lookup"><span data-stu-id="cc3f1-113">Therefore, the runtime recompiles the constructor for class B and runs it.</span></span> <span data-ttu-id="cc3f1-114">Pendant que le constructeur est en marche, il fait un appel à la méthode A, ce qui provoque la méthode A à être recompilé à nouveau.</span><span class="sxs-lookup"><span data-stu-id="cc3f1-114">While the constructor is running, it makes a call to method A, which causes method A to be recompiled again.</span></span> <span data-ttu-id="cc3f1-115">Dans ce scénario, la première récompatation de la méthode A est stoppée.</span><span class="sxs-lookup"><span data-stu-id="cc3f1-115">In this scenario, the first recompilation of method A is halted.</span></span> <span data-ttu-id="cc3f1-116">Cependant, les deux tentatives de recompiler la méthode A sont signalées avec des événements de recomplération JIT.</span><span class="sxs-lookup"><span data-stu-id="cc3f1-116">However, both attempts to recompile method A are reported with JIT recompilation events.</span></span>  
  
 <span data-ttu-id="cc3f1-117">Les profileurs doivent prendre en charge la séquence des rappels de recomplissement JIT dans les cas où deux threads effectuent simultanément des rappels.</span><span class="sxs-lookup"><span data-stu-id="cc3f1-117">Profilers must support the sequence of JIT recompilation callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="cc3f1-118">Par exemple, les `ReJITCompilationStarted`appels de fil A ; cependant, avant le fil A appelle [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md), thread B appelle [ICorProfilerCallback::ExceptionSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) avec l’ID de fonction de la callback pour le `ReJITCompilationStarted` fil A. Il peut sembler que l’ID de fonction ne devrait pas encore être valide parce qu’un appel à [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) n’avait pas encore été reçu par le profileur.</span><span class="sxs-lookup"><span data-stu-id="cc3f1-118">For example, thread A calls `ReJITCompilationStarted`; however, before thread A calls [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md), thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from the `ReJITCompilationStarted` callback for thread A. It might appear that the function ID should not yet be valid because a call to [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) had not yet been received by the profiler.</span></span> <span data-ttu-id="cc3f1-119">Toutefois, dans ce cas, l’ID de fonction est valide.</span><span class="sxs-lookup"><span data-stu-id="cc3f1-119">However, in this case, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc3f1-120">Spécifications</span><span class="sxs-lookup"><span data-stu-id="cc3f1-120">Requirements</span></span>  
 <span data-ttu-id="cc3f1-121">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc3f1-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc3f1-122">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cc3f1-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cc3f1-123">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc3f1-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc3f1-124">**.NET Versions-cadre:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc3f1-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc3f1-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cc3f1-125">See also</span></span>

- [<span data-ttu-id="cc3f1-126">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="cc3f1-126">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="cc3f1-127">ICorProfilerCallback4, interface</span><span class="sxs-lookup"><span data-stu-id="cc3f1-127">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
- [<span data-ttu-id="cc3f1-128">JITCompilationFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="cc3f1-128">JITCompilationFinished Method</span></span>](icorprofilercallback-jitcompilationfinished-method.md)
- [<span data-ttu-id="cc3f1-129">ReJITCompilationFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="cc3f1-129">ReJITCompilationFinished Method</span></span>](icorprofilercallback4-rejitcompilationfinished-method.md)
