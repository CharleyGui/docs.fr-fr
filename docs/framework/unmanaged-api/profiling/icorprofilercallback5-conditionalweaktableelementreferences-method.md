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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8fd904ba03fd5c652b1e5e5c7f763dab2b80e517
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636666"
---
# <a name="icorprofilercallback5conditionalweaktableelementreferences-method"></a>ICorProfilerCallback5::ConditionalWeakTableElementReferences, méthode

Identifie la fermeture transitive des objets référencés par ces racines via les références des champs des membres directs et via les dépendances de `ConditionalWeakTable`.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT ConditionalWeakTableElementReferences(
     [in]                     ULONG    cRootRefs,
     [in, size_is(cRootRefs)] ObjectID keyRefIds[],
     [in, size_is(cRootRefs)] ObjectID valueRefIds[],
     [in, size_is(cRootRefs)] GCHandleID rootIds[]
);
```

## <a name="parameters"></a>Paramètres

`cRootRefs`\
[en entrée] Le nombre d'éléments dans les tableaux `keyRefIds`, `valueRefIds` et `rootIds`.

`keyRefIds`\
[en entrée] Un tableau d'ID d'objets, chacun contenant l'`ObjectID` pour l'élément principal de la paire de handles dépendants.

`valueRefIds`\
[en entrée] Un tableau d'ID d'objets, chacun contenant l'`ObjectID` pour l'élément secondaire de la paire de handles dépendants. (`keyRefIds[i]` conserve `valueRefIds[i]` actif.)

`rootIds`\
[en entrée] Un tableau de valeurs de `GCHandleID` qui pointent vers un entier contenant des informations supplémentaires sur la racine de garbage collection.

Aucune des valeurs d'`ObjectID` retournées par la méthode `ConditionalWeakTableElementReferences` ne sont valides pendant le rappel lui-même, car le récupérateur de mémoire peut être occupé à déplacer des objets depuis des anciens emplacements vers des nouveaux. Les profileurs ne doivent donc pas essayer d'inspecter des objets pendant un appel de `ConditionalWeakTableElementReferences`. Quand l'état est `GarbageCollectionFinished`, tous les objets ont été déplacés à leur nouvel emplacement et une inspection peut être effectuée.

## <a name="example"></a>Exemple

L’exemple de code suivant montre comment implémenter [ICorProfilerCallback5](icorprofilercallback5-interface.md) et utilisez cette méthode.

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

## <a name="remarks"></a>Notes

Un profileur pour le [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] ou ultérieur implémente le [ICorProfilerCallback5](icorprofilercallback5-interface.md) interface et enregistre les dépendances spécifiées par le `ConditionalWeakTableElementReferences` (méthode). `ICorProfilerCallback5` fournit l’ensemble complet des dépendances entre les objets actifs représentés par `ConditionalWeakTable` entrées. Ces dépendances et le membre spécifiés par les références de champ la [ICorProfilerCallback::ObjectReferences](icorprofilercallback-objectreferences-method.md) méthode activer un profileur managé générer le graphique d’objet complet d’objets actifs.

## <a name="requirements"></a>Configuration requise

**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).

**En-tête :** CorProf.idl, CorProf.h

**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]

## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback5, interface](icorprofilercallback5-interface.md)
