---
title: ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion, méthode
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegionsCallback.EnumMemoryRegion
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion
helpviewer_keywords:
- EnumMemoryRegion method [.NET Framework debugging]
- ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion method [.NET Framework debugging]
ms.assetid: 9bb93fab-57e8-4f9a-9ef3-1794504fa896
topic_type:
- apiref
ms.openlocfilehash: c8313b7c97eb5d94424259dc91459f62e13368fb
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785591"
---
# <a name="iclrdataenummemoryregionscallbackenummemoryregion-method"></a><span data-ttu-id="99cd7-102">ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion, méthode</span><span class="sxs-lookup"><span data-stu-id="99cd7-102">ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion Method</span></span>
<span data-ttu-id="99cd7-103">Appelé par [ICLRDataEnumMemoryRegions :: EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) pour signaler au débogueur le résultat d’une tentative d’énumération d’une région de mémoire spécifiée.</span><span class="sxs-lookup"><span data-stu-id="99cd7-103">Called by [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99cd7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="99cd7-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemoryRegion (  
    [in] CLRDATA_ADDRESS  address,  
    [in] ULONG32          size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99cd7-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="99cd7-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="99cd7-106">dans Adresse de début de la région de mémoire qui doit être énumérée.</span><span class="sxs-lookup"><span data-stu-id="99cd7-106">[in] The starting address of the memory region that was to be enumerated.</span></span>  
  
 `size`  
 <span data-ttu-id="99cd7-107">dans Taille, en octets, de la région de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="99cd7-107">[in] The size, in bytes, of the memory region.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99cd7-108">Notes</span><span class="sxs-lookup"><span data-stu-id="99cd7-108">Remarks</span></span>  
 <span data-ttu-id="99cd7-109">La méthode `ICLRDataEnumMemoryRegions::EnumMemoryRegions` appellera cette méthode de rappel après chaque tentative d’énumération d’une région de mémoire.</span><span class="sxs-lookup"><span data-stu-id="99cd7-109">The `ICLRDataEnumMemoryRegions::EnumMemoryRegions` method will call this callback method after each attempt to enumerate a memory region.</span></span> <span data-ttu-id="99cd7-110">L’énumération continue même si cette méthode retourne un HRESULT indiquant un échec.</span><span class="sxs-lookup"><span data-stu-id="99cd7-110">The enumeration will continue even if this method returns an HRESULT indicating failure.</span></span>  
  
 <span data-ttu-id="99cd7-111">Les régions signalées par ce rappel peuvent être des doublons ou des régions qui se chevauchent.</span><span class="sxs-lookup"><span data-stu-id="99cd7-111">Regions reported by this callback may be duplicates or overlapping regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99cd7-112">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="99cd7-112">Requirements</span></span>  
 <span data-ttu-id="99cd7-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99cd7-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99cd7-114">**En-tête :** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="99cd7-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="99cd7-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="99cd7-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="99cd7-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99cd7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99cd7-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="99cd7-117">See also</span></span>

- [<span data-ttu-id="99cd7-118">ICLRDataEnumMemoryRegionsCallback, interface</span><span class="sxs-lookup"><span data-stu-id="99cd7-118">ICLRDataEnumMemoryRegionsCallback Interface</span></span>](iclrdataenummemoryregionscallback-interface.md)
