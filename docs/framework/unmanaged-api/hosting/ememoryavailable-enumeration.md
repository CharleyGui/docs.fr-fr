---
title: EMemoryAvailable, énumération
ms.date: 03/30/2017
api_name:
- EMemoryAvailable
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EMemoryAvailable
helpviewer_keywords:
- EMemoryAvailable enumeration [.NET Framework hosting]
ms.assetid: 38e72a06-dbed-473b-a59b-7e0b3ea4f2af
topic_type:
- apiref
ms.openlocfilehash: 0073a532f680d8764ec9e76ea22326a630457043
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176433"
---
# <a name="ememoryavailable-enumeration"></a><span data-ttu-id="ccd1d-102">EMemoryAvailable, énumération</span><span class="sxs-lookup"><span data-stu-id="ccd1d-102">EMemoryAvailable Enumeration</span></span>
<span data-ttu-id="ccd1d-103">Contient des valeurs qui indiquent la quantité de mémoire physique gratuite sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ccd1d-103">Contains values that indicate the amount of free physical memory on the computer.</span></span> <span data-ttu-id="ccd1d-104">Ces valeurs cartographient logiquement les événements de `CreateMemoryResourceNotification` haute et basse mémoire de la fonction dans l’API Windows.</span><span class="sxs-lookup"><span data-stu-id="ccd1d-104">These values logically map to the events for high and low memory returned from the `CreateMemoryResourceNotification` function in the Windows API.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccd1d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ccd1d-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3
} EMemoryAvailable;  
```  
  
## <a name="members"></a><span data-ttu-id="ccd1d-106">Membres</span><span class="sxs-lookup"><span data-stu-id="ccd1d-106">Members</span></span>  
  
|<span data-ttu-id="ccd1d-107">Membre</span><span class="sxs-lookup"><span data-stu-id="ccd1d-107">Member</span></span>|<span data-ttu-id="ccd1d-108">Description</span><span class="sxs-lookup"><span data-stu-id="ccd1d-108">Description</span></span>|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|<span data-ttu-id="ccd1d-109">Beaucoup de mémoire physique est disponible.</span><span class="sxs-lookup"><span data-stu-id="ccd1d-109">Plenty of physical memory is available.</span></span>|  
|`eMemoryAvailableLow`|<span data-ttu-id="ccd1d-110">Très peu de mémoire physique est disponible.</span><span class="sxs-lookup"><span data-stu-id="ccd1d-110">Very little physical memory is available.</span></span>|  
|`eMemoryAvailableNeutral`|<span data-ttu-id="ccd1d-111">La mémoire physique disponible est neutre.</span><span class="sxs-lookup"><span data-stu-id="ccd1d-111">The available physical memory is neutral.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ccd1d-112">Notes </span><span class="sxs-lookup"><span data-stu-id="ccd1d-112">Remarks</span></span>  
 <span data-ttu-id="ccd1d-113">Cette valeur est transmise par l’hôte de l’heure courante (CLR) en utilisant un appel à [l’ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) méthode.</span><span class="sxs-lookup"><span data-stu-id="ccd1d-113">This value is passed by the host to the common language runtime (CLR) by using a call to the [ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccd1d-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ccd1d-114">Requirements</span></span>  
 <span data-ttu-id="ccd1d-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ccd1d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccd1d-116">**En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor</span><span class="sxs-lookup"><span data-stu-id="ccd1d-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ccd1d-117">**Bibliothèque:** MSCorEE.dll MSCorEE.dll MSCorEE.dll MSCor</span><span class="sxs-lookup"><span data-stu-id="ccd1d-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ccd1d-118">**.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ccd1d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccd1d-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ccd1d-119">See also</span></span>

- [<span data-ttu-id="ccd1d-120">Énumérations d'hébergement</span><span class="sxs-lookup"><span data-stu-id="ccd1d-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
