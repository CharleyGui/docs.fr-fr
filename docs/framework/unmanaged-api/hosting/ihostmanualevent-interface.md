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
ms.openlocfilehash: 8eba189d6dfca3781c28631a72a9af3c037efeda
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136794"
---
# <a name="ihostmanualevent-interface"></a><span data-ttu-id="f8784-102">IHostManualEvent, interface</span><span class="sxs-lookup"><span data-stu-id="f8784-102">IHostManualEvent Interface</span></span>
<span data-ttu-id="f8784-103">Fournit l’implémentation de l’hôte d’une représentation d’un événement de réinitialisation manuelle.</span><span class="sxs-lookup"><span data-stu-id="f8784-103">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f8784-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="f8784-104">Methods</span></span>  
  
|<span data-ttu-id="f8784-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="f8784-105">Method</span></span>|<span data-ttu-id="f8784-106">Description</span><span class="sxs-lookup"><span data-stu-id="f8784-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f8784-107">Reset, méthode</span><span class="sxs-lookup"><span data-stu-id="f8784-107">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md)|<span data-ttu-id="f8784-108">Réinitialise l’instance de `IHostManualEvent` actuelle à un État non signalé.</span><span class="sxs-lookup"><span data-stu-id="f8784-108">Resets the current `IHostManualEvent` instance to a non-signaled state.</span></span>|  
|[<span data-ttu-id="f8784-109">Set, méthode</span><span class="sxs-lookup"><span data-stu-id="f8784-109">Set Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-set-method.md)|<span data-ttu-id="f8784-110">Définit l’instance de `IHostManualEvent` actuelle à un état signalé.</span><span class="sxs-lookup"><span data-stu-id="f8784-110">Sets the current `IHostManualEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="f8784-111">Wait, méthode</span><span class="sxs-lookup"><span data-stu-id="f8784-111">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-wait-method.md)|<span data-ttu-id="f8784-112">Entraîne l’attente de l’instance de `IHostManualEvent` actuelle jusqu’à ce qu’elle appartienne ou qu’un laps de temps spécifié se soit écoulé.</span><span class="sxs-lookup"><span data-stu-id="f8784-112">Causes the current `IHostManualEvent` instance to wait until it is owned, or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f8784-113">spécifications</span><span class="sxs-lookup"><span data-stu-id="f8784-113">Requirements</span></span>  
 <span data-ttu-id="f8784-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8784-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8784-115">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f8784-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f8784-116">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f8784-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f8784-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8784-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8784-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8784-118">See also</span></span>

- [<span data-ttu-id="f8784-119">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="f8784-119">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="f8784-120">IHostAutoEvent, interface</span><span class="sxs-lookup"><span data-stu-id="f8784-120">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="f8784-121">IHostSemaphore, interface</span><span class="sxs-lookup"><span data-stu-id="f8784-121">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="f8784-122">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="f8784-122">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="f8784-123">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="f8784-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
