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
ms.openlocfilehash: 84a71853ba2ccc8b95e4a8936005f2790d09a2c4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717307"
---
# <a name="icorprofilercallback2garbagecollectionfinished-method"></a><span data-ttu-id="80d31-102">ICorProfilerCallback2::GarbageCollectionFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="80d31-102">ICorProfilerCallback2::GarbageCollectionFinished Method</span></span>

<span data-ttu-id="80d31-103">Notifie le profileur que garbage collection est terminé et que tous les rappels de garbage collection ont été émis pour celui-ci.</span><span class="sxs-lookup"><span data-stu-id="80d31-103">Notifies the profiler that garbage collection has completed and all garbage collection callbacks have been issued for it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80d31-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="80d31-104">Syntax</span></span>  
  
```cpp  
HRESULT GarbageCollectionFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="80d31-105">Notes</span><span class="sxs-lookup"><span data-stu-id="80d31-105">Remarks</span></span>  

 <span data-ttu-id="80d31-106">Le profileur peut inspecter en toute sécurité les objets dans leurs emplacements finaux lorsque la `GarbageCollectionFinished` méthode est appelée.</span><span class="sxs-lookup"><span data-stu-id="80d31-106">It is safe for the profiler to inspect objects in their final locations when the `GarbageCollectionFinished` method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80d31-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="80d31-107">Requirements</span></span>  

 <span data-ttu-id="80d31-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80d31-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80d31-109">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="80d31-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="80d31-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="80d31-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="80d31-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80d31-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80d31-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="80d31-112">See also</span></span>

- [<span data-ttu-id="80d31-113">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="80d31-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="80d31-114">ICorProfilerCallback2, interface</span><span class="sxs-lookup"><span data-stu-id="80d31-114">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
