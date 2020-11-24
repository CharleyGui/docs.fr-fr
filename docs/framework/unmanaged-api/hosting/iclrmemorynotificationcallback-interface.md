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
ms.openlocfilehash: 5762a354bec485cb382b5460dfd2a337f79bee1a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689535"
---
# <a name="iclrmemorynotificationcallback-interface"></a><span data-ttu-id="81d64-102">ICLRMemoryNotificationCallback, interface</span><span class="sxs-lookup"><span data-stu-id="81d64-102">ICLRMemoryNotificationCallback Interface</span></span>

<span data-ttu-id="81d64-103">Permet à l’hôte de signaler des conditions de sollicitation de la mémoire à l’aide d’une approche similaire à celle de la `CreateMemoryResourceNotification` fonction Win32.</span><span class="sxs-lookup"><span data-stu-id="81d64-103">Allows the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="81d64-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="81d64-104">Methods</span></span>  
  
|<span data-ttu-id="81d64-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="81d64-105">Method</span></span>|<span data-ttu-id="81d64-106">Description</span><span class="sxs-lookup"><span data-stu-id="81d64-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="81d64-107">OnMemoryNotification, méthode</span><span class="sxs-lookup"><span data-stu-id="81d64-107">OnMemoryNotification Method</span></span>](iclrmemorynotificationcallback-onmemorynotification-method.md)|<span data-ttu-id="81d64-108">Notifie le common language runtime (CLR) de la charge de mémoire sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="81d64-108">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81d64-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="81d64-109">Remarks</span></span>  

 <span data-ttu-id="81d64-110">L’hôte utilise l' `ICLRMemoryNotificationCallback` interface pour demander que le CLR libère des ressources mémoire.</span><span class="sxs-lookup"><span data-stu-id="81d64-110">The host uses the `ICLRMemoryNotificationCallback` interface to request that the CLR free memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81d64-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="81d64-111">Requirements</span></span>  

 <span data-ttu-id="81d64-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81d64-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81d64-113">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="81d64-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="81d64-114">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="81d64-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="81d64-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81d64-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81d64-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="81d64-116">See also</span></span>

- [<span data-ttu-id="81d64-117">IHostMemoryManager, interface</span><span class="sxs-lookup"><span data-stu-id="81d64-117">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="81d64-118">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="81d64-118">Hosting Interfaces</span></span>](hosting-interfaces.md)
