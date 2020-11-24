---
title: IHostManualEvent, interface
ms.date: 03/30/2017
api_name:
- IHostManualEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent
helpviewer_keywords:
- IHostManualEvent interface [.NET Framework hosting]
ms.assetid: 300c2661-b7d1-4c39-b080-9ebdef0fd523
topic_type:
- apiref
ms.openlocfilehash: 50e37b770e3ee6e0a5cdfca61fc5b09749e5735f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673196"
---
# <a name="ihostmanualevent-interface"></a><span data-ttu-id="ab150-102">IHostManualEvent, interface</span><span class="sxs-lookup"><span data-stu-id="ab150-102">IHostManualEvent Interface</span></span>

<span data-ttu-id="ab150-103">Fournit l’implémentation de l’hôte d’une représentation d’un événement de réinitialisation manuelle.</span><span class="sxs-lookup"><span data-stu-id="ab150-103">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ab150-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="ab150-104">Methods</span></span>  
  
|<span data-ttu-id="ab150-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="ab150-105">Method</span></span>|<span data-ttu-id="ab150-106">Description</span><span class="sxs-lookup"><span data-stu-id="ab150-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ab150-107">Reset, méthode</span><span class="sxs-lookup"><span data-stu-id="ab150-107">Reset Method</span></span>](ihostmanualevent-reset-method.md)|<span data-ttu-id="ab150-108">Rétablit l' `IHostManualEvent` État non signalé de l’instance actuelle.</span><span class="sxs-lookup"><span data-stu-id="ab150-108">Resets the current `IHostManualEvent` instance to a non-signaled state.</span></span>|  
|[<span data-ttu-id="ab150-109">Set, méthode</span><span class="sxs-lookup"><span data-stu-id="ab150-109">Set Method</span></span>](ihostmanualevent-set-method.md)|<span data-ttu-id="ab150-110">Définit l' `IHostManualEvent` état signalé de l’instance actuelle.</span><span class="sxs-lookup"><span data-stu-id="ab150-110">Sets the current `IHostManualEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="ab150-111">Wait, méthode</span><span class="sxs-lookup"><span data-stu-id="ab150-111">Wait Method</span></span>](ihostmanualevent-wait-method.md)|<span data-ttu-id="ab150-112">Fait en sorte que l' `IHostManualEvent` instance actuelle attende jusqu’à ce qu’elle appartienne ou qu’un laps de temps spécifié se soit écoulé.</span><span class="sxs-lookup"><span data-stu-id="ab150-112">Causes the current `IHostManualEvent` instance to wait until it is owned, or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ab150-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ab150-113">Requirements</span></span>  

 <span data-ttu-id="ab150-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab150-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab150-115">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ab150-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ab150-116">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ab150-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ab150-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab150-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab150-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab150-118">See also</span></span>

- [<span data-ttu-id="ab150-119">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="ab150-119">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="ab150-120">IHostAutoEvent, interface</span><span class="sxs-lookup"><span data-stu-id="ab150-120">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="ab150-121">IHostSemaphore, interface</span><span class="sxs-lookup"><span data-stu-id="ab150-121">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="ab150-122">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="ab150-122">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="ab150-123">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="ab150-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
