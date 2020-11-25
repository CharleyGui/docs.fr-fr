---
title: ICorProfilerCallback4::MovedReferences2, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.MovedReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::MovedReferences2
helpviewer_keywords:
- MovedReferences2 method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::MovedReferences2 method [.NET Framework profiling]
ms.assetid: d17a065b-5bc6-4817-b3e1-1e413fcb33a8
topic_type:
- apiref
ms.openlocfilehash: 41f7010b6c13327e45a4da7fdae1b9e1fe6e41a0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730277"
---
# <a name="icorprofilercallback4movedreferences2-method"></a><span data-ttu-id="a10e2-102">ICorProfilerCallback4::MovedReferences2, méthode</span><span class="sxs-lookup"><span data-stu-id="a10e2-102">ICorProfilerCallback4::MovedReferences2 Method</span></span>

<span data-ttu-id="a10e2-103">Appelée pour signaler la nouvelle disposition d'objets dans le tas suite à un garbage collection de compactage.</span><span class="sxs-lookup"><span data-stu-id="a10e2-103">Called to report the new layout of objects in the heap as a result of a compacting garbage collection.</span></span> <span data-ttu-id="a10e2-104">Cette méthode est appelée si le profileur a implémenté l’interface [ICorProfilerCallback4](icorprofilercallback4-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="a10e2-104">This method is called if the profiler has implemented the [ICorProfilerCallback4](icorprofilercallback4-interface.md) interface.</span></span> <span data-ttu-id="a10e2-105">Ce rappel remplace la méthode [ICorProfilerCallback :: MovedReferences](icorprofilercallback-movedreferences-method.md) , car il peut signaler des plages plus larges d’objets dont les longueurs dépassent ce qui peut être exprimé dans un ulong.</span><span class="sxs-lookup"><span data-stu-id="a10e2-105">This callback replaces the [ICorProfilerCallback::MovedReferences](icorprofilercallback-movedreferences-method.md) method, because it can report larger ranges of objects whose lengths exceed what can be expressed in a ULONG.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a10e2-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a10e2-106">Syntax</span></span>  
  
```cpp  
HRESULT MovedReferences2(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] SIZE_T    cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="a10e2-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a10e2-107">Parameters</span></span>  

 `cMovedObjectIDRanges`  
 <span data-ttu-id="a10e2-108">[in] Nombre de blocs d’objets contigus qui ont été déplacés à la suite du garbage collection de compactage.</span><span class="sxs-lookup"><span data-stu-id="a10e2-108">[in] The number of blocks of contiguous objects that moved as the result of the compacting garbage collection.</span></span> <span data-ttu-id="a10e2-109">Autrement dit, la valeur de `cMovedObjectIDRanges` est la taille totale des tableaux `oldObjectIDRangeStart`, `newObjectIDRangeStart` et `cObjectIDRangeLength`.</span><span class="sxs-lookup"><span data-stu-id="a10e2-109">That is, the value of `cMovedObjectIDRanges` is the total size of the `oldObjectIDRangeStart`, `newObjectIDRangeStart`, and `cObjectIDRangeLength` arrays.</span></span>  
  
 <span data-ttu-id="a10e2-110">Les trois arguments suivants de `MovedReferences2` sont des tableaux parallèles.</span><span class="sxs-lookup"><span data-stu-id="a10e2-110">The next three arguments of `MovedReferences2` are parallel arrays.</span></span> <span data-ttu-id="a10e2-111">En d'autres termes, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]` et `cObjectIDRangeLength[i]` concernent un bloc unique d'objets contigus.</span><span class="sxs-lookup"><span data-stu-id="a10e2-111">In other words, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, and `cObjectIDRangeLength[i]` all concern a single block of contiguous objects.</span></span>  
  
 `oldObjectIDRangeStart`  
 <span data-ttu-id="a10e2-112">[in] Tableau de valeurs `ObjectID`, chacune d'elles étant l'ancienne adresse de début (avant le garbage collection) d'un bloc d'objets actifs contigus dans la mémoire.</span><span class="sxs-lookup"><span data-stu-id="a10e2-112">[in] An array of `ObjectID` values, each of which is the old (pre-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `newObjectIDRangeStart`  
 <span data-ttu-id="a10e2-113">[in] Tableau de valeurs `ObjectID`, chacune d’elles étant la nouvelle adresse de début (après le garbage collection) d’un bloc d’objets actifs contigus dans la mémoire.</span><span class="sxs-lookup"><span data-stu-id="a10e2-113">[in] An array of `ObjectID` values, each of which is the new (post-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="a10e2-114">[in] Tableau d'entiers, chacun d'eux correspondant à la taille d'un bloc d'objets contigus dans la mémoire.</span><span class="sxs-lookup"><span data-stu-id="a10e2-114">[in] An array of integers, each of which is the size of a block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="a10e2-115">Une taille est spécifiée pour chaque bloc référencé dans les tableaux `oldObjectIDRangeStart` et `newObjectIDRangeStart`.</span><span class="sxs-lookup"><span data-stu-id="a10e2-115">A size is specified for each block that is referenced in the `oldObjectIDRangeStart` and `newObjectIDRangeStart` arrays.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a10e2-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="a10e2-116">Remarks</span></span>  

 <span data-ttu-id="a10e2-117">Un garbage collection de compactage récupère la mémoire occupée par des objets morts et compacte cet espace libéré.</span><span class="sxs-lookup"><span data-stu-id="a10e2-117">A compacting garbage collector reclaims the memory occupied by dead objects and compacts that freed space.</span></span> <span data-ttu-id="a10e2-118">Par conséquent, les objets actifs peuvent être déplacés dans le tas, et les valeurs `ObjectID` distribuées par des notifications précédentes peuvent changer.</span><span class="sxs-lookup"><span data-stu-id="a10e2-118">As a result, live objects might be moved within the heap, and `ObjectID` values distributed by previous notifications might change.</span></span>  
  
 <span data-ttu-id="a10e2-119">Supposons qu'une valeur `ObjectID` existante (`oldObjectID`) se trouve dans la plage suivante :</span><span class="sxs-lookup"><span data-stu-id="a10e2-119">Assume that an existing `ObjectID` value (`oldObjectID`) lies within the following range:</span></span>  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="a10e2-120">Dans ce cas, l'offset du début de la plage au début de l'objet est le suivant :</span><span class="sxs-lookup"><span data-stu-id="a10e2-120">In this case, the offset from the start of the range to the start of the object is as follows:</span></span>  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 <span data-ttu-id="a10e2-121">Pour toute valeur d'`i` se trouvant dans la plage suivante :</span><span class="sxs-lookup"><span data-stu-id="a10e2-121">For any value of `i` that is in the following range:</span></span>  
  
 <span data-ttu-id="a10e2-122">0 <= `i` < `cMovedObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="a10e2-122">0 <= `i` < `cMovedObjectIDRanges`</span></span>  
  
 <span data-ttu-id="a10e2-123">Vous pouvez calculer le nouvel `ObjectID` comme suit :</span><span class="sxs-lookup"><span data-stu-id="a10e2-123">you can calculate the new `ObjectID` as follows:</span></span>  
  
 <span data-ttu-id="a10e2-124">`newObjectID` = `newObjectIDRangeStart[i]` + ( `oldObjectID` – `oldObjectIDRangeStart[i]` )</span><span class="sxs-lookup"><span data-stu-id="a10e2-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span></span>  
  
 <span data-ttu-id="a10e2-125">Aucune des valeurs `ObjectID` passées par `MovedReferences2` n'est valide pendant le rappel lui-même, car le garbage collector peut être occupé à déplacer des objets depuis des anciens emplacements vers des nouveaux.</span><span class="sxs-lookup"><span data-stu-id="a10e2-125">None of the `ObjectID` values passed by `MovedReferences2` are valid during the callback itself, because the garbage collector might be in the middle of moving objects from old locations to new locations.</span></span> <span data-ttu-id="a10e2-126">Les profileurs ne doivent donc pas essayer d'inspecter des objets pendant un appel de `MovedReferences2`.</span><span class="sxs-lookup"><span data-stu-id="a10e2-126">Therefore, profilers should not attempt to inspect objects during a `MovedReferences2` call.</span></span> <span data-ttu-id="a10e2-127">Un rappel [ICorProfilerCallback2 :: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) indique que tous les objets ont été déplacés vers leurs nouveaux emplacements et que l’inspection peut être effectuée.</span><span class="sxs-lookup"><span data-stu-id="a10e2-127">A [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) callback indicates that all objects have been moved to their new locations and inspection can be performed.</span></span>  
  
 <span data-ttu-id="a10e2-128">Si le profileur implémente à la fois les interfaces [ICorProfilerCallback](icorprofilercallback-interface.md) et [ICorProfilerCallback4](icorprofilercallback4-interface.md) , la `MovedReferences2` méthode est appelée avant la méthode [ICorProfilerCallback :: MovedReferences](icorprofilercallback-movedreferences-method.md) , mais uniquement si la `MovedReferences2` méthode est correctement retournée.</span><span class="sxs-lookup"><span data-stu-id="a10e2-128">If the profiler implements both the [ICorProfilerCallback](icorprofilercallback-interface.md) and the [ICorProfilerCallback4](icorprofilercallback4-interface.md) interfaces, the `MovedReferences2` method is called before the [ICorProfilerCallback::MovedReferences](icorprofilercallback-movedreferences-method.md) method, but only if the `MovedReferences2` method returns successfully.</span></span> <span data-ttu-id="a10e2-129">Les profileurs peuvent retourner un HRESULT qui indique un échec de la méthode `MovedReferences2` pour éviter d'appeler la seconde méthode.</span><span class="sxs-lookup"><span data-stu-id="a10e2-129">Profilers can return an HRESULT that indicates failure from the `MovedReferences2` method, to avoid calling the second method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a10e2-130">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a10e2-130">Requirements</span></span>  

 <span data-ttu-id="a10e2-131">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a10e2-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a10e2-132">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a10e2-132">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a10e2-133">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a10e2-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a10e2-134">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a10e2-134">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a10e2-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a10e2-135">See also</span></span>

- [<span data-ttu-id="a10e2-136">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="a10e2-136">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="a10e2-137">MovedReferences, méthode</span><span class="sxs-lookup"><span data-stu-id="a10e2-137">MovedReferences Method</span></span>](icorprofilercallback-movedreferences-method.md)
- [<span data-ttu-id="a10e2-138">ICorProfilerCallback4, interface</span><span class="sxs-lookup"><span data-stu-id="a10e2-138">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
- [<span data-ttu-id="a10e2-139">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="a10e2-139">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="a10e2-140">Profilage</span><span class="sxs-lookup"><span data-stu-id="a10e2-140">Profiling</span></span>](index.md)
