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
ms.openlocfilehash: 4e3891996af5945ed95c8c37dddfee5c446db248
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789107"
---
# <a name="iclrdataenummemoryregionscallback-interface"></a><span data-ttu-id="695ef-102">ICLRDataEnumMemoryRegionsCallback, interface</span><span class="sxs-lookup"><span data-stu-id="695ef-102">ICLRDataEnumMemoryRegionsCallback Interface</span></span>
<span data-ttu-id="695ef-103">Fournit une méthode de rappel pour [ICLRDataEnumMemoryRegions :: EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) pour signaler au débogueur le résultat d’une tentative d’énumération d’une région de mémoire spécifiée.</span><span class="sxs-lookup"><span data-stu-id="695ef-103">Provides a callback method for [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="695ef-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="695ef-104">Methods</span></span>  
  
|<span data-ttu-id="695ef-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="695ef-105">Method</span></span>|<span data-ttu-id="695ef-106">Description</span><span class="sxs-lookup"><span data-stu-id="695ef-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="695ef-107">EnumMemoryRegion, méthode</span><span class="sxs-lookup"><span data-stu-id="695ef-107">EnumMemoryRegion Method</span></span>](iclrdataenummemoryregionscallback-enummemoryregion-method.md)|<span data-ttu-id="695ef-108">Appelé par `ICLRDataEnumMemoryRegions::EnumMemoryRegions` pour signaler au débogueur le résultat d’une tentative d’énumération d’une région de mémoire spécifiée.</span><span class="sxs-lookup"><span data-stu-id="695ef-108">Called by `ICLRDataEnumMemoryRegions::EnumMemoryRegions` to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="695ef-109">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="695ef-109">Requirements</span></span>  
 <span data-ttu-id="695ef-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="695ef-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="695ef-111">**En-tête :** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="695ef-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="695ef-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="695ef-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="695ef-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="695ef-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="695ef-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="695ef-114">See also</span></span>

- [<span data-ttu-id="695ef-115">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="695ef-115">Debugging Interfaces</span></span>](debugging-interfaces.md)
