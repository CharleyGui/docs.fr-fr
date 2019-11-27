---
title: ICorProfilerCallback::JITCompilationStarted, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCompilationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCompilationStarted
helpviewer_keywords:
- JITCompilationStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationStarted method [.NET Framework profiling]
ms.assetid: 31782b36-d311-4518-8f45-25f65385af5b
topic_type:
- apiref
ms.openlocfilehash: 96ab77a36c0a0bddda0fca342433666dd19082d3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426194"
---
# <a name="icorprofilercallbackjitcompilationstarted-method"></a><span data-ttu-id="047a7-102">ICorProfilerCallback::JITCompilationStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="047a7-102">ICorProfilerCallback::JITCompilationStarted Method</span></span>
<span data-ttu-id="047a7-103">Notifie le profileur que le compilateur juste-à-temps (JIT) a commencé à compiler une fonction.</span><span class="sxs-lookup"><span data-stu-id="047a7-103">Notifies the profiler that the just-in-time (JIT) compiler has started to compile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="047a7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="047a7-104">Syntax</span></span>  
  
```cpp  
HRESULT JITCompilationStarted(  
    [in] FunctionID functionId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="047a7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="047a7-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="047a7-106">dans ID de la fonction pour laquelle la compilation démarre.</span><span class="sxs-lookup"><span data-stu-id="047a7-106">[in] The ID of the function for which the compilation is starting.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="047a7-107">dans Valeur indiquant au profileur si le blocage affecte le fonctionnement du Runtime.</span><span class="sxs-lookup"><span data-stu-id="047a7-107">[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="047a7-108">La valeur est `true` si le blocage peut amener le runtime à attendre que le thread appelant retourne à partir de ce rappel ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="047a7-108">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="047a7-109">Bien qu’une valeur de `true` n’endommage pas le runtime, elle peut incliner les résultats de profilage.</span><span class="sxs-lookup"><span data-stu-id="047a7-109">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="047a7-110">Notes</span><span class="sxs-lookup"><span data-stu-id="047a7-110">Remarks</span></span>  
 <span data-ttu-id="047a7-111">Il est possible de recevoir plus d’une paire d' `JITCompilationStarted` et d’appels [ICorProfilerCallback :: JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md) pour chaque fonction, en raison de la façon dont le Runtime gère les constructeurs de classe.</span><span class="sxs-lookup"><span data-stu-id="047a7-111">It is possible to receive more than one pair of `JITCompilationStarted` and [ICorProfilerCallback::JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md) calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="047a7-112">Par exemple, le runtime commence à effectuer une compilation JIT de la méthode A, mais le constructeur de classe de la classe B doit être exécuté.</span><span class="sxs-lookup"><span data-stu-id="047a7-112">For example, the runtime starts to JIT-compile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="047a7-113">Par conséquent, le runtime JIT compile le constructeur pour la classe B et l’exécute.</span><span class="sxs-lookup"><span data-stu-id="047a7-113">Therefore, the runtime JIT-compiles the constructor for class B and runs it.</span></span> <span data-ttu-id="047a7-114">Pendant que le constructeur est en cours d’exécution, il effectue un appel à la méthode A, ce qui entraîne une nouvelle compilation juste-à-temps de la méthode A.</span><span class="sxs-lookup"><span data-stu-id="047a7-114">While the constructor is running, it makes a call to method A, which causes method A to be JIT-compiled again.</span></span> <span data-ttu-id="047a7-115">Dans ce scénario, la première compilation JIT de la méthode A est arrêtée.</span><span class="sxs-lookup"><span data-stu-id="047a7-115">In this scenario, the first JIT compilation of method A is halted.</span></span> <span data-ttu-id="047a7-116">Toutefois, les deux tentatives de compilation JIT de la méthode A sont signalées par des événements de compilation JIT.</span><span class="sxs-lookup"><span data-stu-id="047a7-116">However, both attempts to JIT-compile method A are reported with JIT-compilation events.</span></span> <span data-ttu-id="047a7-117">Si le profileur va remplacer le code MSIL (Microsoft Intermediate Language) pour la méthode A en appelant la méthode [ICorProfilerInfo :: SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) , il doit le faire pour les deux événements `JITCompilationStarted`, mais il peut utiliser le même bloc MSIL pour les deux.</span><span class="sxs-lookup"><span data-stu-id="047a7-117">If the profiler is going to replace Microsoft intermediate language (MSIL) code for method A by calling the [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) method, it must do so for both `JITCompilationStarted` events, but it may use the same MSIL block for both.</span></span>  
  
 <span data-ttu-id="047a7-118">Les profileurs doivent prendre en charge la séquence de rappels JIT dans les cas où deux threads effectuent simultanément des rappels.</span><span class="sxs-lookup"><span data-stu-id="047a7-118">Profilers must support the sequence of JIT callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="047a7-119">Par exemple, le thread A appelle `JITCompilationStarted`.</span><span class="sxs-lookup"><span data-stu-id="047a7-119">For example, thread A calls `JITCompilationStarted`.</span></span> <span data-ttu-id="047a7-120">Toutefois, avant que le thread A appelle `JITCompilationFinished`, le thread B appelle [ICorProfilerCallback :: ExceptionSearchFunctionEnter,](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) avec l’ID de fonction du rappel `JITCompilationStarted` du thread A.</span><span class="sxs-lookup"><span data-stu-id="047a7-120">However, before thread A calls `JITCompilationFinished`, thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from thread A's `JITCompilationStarted` callback.</span></span> <span data-ttu-id="047a7-121">Il peut sembler que l’ID de fonction ne soit pas encore valide, car un appel à `JITCompilationFinished` n’a pas encore été reçu par le profileur.</span><span class="sxs-lookup"><span data-stu-id="047a7-121">It might appear that the function ID should not yet be valid because a call to `JITCompilationFinished` had not yet been received by the profiler.</span></span> <span data-ttu-id="047a7-122">Toutefois, dans un cas comme celui-ci, l’ID de fonction est valide.</span><span class="sxs-lookup"><span data-stu-id="047a7-122">However, in a case like this one, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="047a7-123">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="047a7-123">Requirements</span></span>  
 <span data-ttu-id="047a7-124">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="047a7-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="047a7-125">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="047a7-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="047a7-126">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="047a7-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="047a7-127">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="047a7-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="047a7-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="047a7-128">See also</span></span>

- [<span data-ttu-id="047a7-129">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="047a7-129">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="047a7-130">JITCompilationFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="047a7-130">JITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)
