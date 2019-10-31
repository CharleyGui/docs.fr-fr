---
title: ICLRDataEnumMemoryRegionsCallback, interface
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegionsCallback
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegionsCallback
helpviewer_keywords:
- ICLRDataEnumMemoryRegionsCallback interface [.NET Framework debugging]
ms.assetid: 3f1af8b0-8478-48e0-a7ec-3e90e0b97649
topic_type:
- apiref
ms.openlocfilehash: cf46133095d1345ffbe0356d3ab486c11ae6dbd6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122914"
---
# <a name="iclrdataenummemoryregionscallback-interface"></a><span data-ttu-id="baced-102">ICLRDataEnumMemoryRegionsCallback, interface</span><span class="sxs-lookup"><span data-stu-id="baced-102">ICLRDataEnumMemoryRegionsCallback Interface</span></span>
<span data-ttu-id="baced-103">Fournit une méthode de rappel pour [ICLRDataEnumMemoryRegions :: EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) pour signaler au débogueur le résultat d’une tentative d’énumération d’une région de mémoire spécifiée.</span><span class="sxs-lookup"><span data-stu-id="baced-103">Provides a callback method for [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="baced-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="baced-104">Methods</span></span>  
  
|<span data-ttu-id="baced-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="baced-105">Method</span></span>|<span data-ttu-id="baced-106">Description</span><span class="sxs-lookup"><span data-stu-id="baced-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="baced-107">EnumMemoryRegion, méthode</span><span class="sxs-lookup"><span data-stu-id="baced-107">EnumMemoryRegion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-enummemoryregion-method.md)|<span data-ttu-id="baced-108">Appelé par `ICLRDataEnumMemoryRegions::EnumMemoryRegions` pour signaler au débogueur le résultat d’une tentative d’énumération d’une région de mémoire spécifiée.</span><span class="sxs-lookup"><span data-stu-id="baced-108">Called by `ICLRDataEnumMemoryRegions::EnumMemoryRegions` to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="baced-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="baced-109">Requirements</span></span>  
 <span data-ttu-id="baced-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="baced-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="baced-111">**En-tête :** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="baced-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="baced-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="baced-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="baced-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="baced-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baced-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="baced-114">See also</span></span>

- [<span data-ttu-id="baced-115">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="baced-115">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
