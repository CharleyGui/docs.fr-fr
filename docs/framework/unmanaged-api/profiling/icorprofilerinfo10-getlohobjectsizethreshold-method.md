---
title: ICorProfilerInfo10::GetLOHObjectSizeThreshold
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.GetLOHObjectSizeThreshold
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 280f0a401f87f81e1ef9d4a2c85c06599442b5ec
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90543944"
---
# <a name="icorprofilerinfo10getlohobjectsizethreshold-method"></a><span data-ttu-id="92f33-102">ICorProfilerInfo10 :: GetLOHObjectSizeThreshold, méthode</span><span class="sxs-lookup"><span data-stu-id="92f33-102">ICorProfilerInfo10::GetLOHObjectSizeThreshold Method</span></span>

<span data-ttu-id="92f33-103">Obtient la valeur du seuil LOH (large Object Heap) configurée.</span><span class="sxs-lookup"><span data-stu-id="92f33-103">Gets the value of the configured large object heap (LOH) threshold.</span></span>

## <a name="syntax"></a><span data-ttu-id="92f33-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="92f33-104">Syntax</span></span>

```cpp
HRESULT GetLOHObjectSizeThreshold( [out] DWORD *pThreshold );
```

## <a name="parameters"></a><span data-ttu-id="92f33-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="92f33-105">Parameters</span></span>

- `pThreshold`

  <span data-ttu-id="92f33-106">\[out] seuil du tas d’objets volumineux, en octets.</span><span class="sxs-lookup"><span data-stu-id="92f33-106">\[out] The large object heap threshold in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="92f33-107">Notes</span><span class="sxs-lookup"><span data-stu-id="92f33-107">Remarks</span></span>

<span data-ttu-id="92f33-108">Les objets plus grands que le seuil du tas d’objets volumineux seront alloués sur le tas des objets volumineux.</span><span class="sxs-lookup"><span data-stu-id="92f33-108">Objects larger than the large object heap threshold will be allocated on the large object heap.</span></span> <span data-ttu-id="92f33-109">À compter de .NET Core 3,0 le seuil du tas d’objets volumineux est configurable, `pThreshold` contient la taille du seuil du tas d’objets volumineux actif, en octets.</span><span class="sxs-lookup"><span data-stu-id="92f33-109">Starting with .NET Core 3.0 the large object heap threshold is configurable, `pThreshold` will contain the active large object heap threshold size in bytes.</span></span>

## <a name="requirements"></a><span data-ttu-id="92f33-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="92f33-110">Requirements</span></span>

<span data-ttu-id="92f33-111">**Plateformes :** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="92f33-111">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="92f33-112">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="92f33-112">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="92f33-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92f33-113">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="92f33-114">**Versions de .net :**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92f33-114">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="92f33-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="92f33-115">See also</span></span>

- [<span data-ttu-id="92f33-116">Interface ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="92f33-116">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
