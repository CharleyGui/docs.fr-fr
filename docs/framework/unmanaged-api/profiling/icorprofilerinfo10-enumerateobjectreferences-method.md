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
ms.openlocfilehash: 9aadf9701444d215291b6fc19cc8cd61ca832837
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452238"
---
# <a name="icorprofilerinfo10enumerateobjectreferences-method"></a><span data-ttu-id="bb2b7-102">ICorProfilerInfo10 :: EnumerateObjectReferences, méthode</span><span class="sxs-lookup"><span data-stu-id="bb2b7-102">ICorProfilerInfo10::EnumerateObjectReferences Method</span></span>

<span data-ttu-id="bb2b7-103">À partir d’un ObjectID, callback et ClientData :, énumère chaque référence d’objet (le cas échéant).</span><span class="sxs-lookup"><span data-stu-id="bb2b7-103">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span>

## <a name="syntax"></a><span data-ttu-id="bb2b7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb2b7-104">Syntax</span></span>

```cpp
HRESULT EnumerateObjectReferences( [in] ObjectID objectId,
                                   [in] ObjectReferenceCallback callback,
                                   [in] void* clientData);
```

## <a name="parameters"></a><span data-ttu-id="bb2b7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bb2b7-105">Parameters</span></span>

- `objectId`

  <span data-ttu-id="bb2b7-106">\[in] objet sur lequel énumérer les références.</span><span class="sxs-lookup"><span data-stu-id="bb2b7-106">\[in] The object to enumerate references on.</span></span>

- `callback`

  <span data-ttu-id="bb2b7-107">\[dans] la fonction qui sera appelée avec les références pour l’objet.</span><span class="sxs-lookup"><span data-stu-id="bb2b7-107">\[in] The function that will be called with the references for the object.</span></span>

- `clientData`

  <span data-ttu-id="bb2b7-108">\[dans] données fournies par le profileur à passer à la fonction `callback`.</span><span class="sxs-lookup"><span data-stu-id="bb2b7-108">\[in] Profiler-provided data to pass to the `callback` function.</span></span>

## <a name="remarks"></a><span data-ttu-id="bb2b7-109">Notes</span><span class="sxs-lookup"><span data-stu-id="bb2b7-109">Remarks</span></span>

<span data-ttu-id="bb2b7-110">La méthode `EnumerateObjectReferences` est semblable à [ObjectReferences](icorprofilercallback-objectreferences-method.md), à ceci près qu’elle parcourt les références à la demande pour le profileur au lieu de préallouer un tableau pour stocker les références.</span><span class="sxs-lookup"><span data-stu-id="bb2b7-110">The `EnumerateObjectReferences` method is similar to [ObjectReferences](icorprofilercallback-objectreferences-method.md), except that it walks the references on demand for the profiler instead of pre-allocating an array to store the references.</span></span>

## <a name="requirements"></a><span data-ttu-id="bb2b7-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="bb2b7-111">Requirements</span></span>

<span data-ttu-id="bb2b7-112">**Plateformes :** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/install/dependencies.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="bb2b7-112">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?pivots=os-windows).</span></span>

<span data-ttu-id="bb2b7-113">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bb2b7-113">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="bb2b7-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bb2b7-114">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="bb2b7-115">**Versions de .net :** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb2b7-115">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="bb2b7-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bb2b7-116">See also</span></span>

- [<span data-ttu-id="bb2b7-117">Interface ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="bb2b7-117">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
