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
ms.openlocfilehash: 30f2e675532848c2dbb1f055a0f1489cf3b2baa1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865790"
---
# <a name="icorprofilercallback2garbagecollectionfinished-method"></a><span data-ttu-id="3bdb6-102">ICorProfilerCallback2::GarbageCollectionFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="3bdb6-102">ICorProfilerCallback2::GarbageCollectionFinished Method</span></span>
<span data-ttu-id="3bdb6-103">Notifie le profileur que garbage collection est terminé et que tous les rappels de garbage collection ont été émis pour celui-ci.</span><span class="sxs-lookup"><span data-stu-id="3bdb6-103">Notifies the profiler that garbage collection has completed and all garbage collection callbacks have been issued for it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bdb6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3bdb6-104">Syntax</span></span>  
  
```cpp  
HRESULT GarbageCollectionFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="3bdb6-105">Notes</span><span class="sxs-lookup"><span data-stu-id="3bdb6-105">Remarks</span></span>  
 <span data-ttu-id="3bdb6-106">Le profileur peut inspecter en toute sécurité les objets dans leurs emplacements finaux lorsque la méthode `GarbageCollectionFinished` est appelée.</span><span class="sxs-lookup"><span data-stu-id="3bdb6-106">It is safe for the profiler to inspect objects in their final locations when the `GarbageCollectionFinished` method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3bdb6-107">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="3bdb6-107">Requirements</span></span>  
 <span data-ttu-id="3bdb6-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3bdb6-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3bdb6-109">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3bdb6-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3bdb6-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3bdb6-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3bdb6-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3bdb6-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bdb6-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3bdb6-112">See also</span></span>

- [<span data-ttu-id="3bdb6-113">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="3bdb6-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="3bdb6-114">ICorProfilerCallback2, interface</span><span class="sxs-lookup"><span data-stu-id="3bdb6-114">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
