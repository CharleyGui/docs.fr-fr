---
title: ICorProfilerCallback::MovedReferences, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.MovedReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::MovedReferences
helpviewer_keywords:
- MovedReferences method [.NET Framework profiling]
- ICorProfilerCallback::MovedReferences method [.NET Framework profiling]
ms.assetid: 996c71ae-0676-4616-a085-84ebf507649d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c037f2509aaa0a5e4c3f7a844614742b6f21bec3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769137"
---
# <a name="icorprofilercallbackmovedreferences-method"></a><span data-ttu-id="a4a1f-102">ICorProfilerCallback::MovedReferences, méthode</span><span class="sxs-lookup"><span data-stu-id="a4a1f-102">ICorProfilerCallback::MovedReferences Method</span></span>
<span data-ttu-id="a4a1f-103">Appelée pour signaler la nouvelle disposition d'objets dans le tas suite à un garbage collection de compactage.</span><span class="sxs-lookup"><span data-stu-id="a4a1f-103">Called to report the new layout of objects in the heap as a result of a compacting garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4a1f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4a1f-104">Syntax</span></span>  
  
```cpp  
HRESULT MovedReferences(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ULONG    cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4a1f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a4a1f-105">Parameters</span></span>  
 `cMovedObjectIDRanges`  
 <span data-ttu-id="a4a1f-106">[in] Nombre de blocs d’objets contigus qui ont été déplacés à la suite du garbage collection de compactage.</span><span class="sxs-lookup"><span data-stu-id="a4a1f-106">[in] The number of blocks of contiguous objects that moved as the result of the compacting garbage collection.</span></span> <span data-ttu-id="a4a1f-107">Autrement dit, la valeur de `cMovedObjectIDRanges` est la taille totale des tableaux `oldObjectIDRangeStart`, `newObjectIDRangeStart` et `cObjectIDRangeLength`.</span><span class="sxs-lookup"><span data-stu-id="a4a1f-107">That is, the value of `cMovedObjectIDRanges` is the total size of the `oldObjectIDRangeStart`, `newObjectIDRangeStart`, and `cObjectIDRangeLength` arrays.</span></span>  
  
 <span data-ttu-id="a4a1f-108">Les trois arguments suivants de `MovedReferences` sont des tableaux parallèles.</span><span class="sxs-lookup"><span data-stu-id="a4a1f-108">The next three arguments of `MovedReferences` are parallel arrays.</span></span> <span data-ttu-id="a4a1f-109">En d'autres termes, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]` et `cObjectIDRangeLength[i]` concernent un bloc unique d'objets contigus.</span><span class="sxs-lookup"><span data-stu-id="a4a1f-109">In other words, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, and `cObjectIDRangeLength[i]` all concern a single block of contiguous objects.</span></span>  
  
 `oldObjectIDRangeStart`  
 <span data-ttu-id="a4a1f-110">[in] Tableau de valeurs `ObjectID`, chacune d'elles étant l'ancienne adresse de début (avant le garbage collection) d'un bloc d'objets actifs contigus dans la mémoire.</span><span class="sxs-lookup"><span data-stu-id="a4a1f-110">[in] An array of `ObjectID` values, each of which is the old (pre-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `newObjectIDRangeStart`  
 <span data-ttu-id="a4a1f-111">[in] Tableau de valeurs `ObjectID`, chacune d’elles étant la nouvelle adresse de début (après le garbage collection) d’un bloc d’objets actifs contigus dans la mémoire.</span><span class="sxs-lookup"><span data-stu-id="a4a1f-111">[in] An array of `ObjectID` values, each of which is the new (post-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="a4a1f-112">[in] Tableau d'entiers, chacun d'eux correspondant à la taille d'un bloc d'objets contigus dans la mémoire.</span><span class="sxs-lookup"><span data-stu-id="a4a1f-112">[in] An array of integers, each of which is the size of a block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="a4a1f-113">Une taille est spécifiée pour chaque bloc référencé dans les tableaux `oldObjectIDRangeStart` et `newObjectIDRangeStart`.</span><span class="sxs-lookup"><span data-stu-id="a4a1f-113">A size is specified for each block that is referenced in the `oldObjectIDRangeStart` and `newObjectIDRangeStart` arrays.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a4a1f-114">Notes</span><span class="sxs-lookup"><span data-stu-id="a4a1f-114">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a4a1f-115">Cette méthode signale les tailles en tant que `MAX_ULONG` pour les objets qui sont supérieurs à 4 Go sur les plateformes 64 bits.</span><span class="sxs-lookup"><span data-stu-id="a4a1f-115">This method reports sizes as `MAX_ULONG` for objects that are greater than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="a4a1f-116">Pour obtenir la taille des objets qui sont supérieurs à 4 Go, utilisez le [ICorProfilerCallback4::MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) méthode à la place.</span><span class="sxs-lookup"><span data-stu-id="a4a1f-116">To get the size of objects that are larger than 4 GB, use the [ICorProfilerCallback4::MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="a4a1f-117">Un garbage collection de compactage récupère la mémoire occupée par des objets morts et compacte cet espace libéré.</span><span class="sxs-lookup"><span data-stu-id="a4a1f-117">A compacting garbage collector reclaims the memory occupied by dead objects and compacts that freed space.</span></span> <span data-ttu-id="a4a1f-118">Par conséquent, les objets actifs peuvent être déplacés dans le tas, et les valeurs `ObjectID` distribuées par des notifications précédentes peuvent changer.</span><span class="sxs-lookup"><span data-stu-id="a4a1f-118">As a result, live objects might be moved within the heap, and `ObjectID` values distributed by previous notifications might change.</span></span>  
  
 <span data-ttu-id="a4a1f-119">Supposons qu'une valeur `ObjectID` existante (`oldObjectID`) se trouve dans la plage suivante :</span><span class="sxs-lookup"><span data-stu-id="a4a1f-119">Assume that an existing `ObjectID` value (`oldObjectID`) lies within the following range:</span></span>  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="a4a1f-120">Dans ce cas, l'offset du début de la plage au début de l'objet est le suivant :</span><span class="sxs-lookup"><span data-stu-id="a4a1f-120">In this case, the offset from the start of the range to the start of the object is as follows:</span></span>  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 <span data-ttu-id="a4a1f-121">Pour toute valeur d'`i` se trouvant dans la plage suivante :</span><span class="sxs-lookup"><span data-stu-id="a4a1f-121">For any value of `i` that is in the following range:</span></span>  
  
 <span data-ttu-id="a4a1f-122">0 <= `i` < `cMovedObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="a4a1f-122">0 <= `i` < `cMovedObjectIDRanges`</span></span>  
  
 <span data-ttu-id="a4a1f-123">Vous pouvez calculer le nouvel `ObjectID` comme suit :</span><span class="sxs-lookup"><span data-stu-id="a4a1f-123">you can calculate the new `ObjectID` as follows:</span></span>  
  
 <span data-ttu-id="a4a1f-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span><span class="sxs-lookup"><span data-stu-id="a4a1f-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span></span>  
  
 <span data-ttu-id="a4a1f-125">Aucune des valeurs `ObjectID` passées par `MovedReferences` n'est valide pendant le rappel lui-même, car le garbage collector peut être occupé à déplacer des objets depuis des anciens emplacements vers des nouveaux.</span><span class="sxs-lookup"><span data-stu-id="a4a1f-125">None of the `ObjectID` values passed by `MovedReferences` are valid during the callback itself, because the garbage collection might be in the middle of moving objects from old locations to new locations.</span></span> <span data-ttu-id="a4a1f-126">Les profileurs ne doivent donc pas essayer d'inspecter des objets pendant un appel de `MovedReferences`.</span><span class="sxs-lookup"><span data-stu-id="a4a1f-126">Therefore, profilers should not attempt to inspect objects during a `MovedReferences` call.</span></span> <span data-ttu-id="a4a1f-127">Un [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) rappel indique que tous les objets ont été déplacés vers leurs nouveaux emplacements et inspection peut être effectuée.</span><span class="sxs-lookup"><span data-stu-id="a4a1f-127">A [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) callback indicates that all objects have been moved to their new locations and inspection can be performed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4a1f-128">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a4a1f-128">Requirements</span></span>  
 <span data-ttu-id="a4a1f-129">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4a1f-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4a1f-130">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a4a1f-130">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a4a1f-131">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a4a1f-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a4a1f-132">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4a1f-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4a1f-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a4a1f-133">See also</span></span>

- [<span data-ttu-id="a4a1f-134">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="a4a1f-134">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="a4a1f-135">MovedReferences2, méthode</span><span class="sxs-lookup"><span data-stu-id="a4a1f-135">MovedReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)
- [<span data-ttu-id="a4a1f-136">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="a4a1f-136">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="a4a1f-137">Profilage</span><span class="sxs-lookup"><span data-stu-id="a4a1f-137">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
