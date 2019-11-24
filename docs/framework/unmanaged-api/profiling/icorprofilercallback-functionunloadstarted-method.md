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
ms.openlocfilehash: f57a3ed70267de65daed85305ad7d623b4ca0337
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448017"
---
# <a name="icorprofilercallbackfunctionunloadstarted-method"></a><span data-ttu-id="d0295-102">ICorProfilerCallback::FunctionUnloadStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="d0295-102">ICorProfilerCallback::FunctionUnloadStarted Method</span></span>
<span data-ttu-id="d0295-103">Notifies the profiler that the runtime has started to unload a function.</span><span class="sxs-lookup"><span data-stu-id="d0295-103">Notifies the profiler that the runtime has started to unload a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0295-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d0295-104">Syntax</span></span>  
  
```cpp  
HRESULT FunctionUnloadStarted(  
    [in] FunctionID functionId);   
```  
  
## <a name="parameters"></a><span data-ttu-id="d0295-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d0295-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="d0295-106">[in] The ID of the function that is being unloaded.</span><span class="sxs-lookup"><span data-stu-id="d0295-106">[in] The ID of the function that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0295-107">Notes</span><span class="sxs-lookup"><span data-stu-id="d0295-107">Remarks</span></span>  
 <span data-ttu-id="d0295-108">The value of the `functionId` parameter is no longer valid after this method returns to the caller.</span><span class="sxs-lookup"><span data-stu-id="d0295-108">The value of the `functionId` parameter is no longer valid after this method returns to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0295-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="d0295-109">Requirements</span></span>  
 <span data-ttu-id="d0295-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0295-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0295-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d0295-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d0295-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d0295-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0295-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0295-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0295-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d0295-114">See also</span></span>

- [<span data-ttu-id="d0295-115">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="d0295-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
