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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 10a000fd98ad12dc39f8f8338485d6bb4093ee07
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782981"
---
# <a name="icorprofilercallbackobjectallocated-method"></a><span data-ttu-id="8bdb8-102">ICorProfilerCallback::ObjectAllocated, méthode</span><span class="sxs-lookup"><span data-stu-id="8bdb8-102">ICorProfilerCallback::ObjectAllocated Method</span></span>
<span data-ttu-id="8bdb8-103">Notifie le profileur de mémoire dans le tas a été allouée pour un objet.</span><span class="sxs-lookup"><span data-stu-id="8bdb8-103">Notifies the profiler that memory within the heap has been allocated for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bdb8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8bdb8-104">Syntax</span></span>  
  
```cpp  
HRESULT ObjectAllocated(  
    [in] ObjectID objectId,  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8bdb8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8bdb8-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="8bdb8-106">[in] L’ID de l’objet pour lequel la mémoire a été allouée.</span><span class="sxs-lookup"><span data-stu-id="8bdb8-106">[in] The ID of the object for which memory was allocated.</span></span>  
  
 `classId`  
 <span data-ttu-id="8bdb8-107">[in] L’ID de la classe dont l’objet est une instance.</span><span class="sxs-lookup"><span data-stu-id="8bdb8-107">[in] The ID of the class of which the object is an instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8bdb8-108">Notes</span><span class="sxs-lookup"><span data-stu-id="8bdb8-108">Remarks</span></span>  
 <span data-ttu-id="8bdb8-109">Le `ObjectedAllocated` méthode n’est pas appelée pour les allocations de la pile ou de mémoire non managée.</span><span class="sxs-lookup"><span data-stu-id="8bdb8-109">The `ObjectedAllocated` method is not called for allocations from either the stack or unmanaged memory.</span></span> <span data-ttu-id="8bdb8-110">Le `classId` paramètre peut faire référence à une classe dans le code managé qui n’a pas encore été chargée.</span><span class="sxs-lookup"><span data-stu-id="8bdb8-110">The `classId` parameter can refer to a class in managed code that has not been loaded yet.</span></span> <span data-ttu-id="8bdb8-111">Le profileur reçoit un rappel de chargement de classe pour cette classe immédiatement après le `ObjectAllocated` rappel.</span><span class="sxs-lookup"><span data-stu-id="8bdb8-111">The profiler will receive a class load callback for that class immediately after the `ObjectAllocated` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8bdb8-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8bdb8-112">Requirements</span></span>  
 <span data-ttu-id="8bdb8-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8bdb8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8bdb8-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8bdb8-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8bdb8-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8bdb8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8bdb8-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8bdb8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bdb8-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8bdb8-117">See also</span></span>

- [<span data-ttu-id="8bdb8-118">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="8bdb8-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="8bdb8-119">ClassLoadStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="8bdb8-119">ClassLoadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)
- [<span data-ttu-id="8bdb8-120">ClassLoadFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="8bdb8-120">ClassLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)
