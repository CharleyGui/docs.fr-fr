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
ms.openlocfilehash: 7c46f00063cdf9281a5f1080594e8d6dbc6c101e
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804599"
---
# <a name="ihostmanualevent-interface"></a><span data-ttu-id="dcf7a-102">IHostManualEvent, interface</span><span class="sxs-lookup"><span data-stu-id="dcf7a-102">IHostManualEvent Interface</span></span>
<span data-ttu-id="dcf7a-103">Fournit l’implémentation de l’hôte d’une représentation d’un événement de réinitialisation manuelle.</span><span class="sxs-lookup"><span data-stu-id="dcf7a-103">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dcf7a-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="dcf7a-104">Methods</span></span>  
  
|<span data-ttu-id="dcf7a-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="dcf7a-105">Method</span></span>|<span data-ttu-id="dcf7a-106">Description</span><span class="sxs-lookup"><span data-stu-id="dcf7a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dcf7a-107">Reset, méthode</span><span class="sxs-lookup"><span data-stu-id="dcf7a-107">Reset Method</span></span>](ihostmanualevent-reset-method.md)|<span data-ttu-id="dcf7a-108">Rétablit l' `IHostManualEvent` État non signalé de l’instance actuelle.</span><span class="sxs-lookup"><span data-stu-id="dcf7a-108">Resets the current `IHostManualEvent` instance to a non-signaled state.</span></span>|  
|[<span data-ttu-id="dcf7a-109">Méthode Set</span><span class="sxs-lookup"><span data-stu-id="dcf7a-109">Set Method</span></span>](ihostmanualevent-set-method.md)|<span data-ttu-id="dcf7a-110">Définit l' `IHostManualEvent` état signalé de l’instance actuelle.</span><span class="sxs-lookup"><span data-stu-id="dcf7a-110">Sets the current `IHostManualEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="dcf7a-111">Wait, méthode</span><span class="sxs-lookup"><span data-stu-id="dcf7a-111">Wait Method</span></span>](ihostmanualevent-wait-method.md)|<span data-ttu-id="dcf7a-112">Fait en sorte que l' `IHostManualEvent` instance actuelle attende jusqu’à ce qu’elle appartienne ou qu’un laps de temps spécifié se soit écoulé.</span><span class="sxs-lookup"><span data-stu-id="dcf7a-112">Causes the current `IHostManualEvent` instance to wait until it is owned, or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dcf7a-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="dcf7a-113">Requirements</span></span>  
 <span data-ttu-id="dcf7a-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dcf7a-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcf7a-115">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="dcf7a-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dcf7a-116">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="dcf7a-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dcf7a-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcf7a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcf7a-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dcf7a-118">See also</span></span>

- [<span data-ttu-id="dcf7a-119">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="dcf7a-119">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="dcf7a-120">IHostAutoEvent, interface</span><span class="sxs-lookup"><span data-stu-id="dcf7a-120">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="dcf7a-121">IHostSemaphore, interface</span><span class="sxs-lookup"><span data-stu-id="dcf7a-121">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="dcf7a-122">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="dcf7a-122">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="dcf7a-123">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="dcf7a-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
