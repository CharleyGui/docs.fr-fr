---
title: IHostGCManager, interface
ms.date: 03/30/2017
api_name:
- IHostGCManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager
helpviewer_keywords:
- IHostGCManager interface [.NET Framework hosting]
ms.assetid: 820330a4-244c-4f67-ab5e-f24b0b3c2080
topic_type:
- apiref
ms.openlocfilehash: eb7e52b5237d4341c27b8c167249dc2614168679
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729520"
---
# <a name="ihostgcmanager-interface"></a><span data-ttu-id="8f165-102">IHostGCManager, interface</span><span class="sxs-lookup"><span data-stu-id="8f165-102">IHostGCManager Interface</span></span>

<span data-ttu-id="8f165-103">Fournit des méthodes qui notifient l’hôte d’événements dans le mécanisme de garbage collection implémenté par le common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="8f165-103">Provides methods that notify the host of events in the garbage collection mechanism implemented by the common language runtime (CLR).</span></span>  
  
## <a name="members"></a><span data-ttu-id="8f165-104">Membres</span><span class="sxs-lookup"><span data-stu-id="8f165-104">Members</span></span>  
  
|<span data-ttu-id="8f165-105">Membre</span><span class="sxs-lookup"><span data-stu-id="8f165-105">Member</span></span>|<span data-ttu-id="8f165-106">Description</span><span class="sxs-lookup"><span data-stu-id="8f165-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8f165-107">SuspensionEnding, méthode</span><span class="sxs-lookup"><span data-stu-id="8f165-107">SuspensionEnding Method</span></span>](ihostgcmanager-suspensionending-method.md)|<span data-ttu-id="8f165-108">Avertit l’hôte que le CLR reprend l’exécution des tâches sur les threads suspendus pour un garbage collection.</span><span class="sxs-lookup"><span data-stu-id="8f165-108">Notifies the host that the CLR is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>|  
|[<span data-ttu-id="8f165-109">SuspensionStarting, méthode</span><span class="sxs-lookup"><span data-stu-id="8f165-109">SuspensionStarting Method</span></span>](ihostgcmanager-suspensionstarting-method.md)|<span data-ttu-id="8f165-110">Avertit l’hôte que le CLR interrompt l’exécution des tâches, pour effectuer une garbage collection.</span><span class="sxs-lookup"><span data-stu-id="8f165-110">Notifies the host that the CLR is suspending execution of tasks, to perform a garbage collection.</span></span>|  
|[<span data-ttu-id="8f165-111">ThreadIsBlockingForSuspension, méthode</span><span class="sxs-lookup"><span data-stu-id="8f165-111">ThreadIsBlockingForSuspension Method</span></span>](ihostgcmanager-threadisblockingforsuspension-method.md)|<span data-ttu-id="8f165-112">Avertit l’hôte que le thread à partir duquel l’appel de méthode a été effectué est sur le le bloc pour un garbage collection.</span><span class="sxs-lookup"><span data-stu-id="8f165-112">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8f165-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8f165-113">Requirements</span></span>  

 <span data-ttu-id="8f165-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f165-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f165-115">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8f165-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8f165-116">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8f165-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8f165-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f165-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f165-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8f165-118">See also</span></span>

- [<span data-ttu-id="8f165-119">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="8f165-119">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="8f165-120">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="8f165-120">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="8f165-121">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="8f165-121">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="8f165-122">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="8f165-122">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="8f165-123">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="8f165-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
