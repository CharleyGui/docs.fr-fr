---
title: ICorProfilerCallback::FunctionUnloadStarted, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.FunctionUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::FunctionUnloadStarted
helpviewer_keywords:
- FunctionUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::FunctionUnloadStarted method [.NET Framework profiling]
ms.assetid: d6a5fa8b-09c6-47a5-b60e-6cf2e355df30
topic_type:
- apiref
ms.openlocfilehash: 2b228337a55d50b94da966b45877e2000b3c03e4
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866310"
---
# <a name="icorprofilercallbackfunctionunloadstarted-method"></a><span data-ttu-id="e4409-102">ICorProfilerCallback::FunctionUnloadStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="e4409-102">ICorProfilerCallback::FunctionUnloadStarted Method</span></span>
<span data-ttu-id="e4409-103">Notifie le profileur que le runtime a commencé à décharger une fonction.</span><span class="sxs-lookup"><span data-stu-id="e4409-103">Notifies the profiler that the runtime has started to unload a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4409-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4409-104">Syntax</span></span>  
  
```cpp  
HRESULT FunctionUnloadStarted(  
    [in] FunctionID functionId);   
```  
  
## <a name="parameters"></a><span data-ttu-id="e4409-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="e4409-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="e4409-106">\[in] ID de la fonction en cours de déchargement.</span><span class="sxs-lookup"><span data-stu-id="e4409-106">\[in] The ID of the function that is being unloaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="e4409-107">Notes</span><span class="sxs-lookup"><span data-stu-id="e4409-107">Remarks</span></span>  
 <span data-ttu-id="e4409-108">La valeur du paramètre `functionId` n’est plus valide après le retour de cette méthode à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="e4409-108">The value of the `functionId` parameter is no longer valid after this method returns to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4409-109">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="e4409-109">Requirements</span></span>  
 <span data-ttu-id="e4409-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4409-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4409-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e4409-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e4409-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e4409-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4409-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4409-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4409-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e4409-114">See also</span></span>

- [<span data-ttu-id="e4409-115">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="e4409-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
