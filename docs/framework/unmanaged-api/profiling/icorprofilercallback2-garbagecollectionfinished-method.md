---
title: ICorProfilerCallback2::GarbageCollectionFinished, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.GarbageCollectionFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::GarbageCollectionFinished
helpviewer_keywords:
- ICorProfilerCallback2::GarbageCollectionFinished method [.NET Framework profiling]
- GarbageCollectionFinished method [.NET Framework profiling]
ms.assetid: 1a5758ea-2354-43c0-92a3-32c9909d64e1
topic_type:
- apiref
ms.openlocfilehash: 1217bb30be8b88f8ba1cf21f03f2531778358d4b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439843"
---
# <a name="icorprofilercallback2garbagecollectionfinished-method"></a><span data-ttu-id="ebe63-102">ICorProfilerCallback2::GarbageCollectionFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="ebe63-102">ICorProfilerCallback2::GarbageCollectionFinished Method</span></span>
<span data-ttu-id="ebe63-103">Notifies the profiler that garbage collection has completed and all garbage collection callbacks have been issued for it.</span><span class="sxs-lookup"><span data-stu-id="ebe63-103">Notifies the profiler that garbage collection has completed and all garbage collection callbacks have been issued for it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebe63-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ebe63-104">Syntax</span></span>  
  
```cpp  
HRESULT GarbageCollectionFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="ebe63-105">Notes</span><span class="sxs-lookup"><span data-stu-id="ebe63-105">Remarks</span></span>  
 <span data-ttu-id="ebe63-106">It is safe for the profiler to inspect objects in their final locations when the `GarbageCollectionFinished` method is called.</span><span class="sxs-lookup"><span data-stu-id="ebe63-106">It is safe for the profiler to inspect objects in their final locations when the `GarbageCollectionFinished` method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebe63-107">spécifications</span><span class="sxs-lookup"><span data-stu-id="ebe63-107">Requirements</span></span>  
 <span data-ttu-id="ebe63-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ebe63-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebe63-109">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ebe63-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ebe63-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ebe63-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ebe63-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebe63-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebe63-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ebe63-112">See also</span></span>

- [<span data-ttu-id="ebe63-113">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="ebe63-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="ebe63-114">ICorProfilerCallback2, interface</span><span class="sxs-lookup"><span data-stu-id="ebe63-114">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
