---
title: ICorProfilerCallback::JITFunctionPitched, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITFunctionPitched
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITFunctionPitched
helpviewer_keywords:
- JITFunctionPitched method [.NET Framework profiling]
- ICorProfilerCallback::JITFunctionPitched method [.NET Framework profiling]
ms.assetid: 116085df-7a77-404a-afac-d0557a12b986
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 71df3bc707099cbad06742d964881ee629216b69
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782815"
---
# <a name="icorprofilercallbackjitfunctionpitched-method"></a><span data-ttu-id="25a5f-102">ICorProfilerCallback::JITFunctionPitched, méthode</span><span class="sxs-lookup"><span data-stu-id="25a5f-102">ICorProfilerCallback::JITFunctionPitched Method</span></span>
<span data-ttu-id="25a5f-103">Notifie le profileur qui une fonction qui a été juste-à-temps (JIT)-compilé a été supprimé de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="25a5f-103">Notifies the profiler that a function that has been just-in-time (JIT)-compiled has been removed from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25a5f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25a5f-104">Syntax</span></span>  
  
```cpp  
HRESULT JITFunctionPitched(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25a5f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="25a5f-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="25a5f-106">[in] L’ID de la fonction qui a été supprimée.</span><span class="sxs-lookup"><span data-stu-id="25a5f-106">[in] The ID of the function that was removed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25a5f-107">Notes</span><span class="sxs-lookup"><span data-stu-id="25a5f-107">Remarks</span></span>  
 <span data-ttu-id="25a5f-108">Si la fonction supprimée est appelée, le profileur reçoit les nouveaux événements de compilation JIT lorsque la fonction est recompilée.</span><span class="sxs-lookup"><span data-stu-id="25a5f-108">If the removed function is called, the profiler will receive new JIT-compilation events when the function is recompiled.</span></span> <span data-ttu-id="25a5f-109">Actuellement, le compilateur JIT de common language runtime (CLR) ne supprime pas les fonctions de la mémoire, ce rappel n’est actuellement pas utilisé et n’est pas reçu par le profileur.</span><span class="sxs-lookup"><span data-stu-id="25a5f-109">Currently, the common language runtime (CLR) JIT compiler does not remove functions from memory, so this callback is currently not used and will not be received by the profiler.</span></span>  
  
 <span data-ttu-id="25a5f-110">La valeur de `functionId` n’est pas valide tant que la fonction est recompilée.</span><span class="sxs-lookup"><span data-stu-id="25a5f-110">The value of `functionId` is not valid until the function is recompiled.</span></span> <span data-ttu-id="25a5f-111">Lorsque la fonction est recompilée, les mêmes `functionId` valeur sera utilisée.</span><span class="sxs-lookup"><span data-stu-id="25a5f-111">When the function is recompiled, the same `functionId` value will be used.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25a5f-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="25a5f-112">Requirements</span></span>  
 <span data-ttu-id="25a5f-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25a5f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25a5f-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="25a5f-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="25a5f-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="25a5f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25a5f-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25a5f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25a5f-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="25a5f-117">See also</span></span>

- [<span data-ttu-id="25a5f-118">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="25a5f-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
