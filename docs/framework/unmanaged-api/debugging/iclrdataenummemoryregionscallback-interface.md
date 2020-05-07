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
ms.openlocfilehash: ddcb8064dfb9be30c66404a8762a9ca73cd6afe4
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860662"
---
# <a name="iclrdataenummemoryregionscallback-interface"></a><span data-ttu-id="aaa75-102">ICLRDataEnumMemoryRegionsCallback, interface</span><span class="sxs-lookup"><span data-stu-id="aaa75-102">ICLRDataEnumMemoryRegionsCallback Interface</span></span>
<span data-ttu-id="aaa75-103">Fournit une méthode de rappel pour [ICLRDataEnumMemoryRegions :: EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) pour signaler au débogueur le résultat d’une tentative d’énumération d’une région de mémoire spécifiée.</span><span class="sxs-lookup"><span data-stu-id="aaa75-103">Provides a callback method for [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="aaa75-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="aaa75-104">Methods</span></span>  
  
|<span data-ttu-id="aaa75-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="aaa75-105">Method</span></span>|<span data-ttu-id="aaa75-106">Description</span><span class="sxs-lookup"><span data-stu-id="aaa75-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="aaa75-107">EnumMemoryRegion, méthode</span><span class="sxs-lookup"><span data-stu-id="aaa75-107">EnumMemoryRegion Method</span></span>](iclrdataenummemoryregionscallback-enummemoryregion-method.md)|<span data-ttu-id="aaa75-108">Appelé par `ICLRDataEnumMemoryRegions::EnumMemoryRegions` pour signaler au débogueur le résultat d’une tentative d’énumération d’une région de mémoire spécifiée.</span><span class="sxs-lookup"><span data-stu-id="aaa75-108">Called by `ICLRDataEnumMemoryRegions::EnumMemoryRegions` to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="aaa75-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="aaa75-109">Requirements</span></span>  
 <span data-ttu-id="aaa75-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aaa75-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aaa75-111">**En-tête :** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="aaa75-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="aaa75-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aaa75-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aaa75-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aaa75-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aaa75-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aaa75-114">See also</span></span>

- [<span data-ttu-id="aaa75-115">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="aaa75-115">Debugging Interfaces</span></span>](debugging-interfaces.md)
