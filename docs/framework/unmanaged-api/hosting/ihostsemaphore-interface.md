---
title: IHostSemaphore, interface
ms.date: 03/30/2017
api_name:
- IHostSemaphore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSemaphore
helpviewer_keywords:
- IHostSemaphore interface [.NET Framework hosting]
ms.assetid: c0765321-656c-441e-bab5-58176292be1e
topic_type:
- apiref
ms.openlocfilehash: 2cf490bcd167b7a498ae21f479f616694ccb5521
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139480"
---
# <a name="ihostsemaphore-interface"></a><span data-ttu-id="964b9-102">IHostSemaphore, interface</span><span class="sxs-lookup"><span data-stu-id="964b9-102">IHostSemaphore Interface</span></span>
<span data-ttu-id="964b9-103">Représente l’implémentation de l’hôte d’un sémaphore pour le Threading.</span><span class="sxs-lookup"><span data-stu-id="964b9-103">Represents the host's implementation of a semaphore for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="964b9-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="964b9-104">Methods</span></span>  
  
|<span data-ttu-id="964b9-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="964b9-105">Method</span></span>|<span data-ttu-id="964b9-106">Description</span><span class="sxs-lookup"><span data-stu-id="964b9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="964b9-107">ReleaseSemaphore, méthode</span><span class="sxs-lookup"><span data-stu-id="964b9-107">ReleaseSemaphore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)|<span data-ttu-id="964b9-108">Augmente le nombre de l’instance de `IHostSemaphore` actuelle de la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="964b9-108">Increases the count of the current `IHostSemaphore` instance by the specified amount.</span></span>|  
|[<span data-ttu-id="964b9-109">Wait, méthode</span><span class="sxs-lookup"><span data-stu-id="964b9-109">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md)|<span data-ttu-id="964b9-110">Entraîne l’attente de l’instance de `IHostSemaphore` actuelle jusqu’à ce qu’elle appartienne ou que la durée spécifiée soit écoulée.</span><span class="sxs-lookup"><span data-stu-id="964b9-110">Causes the current `IHostSemaphore` instance to wait until it is owned or the specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="964b9-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="964b9-111">Requirements</span></span>  
 <span data-ttu-id="964b9-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="964b9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="964b9-113">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="964b9-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="964b9-114">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="964b9-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="964b9-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="964b9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="964b9-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="964b9-116">See also</span></span>

- [<span data-ttu-id="964b9-117">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="964b9-117">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="964b9-118">IHostAutoEvent, interface</span><span class="sxs-lookup"><span data-stu-id="964b9-118">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="964b9-119">IHostManualEvent, interface</span><span class="sxs-lookup"><span data-stu-id="964b9-119">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="964b9-120">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="964b9-120">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="964b9-121">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="964b9-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
