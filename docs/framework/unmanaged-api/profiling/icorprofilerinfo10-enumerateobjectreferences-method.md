---
title: ICorProfilerInfo10::EnumerateObjectReferences
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.EnumerateObjectReferences
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 7fd62e0d3d9173f3b75882131e57126075c0677f
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863307"
---
# <a name="icorprofilerinfo10enumerateobjectreferences-method"></a><span data-ttu-id="44f1c-102">ICorProfilerInfo10 :: EnumerateObjectReferences, méthode</span><span class="sxs-lookup"><span data-stu-id="44f1c-102">ICorProfilerInfo10::EnumerateObjectReferences Method</span></span>

<span data-ttu-id="44f1c-103">À partir d’un ObjectID, callback et ClientData :, énumère chaque référence d’objet (le cas échéant).</span><span class="sxs-lookup"><span data-stu-id="44f1c-103">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span>

## <a name="syntax"></a><span data-ttu-id="44f1c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44f1c-104">Syntax</span></span>

```cpp
HRESULT EnumerateObjectReferences( [in] ObjectID objectId,
                                   [in] ObjectReferenceCallback callback,
                                   [in] void* clientData);
```

## <a name="parameters"></a><span data-ttu-id="44f1c-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="44f1c-105">Parameters</span></span>

- `objectId`

  <span data-ttu-id="44f1c-106">\[in] objet sur lequel énumérer les références.</span><span class="sxs-lookup"><span data-stu-id="44f1c-106">\[in] The object to enumerate references on.</span></span>

- `callback`

  <span data-ttu-id="44f1c-107">\[dans] la fonction qui sera appelée avec les références pour l’objet.</span><span class="sxs-lookup"><span data-stu-id="44f1c-107">\[in] The function that will be called with the references for the object.</span></span>

- `clientData`

  <span data-ttu-id="44f1c-108">\[dans] données fournies par le profileur à passer à la fonction `callback`.</span><span class="sxs-lookup"><span data-stu-id="44f1c-108">\[in] Profiler-provided data to pass to the `callback` function.</span></span>

## <a name="remarks"></a><span data-ttu-id="44f1c-109">Notes</span><span class="sxs-lookup"><span data-stu-id="44f1c-109">Remarks</span></span>

<span data-ttu-id="44f1c-110">La méthode `EnumerateObjectReferences` est semblable à [ObjectReferences](icorprofilercallback-objectreferences-method.md), à ceci près qu’elle parcourt les références à la demande pour le profileur au lieu de préallouer un tableau pour stocker les références.</span><span class="sxs-lookup"><span data-stu-id="44f1c-110">The `EnumerateObjectReferences` method is similar to [ObjectReferences](icorprofilercallback-objectreferences-method.md), except that it walks the references on demand for the profiler instead of pre-allocating an array to store the references.</span></span>

## <a name="requirements"></a><span data-ttu-id="44f1c-111">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="44f1c-111">Requirements</span></span>

<span data-ttu-id="44f1c-112">**Plateformes :** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="44f1c-112">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>

<span data-ttu-id="44f1c-113">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="44f1c-113">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="44f1c-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="44f1c-114">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="44f1c-115">**Versions de .net :** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44f1c-115">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="44f1c-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="44f1c-116">See also</span></span>

- [<span data-ttu-id="44f1c-117">Interface ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="44f1c-117">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
