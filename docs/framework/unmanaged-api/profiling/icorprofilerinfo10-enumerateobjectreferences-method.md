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
ms.openlocfilehash: a276ecfe65ed9752f39ed68a36e8e17a24255508
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558314"
---
# <a name="icorprofilerinfo10enumerateobjectreferences-method"></a><span data-ttu-id="1c021-102">ICorProfilerInfo10 :: EnumerateObjectReferences, méthode</span><span class="sxs-lookup"><span data-stu-id="1c021-102">ICorProfilerInfo10::EnumerateObjectReferences Method</span></span>

<span data-ttu-id="1c021-103">À partir d’un ObjectID, callback et ClientData :, énumère chaque référence d’objet (le cas échéant).</span><span class="sxs-lookup"><span data-stu-id="1c021-103">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span>

## <a name="syntax"></a><span data-ttu-id="1c021-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1c021-104">Syntax</span></span>

```cpp
HRESULT EnumerateObjectReferences( [in] ObjectID objectId,
                                   [in] ObjectReferenceCallback callback,
                                   [in] void* clientData);
```

## <a name="parameters"></a><span data-ttu-id="1c021-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1c021-105">Parameters</span></span>

- `objectId`

  <span data-ttu-id="1c021-106">\[in] objet sur lequel énumérer les références.</span><span class="sxs-lookup"><span data-stu-id="1c021-106">\[in] The object to enumerate references on.</span></span>

- `callback`

  <span data-ttu-id="1c021-107">\[in] fonction qui sera appelée avec les références pour l’objet.</span><span class="sxs-lookup"><span data-stu-id="1c021-107">\[in] The function that will be called with the references for the object.</span></span>

- `clientData`

  <span data-ttu-id="1c021-108">\[in] données fournies par le profileur à passer à la `callback` fonction.</span><span class="sxs-lookup"><span data-stu-id="1c021-108">\[in] Profiler-provided data to pass to the `callback` function.</span></span>

## <a name="remarks"></a><span data-ttu-id="1c021-109">Notes</span><span class="sxs-lookup"><span data-stu-id="1c021-109">Remarks</span></span>

<span data-ttu-id="1c021-110">La `EnumerateObjectReferences` méthode est similaire à [ObjectReferences](icorprofilercallback-objectreferences-method.md), à ceci près qu’elle parcourt les références à la demande pour le profileur au lieu de préallouer un tableau pour stocker les références.</span><span class="sxs-lookup"><span data-stu-id="1c021-110">The `EnumerateObjectReferences` method is similar to [ObjectReferences](icorprofilercallback-objectreferences-method.md), except that it walks the references on demand for the profiler instead of pre-allocating an array to store the references.</span></span>

## <a name="requirements"></a><span data-ttu-id="1c021-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="1c021-111">Requirements</span></span>

<span data-ttu-id="1c021-112">**Plateformes :** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="1c021-112">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="1c021-113">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1c021-113">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="1c021-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c021-114">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="1c021-115">**Versions de .net :**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c021-115">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="1c021-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1c021-116">See also</span></span>

- [<span data-ttu-id="1c021-117">Interface ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="1c021-117">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
