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
ms.openlocfilehash: ac193b6b78434245b8f11a4f627b4e1992feb8a7
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69661271"
---
# <a name="icorprofilerinfo10enumerateobjectreferences-method"></a><span data-ttu-id="c0253-102">ICorProfilerInfo10:: EnumerateObjectReferences, méthode</span><span class="sxs-lookup"><span data-stu-id="c0253-102">ICorProfilerInfo10::EnumerateObjectReferences Method</span></span>

<span data-ttu-id="c0253-103">À partir d’un ObjectID, callback et ClientData:, énumère chaque référence d’objet (le cas échéant).</span><span class="sxs-lookup"><span data-stu-id="c0253-103">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span>

## <a name="syntax"></a><span data-ttu-id="c0253-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c0253-104">Syntax</span></span>

```cpp
HRESULT EnumerateObjectReferences( [in] ObjectID objectId,
                                   [in] ObjectReferenceCallback callback,
                                   [in] void* clientData);
```

#### <a name="parameters"></a><span data-ttu-id="c0253-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c0253-105">Parameters</span></span>

`objectId` \
<span data-ttu-id="c0253-106">dans Objet sur lequel énumérer les références.</span><span class="sxs-lookup"><span data-stu-id="c0253-106">[in] The object to enumerate references on.</span></span>

`callback` \
<span data-ttu-id="c0253-107">dans Fonction qui sera appelée avec les références pour l’objet.</span><span class="sxs-lookup"><span data-stu-id="c0253-107">[in] The function that will be called with the references for the object.</span></span>

`clientData` \
<span data-ttu-id="c0253-108">dans Données fournies par le profileur à passer `callback` à la fonction.</span><span class="sxs-lookup"><span data-stu-id="c0253-108">[in] Profiler-provided data to pass to the `callback` function.</span></span>

## <a name="remarks"></a><span data-ttu-id="c0253-109">Notes</span><span class="sxs-lookup"><span data-stu-id="c0253-109">Remarks</span></span>

<span data-ttu-id="c0253-110">La `EnumerateObjectReferences` méthode est similaire à [ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md), à ceci près qu’elle parcourt les références à la demande pour le profileur au lieu de préallouer un tableau pour stocker les références.</span><span class="sxs-lookup"><span data-stu-id="c0253-110">The `EnumerateObjectReferences` method is similar to [ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md), except that it walks the references on demand for the profiler instead of pre-allocating an array to store the references.</span></span>

## <a name="requirements"></a><span data-ttu-id="c0253-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c0253-111">Requirements</span></span>

<span data-ttu-id="c0253-112">**Plateformes** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="c0253-112">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>

<span data-ttu-id="c0253-113">**En-tête :** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c0253-113">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="c0253-114">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c0253-114">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="c0253-115">**Versions de .net:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0253-115">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="c0253-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0253-116">See also</span></span>

- [<span data-ttu-id="c0253-117">Interface ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="c0253-117">ICorProfilerInfo10 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
