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
ms.openlocfilehash: 95473a8ce8d5fd7540228ecd9767448e51b5b326
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868982"
---
# <a name="icorprofilerinfo10getlohobjectsizethreshold-method"></a><span data-ttu-id="48d98-102">ICorProfilerInfo10 :: GetLOHObjectSizeThreshold, méthode</span><span class="sxs-lookup"><span data-stu-id="48d98-102">ICorProfilerInfo10::GetLOHObjectSizeThreshold Method</span></span>

<span data-ttu-id="48d98-103">Obtient la valeur du seuil LOH (large Object Heap) configurée.</span><span class="sxs-lookup"><span data-stu-id="48d98-103">Gets the value of the configured large object heap (LOH) threshold.</span></span>

## <a name="syntax"></a><span data-ttu-id="48d98-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="48d98-104">Syntax</span></span>

```cpp
HRESULT GetLOHObjectSizeThreshold( [out] DWORD *pThreshold );
```

## <a name="parameters"></a><span data-ttu-id="48d98-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="48d98-105">Parameters</span></span>

- `pThreshold`

  <span data-ttu-id="48d98-106">\[out] le seuil du tas d’objets volumineux, en octets.</span><span class="sxs-lookup"><span data-stu-id="48d98-106">\[out] The large object heap threshold in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="48d98-107">Notes</span><span class="sxs-lookup"><span data-stu-id="48d98-107">Remarks</span></span>

<span data-ttu-id="48d98-108">Les objets plus grands que le seuil du tas d’objets volumineux seront alloués sur le tas des objets volumineux.</span><span class="sxs-lookup"><span data-stu-id="48d98-108">Objects larger than the large object heap threshold will be allocated on the large object heap.</span></span> <span data-ttu-id="48d98-109">À compter de .NET Core 3,0, le seuil du tas d’objets volumineux est configurable, `pThreshold` contient la taille du seuil du tas d’objets volumineux actif, en octets.</span><span class="sxs-lookup"><span data-stu-id="48d98-109">Starting with .NET Core 3.0 the large object heap threshold is configurable, `pThreshold` will contain the active large object heap threshold size in bytes.</span></span>

## <a name="requirements"></a><span data-ttu-id="48d98-110">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="48d98-110">Requirements</span></span>

<span data-ttu-id="48d98-111">**Plateformes :** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="48d98-111">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>

<span data-ttu-id="48d98-112">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="48d98-112">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="48d98-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="48d98-113">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="48d98-114">**Versions de .net :** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48d98-114">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="48d98-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="48d98-115">See also</span></span>

- [<span data-ttu-id="48d98-116">Interface ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="48d98-116">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
