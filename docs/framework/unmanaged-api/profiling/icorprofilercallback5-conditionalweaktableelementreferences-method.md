---
title: ICorProfilerCallback5::ConditionalWeakTableElementReferences, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback5.ConditionalWeakTableReferences
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ConditionalWeakTableElementReferences
helpviewer_keywords:
- ConditionalWeakTableElementReferences method, ICorProfilerCallback5 interface [.NET Framework profiling]
- ICorProfilerCallback5::ConditionalWeakTableElementReferences method [.NET Framework profiling]
ms.assetid: 532c7a02-a9de-4cea-bb2b-7f470da594de
topic_type:
- apiref
ms.openlocfilehash: 17fbc99b30921f795c1f7ff882ec73432aade8c6
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499244"
---
# <a name="icorprofilercallback5conditionalweaktableelementreferences-method"></a><span data-ttu-id="dded5-102">ICorProfilerCallback5::ConditionalWeakTableElementReferences, méthode</span><span class="sxs-lookup"><span data-stu-id="dded5-102">ICorProfilerCallback5::ConditionalWeakTableElementReferences Method</span></span>

<span data-ttu-id="dded5-103">Identifie la fermeture transitive des objets référencés par ces racines via les références des champs des membres directs et via les dépendances de `ConditionalWeakTable`.</span><span class="sxs-lookup"><span data-stu-id="dded5-103">Identifies the transitive closure of objects referenced by those roots through both direct member field references and through `ConditionalWeakTable` dependencies.</span></span>

## <a name="syntax"></a><span data-ttu-id="dded5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dded5-104">Syntax</span></span>

```cpp
HRESULT ConditionalWeakTableElementReferences(
     [in]                     ULONG    cRootRefs,
     [in, size_is(cRootRefs)] ObjectID keyRefIds[],
     [in, size_is(cRootRefs)] ObjectID valueRefIds[],
     [in, size_is(cRootRefs)] GCHandleID rootIds[]
);
```

## <a name="parameters"></a><span data-ttu-id="dded5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="dded5-105">Parameters</span></span>

`cRootRefs`\
<span data-ttu-id="dded5-106">[en entrée] Le nombre d'éléments dans les tableaux `keyRefIds`, `valueRefIds` et `rootIds`.</span><span class="sxs-lookup"><span data-stu-id="dded5-106">[in] The number of elements in the `keyRefIds`, `valueRefIds`, and `rootIds` arrays.</span></span>

`keyRefIds`\
<span data-ttu-id="dded5-107">[en entrée] Un tableau d'ID d'objets, chacun contenant l'`ObjectID` pour l'élément principal de la paire de handles dépendants.</span><span class="sxs-lookup"><span data-stu-id="dded5-107">[in] An array of object IDs, each of which contains the `ObjectID` for the primary element in the dependent handle pair.</span></span>

`valueRefIds`\
<span data-ttu-id="dded5-108">[en entrée] Un tableau d'ID d'objets, chacun contenant l'`ObjectID` pour l'élément secondaire de la paire de handles dépendants.</span><span class="sxs-lookup"><span data-stu-id="dded5-108">[in] An array of object IDs, each of which contains the `ObjectID` for the secondary element in the dependent handle pair.</span></span> <span data-ttu-id="dded5-109">( `keyRefIds[i]` reste `valueRefIds[i]` actif.)</span><span class="sxs-lookup"><span data-stu-id="dded5-109">(`keyRefIds[i]` keeps `valueRefIds[i]` alive.)</span></span>

`rootIds`\
<span data-ttu-id="dded5-110">[en entrée] Un tableau de valeurs de `GCHandleID` qui pointent vers un entier contenant des informations supplémentaires sur la racine de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="dded5-110">[in] An array of `GCHandleID` values that point to an integer that contains additional information about the garbage collection root.</span></span>

<span data-ttu-id="dded5-111">Aucune des valeurs d'`ObjectID` retournées par la méthode `ConditionalWeakTableElementReferences` ne sont valides pendant le rappel lui-même, car le récupérateur de mémoire peut être occupé à déplacer des objets depuis des anciens emplacements vers des nouveaux.</span><span class="sxs-lookup"><span data-stu-id="dded5-111">None of the `ObjectID` values returned by the `ConditionalWeakTableElementReferences` method are valid during the callback itself, because the garbage collector may be in the process of moving objects from old to new locations.</span></span> <span data-ttu-id="dded5-112">Les profileurs ne doivent donc pas essayer d'inspecter des objets pendant un appel de `ConditionalWeakTableElementReferences`.</span><span class="sxs-lookup"><span data-stu-id="dded5-112">Therefore, profilers should not attempt to inspect objects during a `ConditionalWeakTableElementReferences` call.</span></span> <span data-ttu-id="dded5-113">Quand l'état est `GarbageCollectionFinished`, tous les objets ont été déplacés à leur nouvel emplacement et une inspection peut être effectuée.</span><span class="sxs-lookup"><span data-stu-id="dded5-113">At `GarbageCollectionFinished`, all objects have been moved to their new locations, and inspection may be done.</span></span>

## <a name="example"></a><span data-ttu-id="dded5-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="dded5-114">Example</span></span>

<span data-ttu-id="dded5-115">L’exemple de code suivant montre comment implémenter [ICorProfilerCallback5](icorprofilercallback5-interface.md) et utiliser cette méthode.</span><span class="sxs-lookup"><span data-stu-id="dded5-115">The following code example demonstrates how to implement [ICorProfilerCallback5](icorprofilercallback5-interface.md) and use this method.</span></span>

```cpp
HRESULT Callback5Impl::ConditionalWeakTableElementReferences(
    ULONG      cRootRefs,
    ObjectID   keyRefIds[],
    ObjectID   valueRefIds[],
    GCHandleID rootIds[])
{
    printf("Callback5Impl::ConditionalWeakTableElementReferences called\n");
    for (unsigned int i = 0; i < cRootRefs; ++i)
    {
        // Save dependency to XML for later retrieval
        PersistDependencyToXml(rootIds[i], keyRefIds[i], valueRefIds[i]);
        // or store dependency to an internal map
        m_cwt_deps->add_dep(rootIds[i], keyRefIds[i], valueRefIds[i]);
        // or add arc to object graph
        m_obj_graph->add_arc(keyRefIds[i], valueRefIds[i], rootIds[i]);
    }
    return S_OK;
}
```

## <a name="remarks"></a><span data-ttu-id="dded5-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="dded5-116">Remarks</span></span>

<span data-ttu-id="dded5-117">Un profileur pour le .NET Framework 4,5 ou les versions ultérieures implémente l’interface [ICorProfilerCallback5](icorprofilercallback5-interface.md) et enregistre les dépendances spécifiées par la `ConditionalWeakTableElementReferences` méthode.</span><span class="sxs-lookup"><span data-stu-id="dded5-117">A profiler for the .NET Framework 4.5 or later versions implements the [ICorProfilerCallback5](icorprofilercallback5-interface.md) interface and records the dependencies specified by the `ConditionalWeakTableElementReferences` method.</span></span> <span data-ttu-id="dded5-118">`ICorProfilerCallback5`fournit l’ensemble complet des dépendances entre les objets actifs représentés par les `ConditionalWeakTable` entrées.</span><span class="sxs-lookup"><span data-stu-id="dded5-118">`ICorProfilerCallback5` provides the complete set of dependencies among live objects represented by `ConditionalWeakTable` entries.</span></span> <span data-ttu-id="dded5-119">Ces dépendances et les références de champ de membre spécifiées par la méthode [ICorProfilerCallback :: ObjectReferences](icorprofilercallback-objectreferences-method.md) permettent à un profileur managé de générer le graphique d’objet complet d’objets actifs.</span><span class="sxs-lookup"><span data-stu-id="dded5-119">These dependencies and the member field references specified by the [ICorProfilerCallback::ObjectReferences](icorprofilercallback-objectreferences-method.md) method enable a managed profiler to generate the full object graph of live objects.</span></span>

## <a name="requirements"></a><span data-ttu-id="dded5-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="dded5-120">Requirements</span></span>

<span data-ttu-id="dded5-121">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dded5-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="dded5-122">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dded5-122">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="dded5-123">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dded5-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="dded5-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dded5-124">See also</span></span>

- [<span data-ttu-id="dded5-125">ICorProfilerCallback5, interface</span><span class="sxs-lookup"><span data-stu-id="dded5-125">ICorProfilerCallback5 Interface</span></span>](icorprofilercallback5-interface.md)
