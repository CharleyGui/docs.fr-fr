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
ms.openlocfilehash: d6b6575cf04635b40b504b11bc415f61f05b4205
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68974019"
---
# <a name="icorprofilerinfo10getlohobjectsizethreshold-method"></a><span data-ttu-id="13c0e-102">ICorProfilerInfo10:: GetLOHObjectSizeThreshold, méthode</span><span class="sxs-lookup"><span data-stu-id="13c0e-102">ICorProfilerInfo10::GetLOHObjectSizeThreshold Method</span></span>
  
 <span data-ttu-id="13c0e-103">Obtient la valeur du seuil LOH (large Object Heap) configurée.</span><span class="sxs-lookup"><span data-stu-id="13c0e-103">Gets the value of the configured large object heap (LOH) threshold.</span></span>   
  
## <a name="syntax"></a><span data-ttu-id="13c0e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="13c0e-104">Syntax</span></span>  
  
```cpp
HRESULT GetLOHObjectSizeThreshold( [out] DWORD *pThreshold );
```  
  
#### <a name="parameters"></a><span data-ttu-id="13c0e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="13c0e-105">Parameters</span></span>  
 `pThreshold` \
 <span data-ttu-id="13c0e-106">à Seuil du tas d’objets volumineux, en octets.</span><span class="sxs-lookup"><span data-stu-id="13c0e-106">[out] The large object heap threshold in bytes.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="13c0e-107">Notes</span><span class="sxs-lookup"><span data-stu-id="13c0e-107">Remarks</span></span>  
 <span data-ttu-id="13c0e-108">Les objets plus grands que le seuil du tas d’objets volumineux seront alloués sur le tas des objets volumineux.</span><span class="sxs-lookup"><span data-stu-id="13c0e-108">Objects larger than the large object heap threshold will be allocated on the large object heap.</span></span> <span data-ttu-id="13c0e-109">À compter de .net Core 3,0 le seuil du tas d’objets volumineux est `pThreshold` configurable, contient la taille du seuil du tas d’objets volumineux actif, en octets.</span><span class="sxs-lookup"><span data-stu-id="13c0e-109">Starting with .NET Core 3.0 the large object heap threshold is configurable, `pThreshold` will contain the active large object heap threshold size in bytes.</span></span>

## <a name="requirements"></a><span data-ttu-id="13c0e-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="13c0e-110">Requirements</span></span>  
 <span data-ttu-id="13c0e-111">**Plateformes** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="13c0e-111">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>  
  
 <span data-ttu-id="13c0e-112">**En-tête :** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="13c0e-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="13c0e-113">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="13c0e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="13c0e-114">**Versions de .net:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13c0e-114">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="13c0e-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="13c0e-115">See also</span></span>
- [<span data-ttu-id="13c0e-116">Interface ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="13c0e-116">ICorProfilerInfo10 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)

