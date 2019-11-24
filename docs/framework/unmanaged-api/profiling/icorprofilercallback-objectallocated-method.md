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
# <a name="icorprofilercallbackobjectallocated-method"></a><span data-ttu-id="51326-102">ICorProfilerCallback::ObjectAllocated, méthode</span><span class="sxs-lookup"><span data-stu-id="51326-102">ICorProfilerCallback::ObjectAllocated Method</span></span>
<span data-ttu-id="51326-103">Notifies the profiler that memory within the heap has been allocated for an object.</span><span class="sxs-lookup"><span data-stu-id="51326-103">Notifies the profiler that memory within the heap has been allocated for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51326-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51326-104">Syntax</span></span>  
  
```cpp  
HRESULT ObjectAllocated(  
    [in] ObjectID objectId,  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="51326-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="51326-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="51326-106">[in] The ID of the object for which memory was allocated.</span><span class="sxs-lookup"><span data-stu-id="51326-106">[in] The ID of the object for which memory was allocated.</span></span>  
  
 `classId`  
 <span data-ttu-id="51326-107">[in] The ID of the class of which the object is an instance.</span><span class="sxs-lookup"><span data-stu-id="51326-107">[in] The ID of the class of which the object is an instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="51326-108">Notes</span><span class="sxs-lookup"><span data-stu-id="51326-108">Remarks</span></span>  
 <span data-ttu-id="51326-109">The `ObjectedAllocated` method is not called for allocations from either the stack or unmanaged memory.</span><span class="sxs-lookup"><span data-stu-id="51326-109">The `ObjectedAllocated` method is not called for allocations from either the stack or unmanaged memory.</span></span> <span data-ttu-id="51326-110">The `classId` parameter can refer to a class in managed code that has not been loaded yet.</span><span class="sxs-lookup"><span data-stu-id="51326-110">The `classId` parameter can refer to a class in managed code that has not been loaded yet.</span></span> <span data-ttu-id="51326-111">The profiler will receive a class load callback for that class immediately after the `ObjectAllocated` callback.</span><span class="sxs-lookup"><span data-stu-id="51326-111">The profiler will receive a class load callback for that class immediately after the `ObjectAllocated` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51326-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="51326-112">Requirements</span></span>  
 <span data-ttu-id="51326-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51326-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51326-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="51326-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="51326-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="51326-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51326-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51326-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51326-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="51326-117">See also</span></span>

- [<span data-ttu-id="51326-118">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="51326-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="51326-119">ClassLoadStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="51326-119">ClassLoadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)
- [<span data-ttu-id="51326-120">ClassLoadFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="51326-120">ClassLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)
