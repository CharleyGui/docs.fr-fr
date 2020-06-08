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
ms.openlocfilehash: 2715a5b6b03a5ad33a6f18fb736fce3911bfbef0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500024"
---
# <a name="icorprofilercallbackjitfunctionpitched-method"></a><span data-ttu-id="036f0-102">ICorProfilerCallback::JITFunctionPitched, méthode</span><span class="sxs-lookup"><span data-stu-id="036f0-102">ICorProfilerCallback::JITFunctionPitched Method</span></span>
<span data-ttu-id="036f0-103">Notifie le profileur qu’une fonction qui a été compilée juste-à-temps (JIT) a été supprimée de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="036f0-103">Notifies the profiler that a function that has been just-in-time (JIT)-compiled has been removed from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="036f0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="036f0-104">Syntax</span></span>  
  
```cpp  
HRESULT JITFunctionPitched(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="036f0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="036f0-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="036f0-106">dans ID de la fonction qui a été supprimée.</span><span class="sxs-lookup"><span data-stu-id="036f0-106">[in] The ID of the function that was removed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="036f0-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="036f0-107">Remarks</span></span>  
 <span data-ttu-id="036f0-108">Si la fonction supprimée est appelée, le profileur reçoit de nouveaux événements de compilation JIT lorsque la fonction est recompilée.</span><span class="sxs-lookup"><span data-stu-id="036f0-108">If the removed function is called, the profiler will receive new JIT-compilation events when the function is recompiled.</span></span> <span data-ttu-id="036f0-109">Actuellement, le compilateur JIT (CLR) common language runtime ne supprime pas les fonctions de la mémoire, ce rappel n’est donc pas utilisé pour le moment et n’est pas reçu par le profileur.</span><span class="sxs-lookup"><span data-stu-id="036f0-109">Currently, the common language runtime (CLR) JIT compiler does not remove functions from memory, so this callback is currently not used and will not be received by the profiler.</span></span>  
  
 <span data-ttu-id="036f0-110">La valeur de `functionId` n’est pas valide tant que la fonction n’est pas recompilée.</span><span class="sxs-lookup"><span data-stu-id="036f0-110">The value of `functionId` is not valid until the function is recompiled.</span></span> <span data-ttu-id="036f0-111">Lorsque la fonction est recompilée, la même `functionId` valeur est utilisée.</span><span class="sxs-lookup"><span data-stu-id="036f0-111">When the function is recompiled, the same `functionId` value will be used.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="036f0-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="036f0-112">Requirements</span></span>  
 <span data-ttu-id="036f0-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="036f0-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="036f0-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="036f0-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="036f0-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="036f0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="036f0-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="036f0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="036f0-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="036f0-117">See also</span></span>

- [<span data-ttu-id="036f0-118">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="036f0-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
