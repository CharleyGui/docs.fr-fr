---
title: ICorProfilerCallback4::ReJITCompilationFinished, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITCompilationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITCompilationFinished
helpviewer_keywords:
- ICorProfilerCallback4::ReJITCompilationFinished method [.NET Framework profiling]
- ReJITCompilationFinished method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 3b5cff02-2005-44eb-a2bc-50214c4b0e1d
topic_type:
- apiref
ms.openlocfilehash: a6c2209433a652523fd8e3a7cc2db1272600e1bd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730264"
---
# <a name="icorprofilercallback4rejitcompilationfinished-method"></a><span data-ttu-id="3496d-102">ICorProfilerCallback4::ReJITCompilationFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="3496d-102">ICorProfilerCallback4::ReJITCompilationFinished Method</span></span>

<span data-ttu-id="3496d-103">Notifie le profileur que le compilateur juste-à-temps (JIT) a terminé la recompilation d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="3496d-103">Notifies the profiler that the just-in-time (JIT) compiler has finished recompiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3496d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3496d-104">Syntax</span></span>  
  
```cpp  
HRESULT ReJITCompilationFinished(  
    [in] FunctionID functionId,    [in] ReJITID rejitId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3496d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3496d-105">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="3496d-106">dans ID de la fonction qui a été recompilée.</span><span class="sxs-lookup"><span data-stu-id="3496d-106">[in] The ID of the function that was recompiled.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="3496d-107">[in] Identité de la fonction recompilée juste-à-temps.</span><span class="sxs-lookup"><span data-stu-id="3496d-107">[in] The identity of the JIT-recompiled function.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="3496d-108">dans Valeur qui indique si la recompilation JIT a réussi.</span><span class="sxs-lookup"><span data-stu-id="3496d-108">[in] A value that indicates whether the JIT recompilation was successful.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="3496d-109">[in] `true` pour indiquer que le blocage peut amener le runtime à attendre que le thread appelant retourne à partir de ce rappel ; `false` pour indiquer que le blocage n’affectera pas le fonctionnement du Runtime.</span><span class="sxs-lookup"><span data-stu-id="3496d-109">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  
  
 <span data-ttu-id="3496d-110">Une valeur de `true` n’endommage pas le runtime, mais peut affecter les résultats de profilage.</span><span class="sxs-lookup"><span data-stu-id="3496d-110">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3496d-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3496d-111">Requirements</span></span>  

 <span data-ttu-id="3496d-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3496d-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3496d-113">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3496d-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3496d-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3496d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3496d-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3496d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3496d-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3496d-116">See also</span></span>

- [<span data-ttu-id="3496d-117">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="3496d-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="3496d-118">ICorProfilerCallback4, interface</span><span class="sxs-lookup"><span data-stu-id="3496d-118">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
- [<span data-ttu-id="3496d-119">JITCompilationStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="3496d-119">JITCompilationStarted Method</span></span>](icorprofilercallback-jitcompilationstarted-method.md)
- [<span data-ttu-id="3496d-120">ReJITCompilationStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="3496d-120">ReJITCompilationStarted Method</span></span>](icorprofilercallback4-rejitcompilationstarted-method.md)
