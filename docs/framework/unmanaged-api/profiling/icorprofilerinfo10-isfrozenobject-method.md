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
ms.openlocfilehash: b6dabefceba038a129148f7ba36d4ffcfc425c80
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790036"
---
# <a name="icorprofilerinfo10isfrozenobject-method"></a><span data-ttu-id="e4731-102">ICorProfilerInfo10 :: IsFrozenObject, méthode</span><span class="sxs-lookup"><span data-stu-id="e4731-102">ICorProfilerInfo10::IsFrozenObject Method</span></span>

<span data-ttu-id="e4731-103">À partir d’un ObjectID, détermine si l’objet se trouve dans un segment en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="e4731-103">Given an ObjectID, determines whether the object is in a read-only segment.</span></span>

## <a name="syntax"></a><span data-ttu-id="e4731-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4731-104">Syntax</span></span>

```cpp
HRESULT IsFrozenObject( [in]  ObjectID objectId,
                        [out] BOOL *pbFrozen);
```

## <a name="parameters"></a><span data-ttu-id="e4731-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="e4731-105">Parameters</span></span>

- `objectId`

  <span data-ttu-id="e4731-106">\[dans] objet à examiner.</span><span class="sxs-lookup"><span data-stu-id="e4731-106">\[in] The object to examine.</span></span>

- `pbFrozen`

  <span data-ttu-id="e4731-107">\[out] `BOOL` indiquant si l’objet se trouve dans un segment en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="e4731-107">\[out] A `BOOL` indicating if the object is in a read-only segment.</span></span>

## <a name="requirements"></a><span data-ttu-id="e4731-108">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="e4731-108">Requirements</span></span>

<span data-ttu-id="e4731-109">**Plateformes :** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="e4731-109">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>

<span data-ttu-id="e4731-110">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e4731-110">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="e4731-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e4731-111">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="e4731-112">**Versions de .net :** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4731-112">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="e4731-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e4731-113">See also</span></span>

- [<span data-ttu-id="e4731-114">Interface ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="e4731-114">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
