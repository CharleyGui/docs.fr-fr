---
title: ICorProfilerInfo4::RequestReJIT, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.RequestReJIT
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::RequestReJIT
helpviewer_keywords:
- RequestReJIT method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestReJIT method [.NET Framework profiling]
ms.assetid: 781ed736-f30c-4816-920e-3552e36542c6
topic_type:
- apiref
ms.openlocfilehash: d2f8d538adb965864915fb1195bf9f2b8488aac8
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868406"
---
# <a name="icorprofilerinfo4requestrejit-method"></a><span data-ttu-id="7a485-102">ICorProfilerInfo4::RequestReJIT, méthode</span><span class="sxs-lookup"><span data-stu-id="7a485-102">ICorProfilerInfo4::RequestReJIT Method</span></span>
<span data-ttu-id="7a485-103">Demande une recompilation juste-à-temps de toutes les instances des fonctions spécifiées.</span><span class="sxs-lookup"><span data-stu-id="7a485-103">Requests a JIT recompilation of all instances of the specified functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a485-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7a485-104">Syntax</span></span>  
  
```cpp  
HRESULT RequestReJIT (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7a485-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="7a485-105">Parameters</span></span>  
 `cFunctions`  
 <span data-ttu-id="7a485-106">[in] Nombre de fonctions à recompiler.</span><span class="sxs-lookup"><span data-stu-id="7a485-106">[in] The number of functions to recompile.</span></span>  
  
 `moduleIds`  
 <span data-ttu-id="7a485-107">[in] Spécifie la partie `moduleId` des paires (`module`, `methodDef`) qui identifient les fonctions à recompiler.</span><span class="sxs-lookup"><span data-stu-id="7a485-107">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>  
  
 `methodIds`  
 <span data-ttu-id="7a485-108">[in] Spécifie la partie `methodId` des paires (`module`, `methodDef`) qui identifient les fonctions à recompiler.</span><span class="sxs-lookup"><span data-stu-id="7a485-108">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7a485-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="7a485-109">Return Value</span></span>  
 <span data-ttu-id="7a485-110">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="7a485-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="7a485-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7a485-111">HRESULT</span></span>|<span data-ttu-id="7a485-112">Description</span><span class="sxs-lookup"><span data-stu-id="7a485-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7a485-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="7a485-113">S_OK</span></span>|<span data-ttu-id="7a485-114">Une tentative a été effectuée pour marquer toutes les méthodes de recompilation juste-à-temps.</span><span class="sxs-lookup"><span data-stu-id="7a485-114">An attempt was made to mark all the methods for JIT recompilation.</span></span> <span data-ttu-id="7a485-115">Le profileur doit implémenter la méthode [ICorProfilerCallback4 :: rejiterror,](icorprofilercallback4-rejiterror-method.md) pour déterminer les méthodes qui ont été marquées avec succès pour la recompilation JIT.</span><span class="sxs-lookup"><span data-stu-id="7a485-115">The profiler must implement the [ICorProfilerCallback4::ReJITError](icorprofilercallback4-rejiterror-method.md) method to determine which methods were successfully marked for JIT recompilation.</span></span>|  
|<span data-ttu-id="7a485-116">CORPROF_E_CALLBACK4_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="7a485-116">CORPROF_E_CALLBACK4_REQUIRED</span></span>|<span data-ttu-id="7a485-117">Le profileur doit implémenter l’interface [ICorProfilerCallback4](icorprofilercallback4-interface.md) pour que cet appel soit pris en charge.</span><span class="sxs-lookup"><span data-stu-id="7a485-117">The profiler must implement the [ICorProfilerCallback4](icorprofilercallback4-interface.md) interface for this call to be supported.</span></span>|  
|<span data-ttu-id="7a485-118">CORPROF_E_REJIT_NOT_ENABLED</span><span class="sxs-lookup"><span data-stu-id="7a485-118">CORPROF_E_REJIT_NOT_ENABLED</span></span>|<span data-ttu-id="7a485-119">La recompilation juste-à-temps n'a pas été activée.</span><span class="sxs-lookup"><span data-stu-id="7a485-119">JIT recompilation has not been enabled.</span></span> <span data-ttu-id="7a485-120">Vous devez activer la recompilation JIT pendant l’initialisation à l’aide de la méthode [ICorProfilerInfo :: SetEventMask](icorprofilerinfo-seteventmask-method.md) pour définir l’indicateur `COR_PRF_ENABLE_REJIT`.</span><span class="sxs-lookup"><span data-stu-id="7a485-120">You must enable JIT recompilation during initialization by using the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the `COR_PRF_ENABLE_REJIT` flag.</span></span>|  
|<span data-ttu-id="7a485-121">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="7a485-121">E_INVALIDARG</span></span>|<span data-ttu-id="7a485-122">`cFunctions` est égal à 0, ou `moduleIds` ou `methodIds` a la valeur `NULL`.</span><span class="sxs-lookup"><span data-stu-id="7a485-122">`cFunctions` is 0, or `moduleIds` or `methodIds` is `NULL`.</span></span>|  
|||  
|<span data-ttu-id="7a485-123">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="7a485-123">E_OUTOFMEMORY</span></span>|<span data-ttu-id="7a485-124">Le CLR n'a pas pu terminer la demande en raison d'une mémoire insuffisante.</span><span class="sxs-lookup"><span data-stu-id="7a485-124">The CLR was unable to complete the request because it ran out of memory.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7a485-125">Notes</span><span class="sxs-lookup"><span data-stu-id="7a485-125">Remarks</span></span>  
 <span data-ttu-id="7a485-126">Appelez `RequestReJIT` pour que le runtime recompile un jeu spécifié de fonctions.</span><span class="sxs-lookup"><span data-stu-id="7a485-126">Call `RequestReJIT` to have the runtime recompile a specified set of functions.</span></span> <span data-ttu-id="7a485-127">Un profileur de code peut ensuite utiliser l’interface [ICorProfilerFunctionControl](icorprofilerfunctioncontrol-interface.md) pour ajuster le code qui est généré lorsque les fonctions sont recompilées.</span><span class="sxs-lookup"><span data-stu-id="7a485-127">A code profiler can then use the [ICorProfilerFunctionControl](icorprofilerfunctioncontrol-interface.md) interface to adjust the code that is generated when the functions are recompiled.</span></span> <span data-ttu-id="7a485-128">Cela n'affecte pas les fonctions en cours d'exécution ; seules les futurs appels de fonction sont concernés.</span><span class="sxs-lookup"><span data-stu-id="7a485-128">This does not affect currently executing functions, only future function invocations.</span></span> <span data-ttu-id="7a485-129">Si aucune des fonctions spécifiées n'a précédemment été recompilée juste-à-temps, le fait de demander une recompilation équivaut à restaurer et à recompiler la fonction.</span><span class="sxs-lookup"><span data-stu-id="7a485-129">If any of the specified functions has previously been JIT-recompiled, requesting a recompilation is equivalent to reverting and recompiling the function.</span></span> <span data-ttu-id="7a485-130">Pour conserver la capacité de restauration, le compilateur juste-à-temps tient uniquement compte des versions originales de ses appelés dans le cadre des décisions d'incorporation quand il compile la version d'origine d'une fonction.</span><span class="sxs-lookup"><span data-stu-id="7a485-130">To preserve reversibility, when the JIT compiler compiles the original version of a function, it considers only the original versions of its callees for inlining decisions.</span></span> <span data-ttu-id="7a485-131">Quand le compilateur juste-à-temps recompile une fonction, il tient compte des versions actuelles (recompilées ou d'origine) de ses appelés pour l'incorporation.</span><span class="sxs-lookup"><span data-stu-id="7a485-131">When the JIT compiler recompiles a function, it considers the current versions (recompiled or original) of its callees for inlining.</span></span>  
  
 <span data-ttu-id="7a485-132">Un profileur appelle généralement `RequestReJIT` en réponse à une entrée utilisateur demandant au profileur d'instrumenter une ou plusieurs méthodes.</span><span class="sxs-lookup"><span data-stu-id="7a485-132">A profiler typically calls `RequestReJIT` in response to user input requesting that the profiler instrument one or more methods.</span></span> <span data-ttu-id="7a485-133">`RequestReJIT` interrompt généralement le runtime pour effectuer une partie de son travail et peut éventuellement déclencher un garbage collection.</span><span class="sxs-lookup"><span data-stu-id="7a485-133">`RequestReJIT` typically suspends the runtime in order to do some of its work, and can potentially trigger a garbage collection.</span></span> <span data-ttu-id="7a485-134">Par conséquent, le profileur doit appeler `RequestReJIT` à partir d'un thread créé précédemment et non à partir d'un thread créé par le CLR qui exécute actuellement un rappel de profileur.</span><span class="sxs-lookup"><span data-stu-id="7a485-134">As such, the profiler should call `RequestReJIT` from a thread it previously created, and not from a CLR-created thread that is currently executing a profiler callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a485-135">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="7a485-135">Requirements</span></span>  
 <span data-ttu-id="7a485-136">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a485-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a485-137">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7a485-137">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7a485-138">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a485-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a485-139">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a485-139">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a485-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7a485-140">See also</span></span>

- [<span data-ttu-id="7a485-141">ICorProfilerInfo4, interface</span><span class="sxs-lookup"><span data-stu-id="7a485-141">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="7a485-142">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="7a485-142">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="7a485-143">Profilage</span><span class="sxs-lookup"><span data-stu-id="7a485-143">Profiling</span></span>](index.md)
