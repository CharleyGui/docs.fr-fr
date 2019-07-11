---
title: ICorProfilerCallback::ObjectReferences, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectReferences
helpviewer_keywords:
- ObjectReferences method [.NET Framework profiling]
- ICorProfilerCallback::ObjectReferences method [.NET Framework profiling]
ms.assetid: dd5e9b64-b4a3-4ba6-9be6-ddb540f4ffcf
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4141c79502dae89ec228e4e39da121615f292786
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782972"
---
# <a name="icorprofilercallbackobjectreferences-method"></a><span data-ttu-id="9eabc-102">ICorProfilerCallback::ObjectReferences, méthode</span><span class="sxs-lookup"><span data-stu-id="9eabc-102">ICorProfilerCallback::ObjectReferences Method</span></span>
<span data-ttu-id="9eabc-103">Notifie le profileur sur les objets en mémoire qui sont référencés par l’objet spécifié.</span><span class="sxs-lookup"><span data-stu-id="9eabc-103">Notifies the profiler about objects in memory that are being referenced by the specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9eabc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9eabc-104">Syntax</span></span>  
  
```cpp  
HRESULT ObjectReferences(  
    [in]  ObjectID objectId,  
    [in]  ClassID  classId,  
    [in]  ULONG    cObjectRefs,  
    [in, size_is(cObjectRefs)] ObjectID objectRefIds[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="9eabc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9eabc-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="9eabc-106">[in] L’ID de l’objet qui fait référence à des objets.</span><span class="sxs-lookup"><span data-stu-id="9eabc-106">[in] The ID of the object that is referencing objects.</span></span>  
  
 `classId`  
 <span data-ttu-id="9eabc-107">[in] L’ID de la classe de l’objet spécifié est une instance de.</span><span class="sxs-lookup"><span data-stu-id="9eabc-107">[in] The ID of the class that the specified object is an instance of.</span></span>  
  
 `cObjectRefs`  
 <span data-ttu-id="9eabc-108">[in] Le nombre d’objets référencés par l’objet spécifié (autrement dit, le nombre d’éléments dans le `objectRefIds` tableau).</span><span class="sxs-lookup"><span data-stu-id="9eabc-108">[in] The number of objects referenced by the specified object (that is, the number of elements in the `objectRefIds` array).</span></span>  
  
 `objectRefIds`  
 <span data-ttu-id="9eabc-109">[in] Un tableau des ID des objets qui sont référencés par `objectId`.</span><span class="sxs-lookup"><span data-stu-id="9eabc-109">[in] An array of IDs of objects that are being referenced by `objectId`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9eabc-110">Notes</span><span class="sxs-lookup"><span data-stu-id="9eabc-110">Remarks</span></span>  
 <span data-ttu-id="9eabc-111">Le `ObjectReferences` méthode est appelée pour chaque objet reste dans le tas après l’exécution d’un garbage collection.</span><span class="sxs-lookup"><span data-stu-id="9eabc-111">The `ObjectReferences` method is called for each object remaining in the heap after a garbage collection has completed.</span></span> <span data-ttu-id="9eabc-112">Si le profileur retourne une erreur à partir de ce rappel, les services de profilage cessent d’appeler ce rappel jusqu'à ce que le garbage collection suivant.</span><span class="sxs-lookup"><span data-stu-id="9eabc-112">If the profiler returns an error from this callback, the profiling services will discontinue invoking this callback until the next garbage collection.</span></span>  
  
 <span data-ttu-id="9eabc-113">Le `ObjectReferences` rappel peut être utilisé conjointement avec le [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) rappel pour créer un graphique de référence d’objet complet pour le runtime.</span><span class="sxs-lookup"><span data-stu-id="9eabc-113">The `ObjectReferences` callback can be used in conjunction with the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) callback to create a complete object reference graph for the runtime.</span></span> <span data-ttu-id="9eabc-114">Le common language runtime (CLR) garantit que chaque référence d’objet est signalé qu’une seule fois par le `ObjectReferences` (méthode).</span><span class="sxs-lookup"><span data-stu-id="9eabc-114">The common language runtime (CLR) ensures that each object reference is reported only once by the `ObjectReferences` method.</span></span>  
  
 <span data-ttu-id="9eabc-115">Les ID d’objet retourné par `ObjectReferences` ne sont pas valides pendant le rappel lui-même, car le garbage collection peut être occupé à déplacer des objets.</span><span class="sxs-lookup"><span data-stu-id="9eabc-115">The object IDs returned by `ObjectReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects.</span></span> <span data-ttu-id="9eabc-116">Par conséquent, les profileurs ne doivent pas essayer d’inspecter les objets pendant un `ObjectReferences` appeler.</span><span class="sxs-lookup"><span data-stu-id="9eabc-116">Therefore, profilers must not attempt to inspect objects during an `ObjectReferences` call.</span></span> <span data-ttu-id="9eabc-117">Lorsque [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) est appelée, le garbage collection est terminé et l’inspection peut être effectuée en toute sécurité.</span><span class="sxs-lookup"><span data-stu-id="9eabc-117">When [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) is called, the garbage collection is complete and inspection can be safely done.</span></span>  
  
 <span data-ttu-id="9eabc-118">Une valeur null `ClassId` indique que `objectId` a un type qui est déchargement.</span><span class="sxs-lookup"><span data-stu-id="9eabc-118">A null `ClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9eabc-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9eabc-119">Requirements</span></span>  
 <span data-ttu-id="9eabc-120">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9eabc-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9eabc-121">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9eabc-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9eabc-122">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9eabc-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9eabc-123">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9eabc-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9eabc-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9eabc-124">See also</span></span>

- [<span data-ttu-id="9eabc-125">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="9eabc-125">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
