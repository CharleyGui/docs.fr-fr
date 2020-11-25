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
ms.openlocfilehash: 9485e3ca657ab108d2bcc9d00b1c475f8ee3c086
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703952"
---
# <a name="icorprofilercallbackobjectreferences-method"></a><span data-ttu-id="d3a69-102">ICorProfilerCallback::ObjectReferences, méthode</span><span class="sxs-lookup"><span data-stu-id="d3a69-102">ICorProfilerCallback::ObjectReferences Method</span></span>

<span data-ttu-id="d3a69-103">Notifie le profileur des objets en mémoire qui sont référencés par l’objet spécifié.</span><span class="sxs-lookup"><span data-stu-id="d3a69-103">Notifies the profiler about objects in memory that are being referenced by the specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3a69-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d3a69-104">Syntax</span></span>  
  
```cpp  
HRESULT ObjectReferences(  
    [in]  ObjectID objectId,  
    [in]  ClassID  classId,  
    [in]  ULONG    cObjectRefs,  
    [in, size_is(cObjectRefs)] ObjectID objectRefIds[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3a69-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d3a69-105">Parameters</span></span>  

 `objectId`  
 <span data-ttu-id="d3a69-106">dans ID de l’objet qui référence des objets.</span><span class="sxs-lookup"><span data-stu-id="d3a69-106">[in] The ID of the object that is referencing objects.</span></span>  
  
 `classId`  
 <span data-ttu-id="d3a69-107">dans ID de la classe dont l’objet spécifié est une instance de.</span><span class="sxs-lookup"><span data-stu-id="d3a69-107">[in] The ID of the class that the specified object is an instance of.</span></span>  
  
 `cObjectRefs`  
 <span data-ttu-id="d3a69-108">dans Nombre d’objets référencés par l’objet spécifié (autrement dit, le nombre d’éléments dans le `objectRefIds` tableau).</span><span class="sxs-lookup"><span data-stu-id="d3a69-108">[in] The number of objects referenced by the specified object (that is, the number of elements in the `objectRefIds` array).</span></span>  
  
 `objectRefIds`  
 <span data-ttu-id="d3a69-109">dans Tableau d’ID des objets référencés par `objectId` .</span><span class="sxs-lookup"><span data-stu-id="d3a69-109">[in] An array of IDs of objects that are being referenced by `objectId`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3a69-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="d3a69-110">Remarks</span></span>  

 <span data-ttu-id="d3a69-111">La `ObjectReferences` méthode est appelée pour chaque objet restant dans le tas à la fin d’une garbage collection.</span><span class="sxs-lookup"><span data-stu-id="d3a69-111">The `ObjectReferences` method is called for each object remaining in the heap after a garbage collection has completed.</span></span> <span data-ttu-id="d3a69-112">Si le profileur retourne une erreur à partir de ce rappel, les services de profilage ne continueront pas à appeler ce rappel jusqu’à la garbage collection suivante.</span><span class="sxs-lookup"><span data-stu-id="d3a69-112">If the profiler returns an error from this callback, the profiling services will discontinue invoking this callback until the next garbage collection.</span></span>  
  
 <span data-ttu-id="d3a69-113">Le `ObjectReferences` rappel peut être utilisé conjointement avec le rappel [ICorProfilerCallback :: RootReferences](icorprofilercallback-rootreferences-method.md) pour créer un graphique de référence d’objet complet pour le Runtime.</span><span class="sxs-lookup"><span data-stu-id="d3a69-113">The `ObjectReferences` callback can be used in conjunction with the [ICorProfilerCallback::RootReferences](icorprofilercallback-rootreferences-method.md) callback to create a complete object reference graph for the runtime.</span></span> <span data-ttu-id="d3a69-114">Le common language runtime (CLR) s’assure que chaque référence d’objet est signalée une seule fois par la `ObjectReferences` méthode.</span><span class="sxs-lookup"><span data-stu-id="d3a69-114">The common language runtime (CLR) ensures that each object reference is reported only once by the `ObjectReferences` method.</span></span>  
  
 <span data-ttu-id="d3a69-115">Les ID d’objet retournés par `ObjectReferences` ne sont pas valides pendant le rappel lui-même, car le garbage collection peut être en train de déplacer des objets.</span><span class="sxs-lookup"><span data-stu-id="d3a69-115">The object IDs returned by `ObjectReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects.</span></span> <span data-ttu-id="d3a69-116">Par conséquent, les profileurs ne doivent pas tenter d’inspecter les objets pendant un `ObjectReferences` appel.</span><span class="sxs-lookup"><span data-stu-id="d3a69-116">Therefore, profilers must not attempt to inspect objects during an `ObjectReferences` call.</span></span> <span data-ttu-id="d3a69-117">Quand [ICorProfilerCallback2 :: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) est appelé, le garbage collection est terminé et l’inspection peut être effectuée en toute sécurité.</span><span class="sxs-lookup"><span data-stu-id="d3a69-117">When [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) is called, the garbage collection is complete and inspection can be safely done.</span></span>  
  
 <span data-ttu-id="d3a69-118">Une valeur null `ClassId` indique que `objectId` a un type qui décharge.</span><span class="sxs-lookup"><span data-stu-id="d3a69-118">A null `ClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3a69-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d3a69-119">Requirements</span></span>  

 <span data-ttu-id="d3a69-120">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3a69-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3a69-121">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d3a69-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d3a69-122">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d3a69-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3a69-123">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3a69-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3a69-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d3a69-124">See also</span></span>

- [<span data-ttu-id="d3a69-125">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="d3a69-125">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
