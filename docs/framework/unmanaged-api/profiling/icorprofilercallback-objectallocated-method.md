---
title: ICorProfilerCallback::ObjectAllocated, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectAllocated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectAllocated
helpviewer_keywords:
- ObjectAllocated method [.NET Framework profiling]
- ICorProfilerCallback::ObjectAllocated method [.NET Framework profiling]
ms.assetid: eb412622-77cc-4abd-a2cd-c910fe8edd54
topic_type:
- apiref
ms.openlocfilehash: 66643bbb8dbc914b2e0e48a7f0c87630fe95e5d3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445851"
---
# <a name="icorprofilercallbackobjectallocated-method"></a><span data-ttu-id="a90e9-102">ICorProfilerCallback::ObjectAllocated, méthode</span><span class="sxs-lookup"><span data-stu-id="a90e9-102">ICorProfilerCallback::ObjectAllocated Method</span></span>
<span data-ttu-id="a90e9-103">Indique au profileur que la mémoire dans le tas a été allouée pour un objet.</span><span class="sxs-lookup"><span data-stu-id="a90e9-103">Notifies the profiler that memory within the heap has been allocated for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a90e9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a90e9-104">Syntax</span></span>  
  
```cpp  
HRESULT ObjectAllocated(  
    [in] ObjectID objectId,  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a90e9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a90e9-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="a90e9-106">dans ID de l’objet pour lequel la mémoire a été allouée.</span><span class="sxs-lookup"><span data-stu-id="a90e9-106">[in] The ID of the object for which memory was allocated.</span></span>  
  
 `classId`  
 <span data-ttu-id="a90e9-107">dans ID de la classe dont l’objet est une instance.</span><span class="sxs-lookup"><span data-stu-id="a90e9-107">[in] The ID of the class of which the object is an instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a90e9-108">Notes</span><span class="sxs-lookup"><span data-stu-id="a90e9-108">Remarks</span></span>  
 <span data-ttu-id="a90e9-109">La méthode `ObjectedAllocated` n’est pas appelée pour les allocations à partir de la pile ou de la mémoire non managée.</span><span class="sxs-lookup"><span data-stu-id="a90e9-109">The `ObjectedAllocated` method is not called for allocations from either the stack or unmanaged memory.</span></span> <span data-ttu-id="a90e9-110">Le paramètre `classId` peut faire référence à une classe dans du code managé qui n’a pas encore été chargée.</span><span class="sxs-lookup"><span data-stu-id="a90e9-110">The `classId` parameter can refer to a class in managed code that has not been loaded yet.</span></span> <span data-ttu-id="a90e9-111">Le profileur reçoit un rappel de charge de classe pour cette classe immédiatement après le rappel `ObjectAllocated`.</span><span class="sxs-lookup"><span data-stu-id="a90e9-111">The profiler will receive a class load callback for that class immediately after the `ObjectAllocated` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a90e9-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a90e9-112">Requirements</span></span>  
 <span data-ttu-id="a90e9-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a90e9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a90e9-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a90e9-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a90e9-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a90e9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a90e9-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a90e9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a90e9-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a90e9-117">See also</span></span>

- [<span data-ttu-id="a90e9-118">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="a90e9-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="a90e9-119">ClassLoadStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="a90e9-119">ClassLoadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)
- [<span data-ttu-id="a90e9-120">ClassLoadFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="a90e9-120">ClassLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)
