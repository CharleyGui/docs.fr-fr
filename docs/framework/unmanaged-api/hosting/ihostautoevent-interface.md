---
title: IHostAutoEvent, interface
ms.date: 03/30/2017
api_name:
- IHostAutoEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAutoEvent
helpviewer_keywords:
- IHostAutoEvent interface [.NET Framework hosting]
ms.assetid: 6c1d15c1-a80a-4ee9-b1e4-6e859db6575a
topic_type:
- apiref
ms.openlocfilehash: 6893b019c7e86d3f359cf64752d30f7896203786
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680857"
---
# <a name="ihostautoevent-interface"></a><span data-ttu-id="b6542-102">IHostAutoEvent, interface</span><span class="sxs-lookup"><span data-stu-id="b6542-102">IHostAutoEvent Interface</span></span>

<span data-ttu-id="b6542-103">Fournit une représentation de l’implémentation de l’hôte d’un événement de réinitialisation automatique.</span><span class="sxs-lookup"><span data-stu-id="b6542-103">Provides a representation of the host's implementation of an auto-reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b6542-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="b6542-104">Methods</span></span>  
  
|<span data-ttu-id="b6542-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="b6542-105">Method</span></span>|<span data-ttu-id="b6542-106">Description</span><span class="sxs-lookup"><span data-stu-id="b6542-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b6542-107">Set, méthode</span><span class="sxs-lookup"><span data-stu-id="b6542-107">Set Method</span></span>](ihostautoevent-set-method.md)|<span data-ttu-id="b6542-108">Définit l' `IHostAutoEvent` état signalé de l’instance actuelle.</span><span class="sxs-lookup"><span data-stu-id="b6542-108">Sets the current `IHostAutoEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="b6542-109">Wait, méthode</span><span class="sxs-lookup"><span data-stu-id="b6542-109">Wait Method</span></span>](ihostautoevent-wait-method.md)|<span data-ttu-id="b6542-110">Entraîne l' `IHostAutoEvent` attente de l’instance actuelle jusqu’à ce que l’événement soit détenu ou qu’un laps de temps spécifié se soit écoulé.</span><span class="sxs-lookup"><span data-stu-id="b6542-110">Causes the current `IHostAutoEvent` instance to wait until the event is owned or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b6542-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b6542-111">Requirements</span></span>  

 <span data-ttu-id="b6542-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6542-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6542-113">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b6542-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b6542-114">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b6542-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b6542-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6542-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6542-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6542-116">See also</span></span>

- [<span data-ttu-id="b6542-117">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="b6542-117">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="b6542-118">IHostManualEvent, interface</span><span class="sxs-lookup"><span data-stu-id="b6542-118">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="b6542-119">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="b6542-119">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="b6542-120">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="b6542-120">Hosting Interfaces</span></span>](hosting-interfaces.md)
