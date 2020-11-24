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
ms.openlocfilehash: cccbf9a28b16ffee14b3fd3ec43c376109d6ccec
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683054"
---
# <a name="ihostsemaphore-interface"></a><span data-ttu-id="098d7-102">IHostSemaphore, interface</span><span class="sxs-lookup"><span data-stu-id="098d7-102">IHostSemaphore Interface</span></span>

<span data-ttu-id="098d7-103">Représente l’implémentation de l’hôte d’un sémaphore pour le Threading.</span><span class="sxs-lookup"><span data-stu-id="098d7-103">Represents the host's implementation of a semaphore for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="098d7-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="098d7-104">Methods</span></span>  
  
|<span data-ttu-id="098d7-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="098d7-105">Method</span></span>|<span data-ttu-id="098d7-106">Description</span><span class="sxs-lookup"><span data-stu-id="098d7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="098d7-107">ReleaseSemaphore, méthode</span><span class="sxs-lookup"><span data-stu-id="098d7-107">ReleaseSemaphore Method</span></span>](ihostsemaphore-releasesemaphore-method.md)|<span data-ttu-id="098d7-108">Augmente le nombre de l’instance actuelle de `IHostSemaphore` la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="098d7-108">Increases the count of the current `IHostSemaphore` instance by the specified amount.</span></span>|  
|[<span data-ttu-id="098d7-109">Wait, méthode</span><span class="sxs-lookup"><span data-stu-id="098d7-109">Wait Method</span></span>](ihostsemaphore-wait-method.md)|<span data-ttu-id="098d7-110">Fait en sorte que l' `IHostSemaphore` instance actuelle attende jusqu’à ce qu’elle appartienne ou que la durée spécifiée soit écoulée.</span><span class="sxs-lookup"><span data-stu-id="098d7-110">Causes the current `IHostSemaphore` instance to wait until it is owned or the specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="098d7-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="098d7-111">Requirements</span></span>  

 <span data-ttu-id="098d7-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="098d7-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="098d7-113">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="098d7-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="098d7-114">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="098d7-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="098d7-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="098d7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="098d7-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="098d7-116">See also</span></span>

- [<span data-ttu-id="098d7-117">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="098d7-117">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="098d7-118">IHostAutoEvent, interface</span><span class="sxs-lookup"><span data-stu-id="098d7-118">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="098d7-119">IHostManualEvent, interface</span><span class="sxs-lookup"><span data-stu-id="098d7-119">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="098d7-120">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="098d7-120">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="098d7-121">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="098d7-121">Hosting Interfaces</span></span>](hosting-interfaces.md)
