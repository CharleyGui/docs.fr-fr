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
ms.openlocfilehash: 3755260b885768de6b5b2d6342c0ad590a95caff
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548668"
---
# <a name="icorprofilerinfo10isfrozenobject-method"></a><span data-ttu-id="b35a6-102">ICorProfilerInfo10 :: IsFrozenObject, méthode</span><span class="sxs-lookup"><span data-stu-id="b35a6-102">ICorProfilerInfo10::IsFrozenObject Method</span></span>

<span data-ttu-id="b35a6-103">À partir d’un ObjectID, détermine si l’objet se trouve dans un segment en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="b35a6-103">Given an ObjectID, determines whether the object is in a read-only segment.</span></span>

## <a name="syntax"></a><span data-ttu-id="b35a6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b35a6-104">Syntax</span></span>

```cpp
HRESULT IsFrozenObject( [in]  ObjectID objectId,
                        [out] BOOL *pbFrozen);
```

## <a name="parameters"></a><span data-ttu-id="b35a6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b35a6-105">Parameters</span></span>

- `objectId`

  <span data-ttu-id="b35a6-106">\[in] objet à examiner.</span><span class="sxs-lookup"><span data-stu-id="b35a6-106">\[in] The object to examine.</span></span>

- `pbFrozen`

  <span data-ttu-id="b35a6-107">\[out] `BOOL` valeur indiquant si l’objet se trouve dans un segment en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="b35a6-107">\[out] A `BOOL` indicating if the object is in a read-only segment.</span></span>

## <a name="requirements"></a><span data-ttu-id="b35a6-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b35a6-108">Requirements</span></span>

<span data-ttu-id="b35a6-109">**Plateformes :** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="b35a6-109">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="b35a6-110">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b35a6-110">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="b35a6-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b35a6-111">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="b35a6-112">**Versions de .net :**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b35a6-112">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="b35a6-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b35a6-113">See also</span></span>

- [<span data-ttu-id="b35a6-114">Interface ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="b35a6-114">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
