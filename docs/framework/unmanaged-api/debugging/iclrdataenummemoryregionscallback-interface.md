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
ms.openlocfilehash: f080d852b190346740a3629f3b5d46a9f3808293
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703627"
---
# <a name="iclrdataenummemoryregionscallback-interface"></a><span data-ttu-id="4dd37-102">ICLRDataEnumMemoryRegionsCallback, interface</span><span class="sxs-lookup"><span data-stu-id="4dd37-102">ICLRDataEnumMemoryRegionsCallback Interface</span></span>

<span data-ttu-id="4dd37-103">Fournit une méthode de rappel pour [ICLRDataEnumMemoryRegions :: EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) pour signaler au débogueur le résultat d’une tentative d’énumération d’une région de mémoire spécifiée.</span><span class="sxs-lookup"><span data-stu-id="4dd37-103">Provides a callback method for [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4dd37-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="4dd37-104">Methods</span></span>  
  
|<span data-ttu-id="4dd37-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="4dd37-105">Method</span></span>|<span data-ttu-id="4dd37-106">Description</span><span class="sxs-lookup"><span data-stu-id="4dd37-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4dd37-107">EnumMemoryRegion, méthode</span><span class="sxs-lookup"><span data-stu-id="4dd37-107">EnumMemoryRegion Method</span></span>](iclrdataenummemoryregionscallback-enummemoryregion-method.md)|<span data-ttu-id="4dd37-108">Appelé par `ICLRDataEnumMemoryRegions::EnumMemoryRegions` pour signaler au débogueur le résultat d’une tentative d’énumération d’une région de mémoire spécifiée.</span><span class="sxs-lookup"><span data-stu-id="4dd37-108">Called by `ICLRDataEnumMemoryRegions::EnumMemoryRegions` to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4dd37-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4dd37-109">Requirements</span></span>  

 <span data-ttu-id="4dd37-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4dd37-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4dd37-111">**En-tête :** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="4dd37-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="4dd37-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4dd37-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4dd37-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4dd37-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dd37-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4dd37-114">See also</span></span>

- [<span data-ttu-id="4dd37-115">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="4dd37-115">Debugging Interfaces</span></span>](debugging-interfaces.md)
