---
title: IHostSyncManager, interface
ms.date: 03/30/2017
api_name:
- IHostSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager
helpviewer_keywords:
- IHostSyncManager interface [.NET Framework hosting]
ms.assetid: 2e081a37-6a28-4c93-b7ab-1c96a464637c
topic_type:
- apiref
ms.openlocfilehash: e96492270c403f93687245cee8b680dc16b3c787
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803122"
---
# <a name="ihostsyncmanager-interface"></a><span data-ttu-id="78cc3-102">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="78cc3-102">IHostSyncManager Interface</span></span>
<span data-ttu-id="78cc3-103">Fournit des méthodes qui permettent au common language runtime (CLR) de créer des primitives de synchronisation en appelant l’hôte au lieu d’utiliser les fonctions de synchronisation Win32.</span><span class="sxs-lookup"><span data-stu-id="78cc3-103">Provides methods that allow the common language runtime (CLR) to create synchronization primitives by calling the host instead of using the Win32 synchronization functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="78cc3-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="78cc3-104">Methods</span></span>  
  
|<span data-ttu-id="78cc3-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="78cc3-105">Method</span></span>|<span data-ttu-id="78cc3-106">Description</span><span class="sxs-lookup"><span data-stu-id="78cc3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="78cc3-107">CreateAutoEvent, méthode</span><span class="sxs-lookup"><span data-stu-id="78cc3-107">CreateAutoEvent Method</span></span>](ihostsyncmanager-createautoevent-method.md)|<span data-ttu-id="78cc3-108">Crée un objet d’événement à réinitialisation automatique.</span><span class="sxs-lookup"><span data-stu-id="78cc3-108">Creates an auto-reset event object.</span></span>|  
|[<span data-ttu-id="78cc3-109">CreateCrst, méthode</span><span class="sxs-lookup"><span data-stu-id="78cc3-109">CreateCrst Method</span></span>](ihostsyncmanager-createcrst-method.md)|<span data-ttu-id="78cc3-110">Crée un objet de section critique pour la synchronisation.</span><span class="sxs-lookup"><span data-stu-id="78cc3-110">Creates a critical section object for synchronization.</span></span>|  
|[<span data-ttu-id="78cc3-111">CreateCrstWithSpinCount, méthode</span><span class="sxs-lookup"><span data-stu-id="78cc3-111">CreateCrstWithSpinCount Method</span></span>](ihostsyncmanager-createcrstwithspincount-method.md)|<span data-ttu-id="78cc3-112">Crée un objet de section critique avec le nombre de spins pour la synchronisation.</span><span class="sxs-lookup"><span data-stu-id="78cc3-112">Creates a critical section object with spin count for synchronization.</span></span>|  
|[<span data-ttu-id="78cc3-113">CreateManualEvent, méthode</span><span class="sxs-lookup"><span data-stu-id="78cc3-113">CreateManualEvent Method</span></span>](ihostsyncmanager-createmanualevent-method.md)|<span data-ttu-id="78cc3-114">Crée un objet d’événement de réinitialisation manuelle.</span><span class="sxs-lookup"><span data-stu-id="78cc3-114">Creates a manual-reset event object.</span></span>|  
|[<span data-ttu-id="78cc3-115">CreateMonitorEvent, méthode</span><span class="sxs-lookup"><span data-stu-id="78cc3-115">CreateMonitorEvent Method</span></span>](ihostsyncmanager-createmonitorevent-method.md)|<span data-ttu-id="78cc3-116">Crée un objet d’événement de réinitialisation automatique surveillé.</span><span class="sxs-lookup"><span data-stu-id="78cc3-116">Creates a monitored auto-reset event object.</span></span>|  
|[<span data-ttu-id="78cc3-117">CreateRWLockReaderEvent, méthode</span><span class="sxs-lookup"><span data-stu-id="78cc3-117">CreateRWLockReaderEvent Method</span></span>](ihostsyncmanager-createrwlockreaderevent-method.md)|<span data-ttu-id="78cc3-118">Crée un objet d’événement de réinitialisation manuelle pour l’implémentation d’un verrou de lecteur.</span><span class="sxs-lookup"><span data-stu-id="78cc3-118">Creates a manual-reset event object for the implementation of a reader lock.</span></span>|  
|[<span data-ttu-id="78cc3-119">CreateRWLockWriterEvent, méthode</span><span class="sxs-lookup"><span data-stu-id="78cc3-119">CreateRWLockWriterEvent Method</span></span>](ihostsyncmanager-createrwlockwriterevent-method.md)|<span data-ttu-id="78cc3-120">Crée un objet d’événement à réinitialisation automatique pour l’implémentation d’un verrou de writer.</span><span class="sxs-lookup"><span data-stu-id="78cc3-120">Creates an auto-reset event object for the implementation of a writer lock.</span></span>|  
|[<span data-ttu-id="78cc3-121">CreateSemaphore, méthode</span><span class="sxs-lookup"><span data-stu-id="78cc3-121">CreateSemaphore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createsemaphore-method.md)|<span data-ttu-id="78cc3-122">Crée un objet [IHostSemaphore](ihostsemaphore-interface.md) pour le CLR à utiliser comme sémaphore pour les événements d’attente.</span><span class="sxs-lookup"><span data-stu-id="78cc3-122">Creates an [IHostSemaphore](ihostsemaphore-interface.md) object for the CLR to use as a semaphore for wait events.</span></span>|  
|[<span data-ttu-id="78cc3-123">SetCLRSyncManager, méthode</span><span class="sxs-lookup"><span data-stu-id="78cc3-123">SetCLRSyncManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-setclrsyncmanager-method.md)|<span data-ttu-id="78cc3-124">Définit l’instance de [ICLRSyncManager](iclrsyncmanager-interface.md) à associer à l' `IHostSyncManager` instance actuelle.</span><span class="sxs-lookup"><span data-stu-id="78cc3-124">Sets the [ICLRSyncManager](iclrsyncmanager-interface.md) instance to associate with the current `IHostSyncManager` instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78cc3-125">Notes</span><span class="sxs-lookup"><span data-stu-id="78cc3-125">Remarks</span></span>  
 <span data-ttu-id="78cc3-126">Le CLR Découvre l’implémentation de l’hôte de `IHostSyncManager` en appelant la méthode [IHostControl :: GetHostManager,](ihostcontrol-gethostmanager-method.md) avec un `IID` de IID_IHostSyncManager.</span><span class="sxs-lookup"><span data-stu-id="78cc3-126">The CLR discovers the host's implementation of `IHostSyncManager` by calling the [IHostControl::GetHostManager](ihostcontrol-gethostmanager-method.md) method with an `IID` of IID_IHostSyncManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78cc3-127">Spécifications</span><span class="sxs-lookup"><span data-stu-id="78cc3-127">Requirements</span></span>  
 <span data-ttu-id="78cc3-128">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78cc3-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78cc3-129">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="78cc3-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="78cc3-130">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="78cc3-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="78cc3-131">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78cc3-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78cc3-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="78cc3-132">See also</span></span>

- [<span data-ttu-id="78cc3-133">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="78cc3-133">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="78cc3-134">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="78cc3-134">Hosting Interfaces</span></span>](hosting-interfaces.md)
