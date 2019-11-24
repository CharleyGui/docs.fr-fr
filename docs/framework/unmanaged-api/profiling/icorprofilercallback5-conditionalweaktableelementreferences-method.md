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
ms.openlocfilehash: ad721d28f6a7dc6ae0370ce10178990cb02fb9f9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430050"
---
# <a name="icorprofilercallback5conditionalweaktableelementreferences-method"></a><span data-ttu-id="d8039-102">ICorProfilerCallback5::ConditionalWeakTableElementReferences, méthode</span><span class="sxs-lookup"><span data-stu-id="d8039-102">ICorProfilerCallback5::ConditionalWeakTableElementReferences Method</span></span>

<span data-ttu-id="d8039-103">Identifie la fermeture transitive des objets référencés par ces racines via les références des champs des membres directs et via les dépendances de `ConditionalWeakTable`.</span><span class="sxs-lookup"><span data-stu-id="d8039-103">Identifies the transitive closure of objects referenced by those roots through both direct member field references and through `ConditionalWeakTable` dependencies.</span></span>

## <a name="syntax"></a><span data-ttu-id="d8039-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8039-104">Syntax</span></span>

```cpp
HRESULT ConditionalWeakTableElementReferences(
     [in]                     ULONG    cRootRefs,
     [in, size_is(cRootRefs)] ObjectID keyRefIds[],
     [in, size_is(cRootRefs)] ObjectID valueRefIds[],
     [in, size_is(cRootRefs)] GCHandleID rootIds[]
);
```

## <a name="parameters"></a><span data-ttu-id="d8039-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d8039-105">Parameters</span></span>

`cRootRefs`\
<span data-ttu-id="d8039-106">[en entrée] Le nombre d'éléments dans les tableaux `keyRefIds`, `valueRefIds` et `rootIds`.</span><span class="sxs-lookup"><span data-stu-id="d8039-106">[in] The number of elements in the `keyRefIds`, `valueRefIds`, and `rootIds` arrays.</span></span>

`keyRefIds`\
<span data-ttu-id="d8039-107">[en entrée] Un tableau d'ID d'objets, chacun contenant l'`ObjectID` pour l'élément principal de la paire de handles dépendants.</span><span class="sxs-lookup"><span data-stu-id="d8039-107">[in] An array of object IDs, each of which contains the `ObjectID` for the primary element in the dependent handle pair.</span></span>

`valueRefIds`\
<span data-ttu-id="d8039-108">[en entrée] Un tableau d'ID d'objets, chacun contenant l'`ObjectID` pour l'élément secondaire de la paire de handles dépendants.</span><span class="sxs-lookup"><span data-stu-id="d8039-108">[in] An array of object IDs, each of which contains the `ObjectID` for the secondary element in the dependent handle pair.</span></span> <span data-ttu-id="d8039-109">(`keyRefIds[i]` keeps `valueRefIds[i]` alive.)</span><span class="sxs-lookup"><span data-stu-id="d8039-109">(`keyRefIds[i]` keeps `valueRefIds[i]` alive.)</span></span>

`rootIds`\
<span data-ttu-id="d8039-110">[en entrée] Un tableau de valeurs de `GCHandleID` qui pointent vers un entier contenant des informations supplémentaires sur la racine de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="d8039-110">[in] An array of `GCHandleID` values that point to an integer that contains additional information about the garbage collection root.</span></span>

<span data-ttu-id="d8039-111">Aucune des valeurs d'`ObjectID` retournées par la méthode `ConditionalWeakTableElementReferences` ne sont valides pendant le rappel lui-même, car le récupérateur de mémoire peut être occupé à déplacer des objets depuis des anciens emplacements vers des nouveaux.</span><span class="sxs-lookup"><span data-stu-id="d8039-111">None of the `ObjectID` values returned by the `ConditionalWeakTableElementReferences` method are valid during the callback itself, because the garbage collector may be in the process of moving objects from old to new locations.</span></span> <span data-ttu-id="d8039-112">Les profileurs ne doivent donc pas essayer d'inspecter des objets pendant un appel de `ConditionalWeakTableElementReferences`.</span><span class="sxs-lookup"><span data-stu-id="d8039-112">Therefore, profilers should not attempt to inspect objects during a `ConditionalWeakTableElementReferences` call.</span></span> <span data-ttu-id="d8039-113">Quand l'état est `GarbageCollectionFinished`, tous les objets ont été déplacés à leur nouvel emplacement et une inspection peut être effectuée.</span><span class="sxs-lookup"><span data-stu-id="d8039-113">At `GarbageCollectionFinished`, all objects have been moved to their new locations, and inspection may be done.</span></span>

## <a name="example"></a><span data-ttu-id="d8039-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="d8039-114">Example</span></span>

<span data-ttu-id="d8039-115">The following code example demonstrates how to implement [ICorProfilerCallback5](icorprofilercallback5-interface.md) and use this method.</span><span class="sxs-lookup"><span data-stu-id="d8039-115">The following code example demonstrates how to implement [ICorProfilerCallback5](icorprofilercallback5-interface.md) and use this method.</span></span>

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

## <a name="remarks"></a><span data-ttu-id="d8039-116">Notes</span><span class="sxs-lookup"><span data-stu-id="d8039-116">Remarks</span></span>

<span data-ttu-id="d8039-117">A profiler for the .NET Framework 4.5 or later versions implements the [ICorProfilerCallback5](icorprofilercallback5-interface.md) interface and records the dependencies specified by the `ConditionalWeakTableElementReferences` method.</span><span class="sxs-lookup"><span data-stu-id="d8039-117">A profiler for the .NET Framework 4.5 or later versions implements the [ICorProfilerCallback5](icorprofilercallback5-interface.md) interface and records the dependencies specified by the `ConditionalWeakTableElementReferences` method.</span></span> <span data-ttu-id="d8039-118">`ICorProfilerCallback5` provides the complete set of dependencies among live objects represented by `ConditionalWeakTable` entries.</span><span class="sxs-lookup"><span data-stu-id="d8039-118">`ICorProfilerCallback5` provides the complete set of dependencies among live objects represented by `ConditionalWeakTable` entries.</span></span> <span data-ttu-id="d8039-119">These dependencies and the member field references specified by the [ICorProfilerCallback::ObjectReferences](icorprofilercallback-objectreferences-method.md) method enable a managed profiler to generate the full object graph of live objects.</span><span class="sxs-lookup"><span data-stu-id="d8039-119">These dependencies and the member field references specified by the [ICorProfilerCallback::ObjectReferences](icorprofilercallback-objectreferences-method.md) method enable a managed profiler to generate the full object graph of live objects.</span></span>

## <a name="requirements"></a><span data-ttu-id="d8039-120">spécifications</span><span class="sxs-lookup"><span data-stu-id="d8039-120">Requirements</span></span>

<span data-ttu-id="d8039-121">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8039-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="d8039-122">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d8039-122">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="d8039-123">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8039-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="d8039-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8039-124">See also</span></span>

- [<span data-ttu-id="d8039-125">ICorProfilerCallback5, interface</span><span class="sxs-lookup"><span data-stu-id="d8039-125">ICorProfilerCallback5 Interface</span></span>](icorprofilercallback5-interface.md)
