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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 76fc5f578e6da731ffd6406344d00cda8b57f493
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772396"
---
# <a name="ememoryavailable-enumeration"></a><span data-ttu-id="c39e4-102">EMemoryAvailable, énumération</span><span class="sxs-lookup"><span data-stu-id="c39e4-102">EMemoryAvailable Enumeration</span></span>
<span data-ttu-id="c39e4-103">Contient des valeurs qui indiquent la quantité de mémoire physique disponible sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c39e4-103">Contains values that indicate the amount of free physical memory on the computer.</span></span> <span data-ttu-id="c39e4-104">Ces valeurs mappent logiquement aux événements de haute et basse mémoire retournée à partir de la `CreateMemoryResourceNotification` fonction dans l’API Windows.</span><span class="sxs-lookup"><span data-stu-id="c39e4-104">These values logically map to the events for high and low memory returned from the `CreateMemoryResourceNotification` function in the Windows API.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c39e4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c39e4-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3   
} EMemoryAvailable;  
```  
  
## <a name="members"></a><span data-ttu-id="c39e4-106">Membres</span><span class="sxs-lookup"><span data-stu-id="c39e4-106">Members</span></span>  
  
|<span data-ttu-id="c39e4-107">Membre</span><span class="sxs-lookup"><span data-stu-id="c39e4-107">Member</span></span>|<span data-ttu-id="c39e4-108">Description</span><span class="sxs-lookup"><span data-stu-id="c39e4-108">Description</span></span>|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|<span data-ttu-id="c39e4-109">Beaucoup de mémoire physique est disponible.</span><span class="sxs-lookup"><span data-stu-id="c39e4-109">Plenty of physical memory is available.</span></span>|  
|`eMemoryAvailableLow`|<span data-ttu-id="c39e4-110">Très peu de mémoire physique est disponible.</span><span class="sxs-lookup"><span data-stu-id="c39e4-110">Very little physical memory is available.</span></span>|  
|`eMemoryAvailableNeutral`|<span data-ttu-id="c39e4-111">La mémoire physique disponible est neutre.</span><span class="sxs-lookup"><span data-stu-id="c39e4-111">The available physical memory is neutral.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c39e4-112">Notes</span><span class="sxs-lookup"><span data-stu-id="c39e4-112">Remarks</span></span>  
 <span data-ttu-id="c39e4-113">Cette valeur est passée par l’hôte pour le common language runtime (CLR) à l’aide d’un appel à la [ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="c39e4-113">This value is passed by the host to the common language runtime (CLR) by using a call to the [ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c39e4-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c39e4-114">Requirements</span></span>  
 <span data-ttu-id="c39e4-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c39e4-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c39e4-116">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c39e4-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c39e4-117">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c39e4-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c39e4-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c39e4-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c39e4-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c39e4-119">See also</span></span>

- [<span data-ttu-id="c39e4-120">Énumérations d’hébergement</span><span class="sxs-lookup"><span data-stu-id="c39e4-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
