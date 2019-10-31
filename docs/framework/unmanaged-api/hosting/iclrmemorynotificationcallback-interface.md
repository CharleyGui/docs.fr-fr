---
title: ICLRMemoryNotificationCallback, interface
ms.date: 03/30/2017
api_name:
- ICLRMemoryNotificationCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMemoryNotificationCallback
helpviewer_keywords:
- ICLRMemoryNotificationCallback interface [.NET Framework hosting]
ms.assetid: 873639e2-4837-4568-83b3-4493e67e4174
topic_type:
- apiref
ms.openlocfilehash: e980356ad592e137df7d08dadd77431b0e295380
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141006"
---
# <a name="iclrmemorynotificationcallback-interface"></a><span data-ttu-id="7c028-102">ICLRMemoryNotificationCallback, interface</span><span class="sxs-lookup"><span data-stu-id="7c028-102">ICLRMemoryNotificationCallback Interface</span></span>
<span data-ttu-id="7c028-103">Permet à l’hôte de signaler des conditions de sollicitation de la mémoire à l’aide d’une approche similaire à celle de la fonction `CreateMemoryResourceNotification` Win32.</span><span class="sxs-lookup"><span data-stu-id="7c028-103">Allows the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7c028-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="7c028-104">Methods</span></span>  
  
|<span data-ttu-id="7c028-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="7c028-105">Method</span></span>|<span data-ttu-id="7c028-106">Description</span><span class="sxs-lookup"><span data-stu-id="7c028-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7c028-107">OnMemoryNotification, méthode</span><span class="sxs-lookup"><span data-stu-id="7c028-107">OnMemoryNotification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)|<span data-ttu-id="7c028-108">Notifie le common language runtime (CLR) de la charge de mémoire sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="7c028-108">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c028-109">Notes</span><span class="sxs-lookup"><span data-stu-id="7c028-109">Remarks</span></span>  
 <span data-ttu-id="7c028-110">L’hôte utilise l’interface `ICLRMemoryNotificationCallback` pour demander que le CLR libère des ressources mémoire.</span><span class="sxs-lookup"><span data-stu-id="7c028-110">The host uses the `ICLRMemoryNotificationCallback` interface to request that the CLR free memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c028-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="7c028-111">Requirements</span></span>  
 <span data-ttu-id="7c028-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c028-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c028-113">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7c028-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7c028-114">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7c028-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7c028-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c028-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c028-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7c028-116">See also</span></span>

- [<span data-ttu-id="7c028-117">IHostMemoryManager, interface</span><span class="sxs-lookup"><span data-stu-id="7c028-117">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="7c028-118">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="7c028-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
