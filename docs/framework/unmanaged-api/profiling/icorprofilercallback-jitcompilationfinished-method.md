---
title: ICorProfilerCallback::JITCompilationFinished, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCompilationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCompilationFinished
helpviewer_keywords:
- JITCompilationFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationFinished method [.NET Framework profiling]
ms.assetid: 8dcd7537-d0c6-498c-8a56-2c060310ef65
topic_type:
- apiref
ms.openlocfilehash: f1cfef464569b577923fbb16624c99358998d29c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866245"
---
# <a name="icorprofilercallbackjitcompilationfinished-method"></a><span data-ttu-id="141ee-102">ICorProfilerCallback::JITCompilationFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="141ee-102">ICorProfilerCallback::JITCompilationFinished Method</span></span>
<span data-ttu-id="141ee-103">Notifie le profileur que le compilateur juste-à-temps (JIT) a terminé la compilation d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="141ee-103">Notifies the profiler that the just-in-time (JIT) compiler has finished compiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="141ee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="141ee-104">Syntax</span></span>  
  
```cpp  
HRESULT JITCompilationFinished(  
    [in] FunctionID functionId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="141ee-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="141ee-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="141ee-106">\[in] ID de la fonction qui a été compilée.</span><span class="sxs-lookup"><span data-stu-id="141ee-106">\[in] The ID of the function that was compiled.</span></span>

- `hrStatus`

  <span data-ttu-id="141ee-107">\[dans] valeur indiquant si la compilation a réussi.</span><span class="sxs-lookup"><span data-stu-id="141ee-107">\[in] A value indicating whether compilation was successful.</span></span>

- `fIsSafeToBlock`

  <span data-ttu-id="141ee-108">\[in] valeur indiquant au profileur si le blocage affecte le fonctionnement du Runtime.</span><span class="sxs-lookup"><span data-stu-id="141ee-108">\[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="141ee-109">La valeur est `true` si le blocage peut amener le runtime à attendre que le thread appelant retourne à partir de ce rappel ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="141ee-109">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>

  <span data-ttu-id="141ee-110">Bien qu’une valeur de `true` n’endommage pas le runtime, elle peut incliner les résultats de profilage.</span><span class="sxs-lookup"><span data-stu-id="141ee-110">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>

## <a name="requirements"></a><span data-ttu-id="141ee-111">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="141ee-111">Requirements</span></span>  
 <span data-ttu-id="141ee-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="141ee-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="141ee-113">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="141ee-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="141ee-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="141ee-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="141ee-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="141ee-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="141ee-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="141ee-116">See also</span></span>

- [<span data-ttu-id="141ee-117">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="141ee-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="141ee-118">JITCompilationStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="141ee-118">JITCompilationStarted Method</span></span>](icorprofilercallback-jitcompilationstarted-method.md)
