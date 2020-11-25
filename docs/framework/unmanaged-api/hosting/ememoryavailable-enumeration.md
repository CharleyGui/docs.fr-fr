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
ms.openlocfilehash: 6a8765bfd62a2e6543661804ab8d009ce19f8813
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724310"
---
# <a name="ememoryavailable-enumeration"></a><span data-ttu-id="91711-102">EMemoryAvailable, énumération</span><span class="sxs-lookup"><span data-stu-id="91711-102">EMemoryAvailable Enumeration</span></span>

<span data-ttu-id="91711-103">Contient des valeurs qui indiquent la quantité de mémoire physique disponible sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="91711-103">Contains values that indicate the amount of free physical memory on the computer.</span></span> <span data-ttu-id="91711-104">Ces valeurs correspondent logiquement aux événements pour la mémoire haute et la mémoire insuffisante retournés par la `CreateMemoryResourceNotification` fonction dans l’API Windows.</span><span class="sxs-lookup"><span data-stu-id="91711-104">These values logically map to the events for high and low memory returned from the `CreateMemoryResourceNotification` function in the Windows API.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91711-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="91711-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3
} EMemoryAvailable;  
```  
  
## <a name="members"></a><span data-ttu-id="91711-106">Membres</span><span class="sxs-lookup"><span data-stu-id="91711-106">Members</span></span>  
  
|<span data-ttu-id="91711-107">Membre</span><span class="sxs-lookup"><span data-stu-id="91711-107">Member</span></span>|<span data-ttu-id="91711-108">Description</span><span class="sxs-lookup"><span data-stu-id="91711-108">Description</span></span>|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|<span data-ttu-id="91711-109">Une grande quantité de mémoire physique est disponible.</span><span class="sxs-lookup"><span data-stu-id="91711-109">Plenty of physical memory is available.</span></span>|  
|`eMemoryAvailableLow`|<span data-ttu-id="91711-110">Très peu de mémoire physique est disponible.</span><span class="sxs-lookup"><span data-stu-id="91711-110">Very little physical memory is available.</span></span>|  
|`eMemoryAvailableNeutral`|<span data-ttu-id="91711-111">La mémoire physique disponible est neutre.</span><span class="sxs-lookup"><span data-stu-id="91711-111">The available physical memory is neutral.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91711-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="91711-112">Remarks</span></span>  

 <span data-ttu-id="91711-113">Cette valeur est passée par l’hôte au common language runtime (CLR) à l’aide d’un appel à la méthode [ICLRMemoryNotificationCallback :: OnMemoryNotification](iclrmemorynotificationcallback-onmemorynotification-method.md) .</span><span class="sxs-lookup"><span data-stu-id="91711-113">This value is passed by the host to the common language runtime (CLR) by using a call to the [ICLRMemoryNotificationCallback::OnMemoryNotification](iclrmemorynotificationcallback-onmemorynotification-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91711-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="91711-114">Requirements</span></span>  

 <span data-ttu-id="91711-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91711-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91711-116">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="91711-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="91711-117">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="91711-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="91711-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91711-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91711-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="91711-119">See also</span></span>

- [<span data-ttu-id="91711-120">Énumérations d'hébergement</span><span class="sxs-lookup"><span data-stu-id="91711-120">Hosting Enumerations</span></span>](hosting-enumerations.md)
