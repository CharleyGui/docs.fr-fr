---
title: ICorProfilerInfo10::IsFrozenObject
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.IsFrozenObject
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 21f9cb415f913a9c865a487f6e80523344db811e
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452186"
---
# <a name="icorprofilerinfo10isfrozenobject-method"></a><span data-ttu-id="5a6ce-102">ICorProfilerInfo10 :: IsFrozenObject, méthode</span><span class="sxs-lookup"><span data-stu-id="5a6ce-102">ICorProfilerInfo10::IsFrozenObject Method</span></span>

<span data-ttu-id="5a6ce-103">À partir d’un ObjectID, détermine si l’objet se trouve dans un segment en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="5a6ce-103">Given an ObjectID, determines whether the object is in a read-only segment.</span></span>

## <a name="syntax"></a><span data-ttu-id="5a6ce-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a6ce-104">Syntax</span></span>

```cpp
HRESULT IsFrozenObject( [in]  ObjectID objectId,
                        [out] BOOL *pbFrozen);
```

## <a name="parameters"></a><span data-ttu-id="5a6ce-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5a6ce-105">Parameters</span></span>

- `objectId`

  <span data-ttu-id="5a6ce-106">\[dans] objet à examiner.</span><span class="sxs-lookup"><span data-stu-id="5a6ce-106">\[in] The object to examine.</span></span>

- `pbFrozen`

  <span data-ttu-id="5a6ce-107">\[out] `BOOL` indiquant si l’objet se trouve dans un segment en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="5a6ce-107">\[out] A `BOOL` indicating if the object is in a read-only segment.</span></span>

## <a name="requirements"></a><span data-ttu-id="5a6ce-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5a6ce-108">Requirements</span></span>

<span data-ttu-id="5a6ce-109">**Plateformes :** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/install/dependencies.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="5a6ce-109">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?pivots=os-windows).</span></span>

<span data-ttu-id="5a6ce-110">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5a6ce-110">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="5a6ce-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a6ce-111">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="5a6ce-112">**Versions de .net :** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a6ce-112">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="5a6ce-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5a6ce-113">See also</span></span>

- [<span data-ttu-id="5a6ce-114">Interface ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="5a6ce-114">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
