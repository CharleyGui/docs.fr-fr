---
title: ICorProfilerCallback2::RootReferences2, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.RootReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::RootReferences2
helpviewer_keywords:
- RootReferences2 method [.NET Framework profiling]
- ICorProfilerCallback2::RootReferences2 method [.NET Framework profiling]
ms.assetid: 55a2f907-d216-42eb-8f2f-e5d59c2eebd6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 563a2e19c9c254870b3e767253a276a201e631a6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779302"
---
# <a name="icorprofilercallback2rootreferences2-method"></a><span data-ttu-id="981e8-102">ICorProfilerCallback2::RootReferences2, méthode</span><span class="sxs-lookup"><span data-stu-id="981e8-102">ICorProfilerCallback2::RootReferences2 Method</span></span>
<span data-ttu-id="981e8-103">Informe le profileur sur les références racine après qu’un garbage collection s’est produite.</span><span class="sxs-lookup"><span data-stu-id="981e8-103">Notifies the profiler about root references after a garbage collection has occurred.</span></span> <span data-ttu-id="981e8-104">Cette méthode est une extension de la [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="981e8-104">This method is an extension of the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="981e8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="981e8-105">Syntax</span></span>  
  
```cpp  
HRESULT RootReferences2(  
    [in] ULONG  cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_KIND rootKinds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_FLAGS rootFlags[],  
    [in, size_is(cRootRefs)] UINT_PTR rootIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="981e8-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="981e8-106">Parameters</span></span>  
 `cRootRefs`  
 <span data-ttu-id="981e8-107">[in] Le nombre d’éléments dans le `rootRefIds`, `rootKinds`, `rootFlags`, et `rootIds` tableaux.</span><span class="sxs-lookup"><span data-stu-id="981e8-107">[in] The number of elements in the `rootRefIds`, `rootKinds`, `rootFlags`, and `rootIds` arrays.</span></span>  
  
 `rootRefIds`  
 <span data-ttu-id="981e8-108">[in] Tableau d’ID d’objet, chacun d'entre eux fait référence à un objet statique ou un objet sur la pile.</span><span class="sxs-lookup"><span data-stu-id="981e8-108">[in] An array of object IDs, each of which references either a static object or an object on the stack.</span></span> <span data-ttu-id="981e8-109">Éléments dans le `rootKinds` tableau fournissent des informations pour classer les éléments correspondants dans le `rootRefIds` tableau.</span><span class="sxs-lookup"><span data-stu-id="981e8-109">Elements in the `rootKinds` array provide information to classify corresponding elements in the `rootRefIds` array.</span></span>  
  
 `rootKinds`  
 <span data-ttu-id="981e8-110">[in] Un tableau de [COR_PRF_GC_ROOT_KIND](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md) valeurs qui indiquent le type de la racine de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="981e8-110">[in] An array of [COR_PRF_GC_ROOT_KIND](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md) values that indicate the type of the garbage collection root.</span></span>  
  
 `rootFlags`  
 <span data-ttu-id="981e8-111">[in] Un tableau de [COR_PRF_GC_ROOT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md) valeurs qui décrivent les propriétés d’une racine de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="981e8-111">[in] An array of [COR_PRF_GC_ROOT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md) values that describe the properties of a garbage collection root.</span></span>  
  
 `rootIds`  
 <span data-ttu-id="981e8-112">[in] Un tableau de valeurs UINT_PTR qui pointent vers un entier qui contient des informations supplémentaires sur la racine de garbage collection, selon la valeur de la `rootKinds` paramètre.</span><span class="sxs-lookup"><span data-stu-id="981e8-112">[in] An array of UINT_PTR values that point to an integer that contains additional information about the garbage collection root, depending on the value of the `rootKinds` parameter.</span></span>  
  
 <span data-ttu-id="981e8-113">Si le type de la racine est une pile, l’ID de la racine est pour la fonction qui contient la variable.</span><span class="sxs-lookup"><span data-stu-id="981e8-113">If the type of the root is a stack, the root ID is for the function that contains the variable.</span></span> <span data-ttu-id="981e8-114">Si cet ID racine est 0, la fonction est une fonction sans nom qui est interne au CLR.</span><span class="sxs-lookup"><span data-stu-id="981e8-114">If that root ID is 0, the function is an unnamed function that is internal to the CLR.</span></span> <span data-ttu-id="981e8-115">Si le type de la racine est un handle, l’ID de la racine est pour le handle de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="981e8-115">If the type of the root is a handle, the root ID is for the garbage collection handle.</span></span> <span data-ttu-id="981e8-116">Pour les autres types racine, l’ID est une valeur opaque et doit être ignorée.</span><span class="sxs-lookup"><span data-stu-id="981e8-116">For the other root types, the ID is an opaque value and should be ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="981e8-117">Notes</span><span class="sxs-lookup"><span data-stu-id="981e8-117">Remarks</span></span>  
 <span data-ttu-id="981e8-118">Le `rootRefIds`, `rootKinds`, `rootFlags`, et `rootIds` tableaux sont des tableaux parallèles.</span><span class="sxs-lookup"><span data-stu-id="981e8-118">The `rootRefIds`, `rootKinds`, `rootFlags`, and `rootIds` arrays are parallel arrays.</span></span> <span data-ttu-id="981e8-119">Autrement dit, `rootRefIds[i]`, `rootKinds[i]`, `rootFlags[i]`, et `rootIds[i]` concernent la même racine.</span><span class="sxs-lookup"><span data-stu-id="981e8-119">That is, `rootRefIds[i]`, `rootKinds[i]`, `rootFlags[i]`, and `rootIds[i]` all concern the same root.</span></span>  
  
 <span data-ttu-id="981e8-120">Les deux `RootReferences` et `RootReferences2` sont appelées pour notifier le profileur.</span><span class="sxs-lookup"><span data-stu-id="981e8-120">Both `RootReferences` and `RootReferences2` are called to notify the profiler.</span></span> <span data-ttu-id="981e8-121">Les profileurs normalement implémenteront l’un ou l’autre méthode, mais pas les deux, car les informations passées dans `RootReferences2` est un sur-ensemble de celles passées dans `RootReferences`.</span><span class="sxs-lookup"><span data-stu-id="981e8-121">Profilers will normally implement one method or the other, but not both, because the information passed in `RootReferences2` is a superset of that passed in `RootReferences`.</span></span>  
  
 <span data-ttu-id="981e8-122">Il est possible pour les entrées dans `rootRefIds` à zéro, ce qui implique que la référence de racine correspondante est null et ne fait pas référence à un objet sur le tas managé.</span><span class="sxs-lookup"><span data-stu-id="981e8-122">It is possible for entries in `rootRefIds` to be zero, which implies that the corresponding root reference is null and does not refer to an object on the managed heap.</span></span>  
  
 <span data-ttu-id="981e8-123">Les ID d’objet retourné par `RootReferences2` ne sont pas valides pendant le rappel lui-même, car le garbage collection peut être occupé à déplacer les objets des anciennes adresses vers de nouvelles adresses.</span><span class="sxs-lookup"><span data-stu-id="981e8-123">The object IDs returned by `RootReferences2` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects from old addresses to new addresses.</span></span> <span data-ttu-id="981e8-124">Les profileurs ne doivent donc pas essayer d'inspecter des objets pendant un appel de `RootReferences2`.</span><span class="sxs-lookup"><span data-stu-id="981e8-124">Therefore, profilers should not attempt to inspect objects during a `RootReferences2` call.</span></span> <span data-ttu-id="981e8-125">Lorsque [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) est appelée, tous les objets ont été déplacés vers leurs nouveaux emplacements et peuvent être inspectés sans risque.</span><span class="sxs-lookup"><span data-stu-id="981e8-125">When [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) is called, all objects have been moved to their new locations and can be safely inspected.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="981e8-126">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="981e8-126">Requirements</span></span>  
 <span data-ttu-id="981e8-127">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="981e8-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="981e8-128">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="981e8-128">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="981e8-129">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="981e8-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="981e8-130">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="981e8-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="981e8-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="981e8-131">See also</span></span>

- [<span data-ttu-id="981e8-132">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="981e8-132">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="981e8-133">ICorProfilerCallback2, interface</span><span class="sxs-lookup"><span data-stu-id="981e8-133">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
