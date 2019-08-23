---
title: IHostSyncManager::CreateCrst, méthode
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateCrst
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateCrst
helpviewer_keywords:
- CreateCrst method [.NET Framework hosting]
- IHostSyncManager::CreateCrst method [.NET Framework hosting]
ms.assetid: ac278cc8-2540-4a6c-b5c6-b90c3970b4f4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 622b6c523adfb7bae2fc38826152ef69709568cc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931074"
---
# <a name="ihostsyncmanagercreatecrst-method"></a><span data-ttu-id="b858d-102">IHostSyncManager::CreateCrst, méthode</span><span class="sxs-lookup"><span data-stu-id="b858d-102">IHostSyncManager::CreateCrst Method</span></span>
<span data-ttu-id="b858d-103">Crée un objet de section critique pour la synchronisation.</span><span class="sxs-lookup"><span data-stu-id="b858d-103">Creates a critical section object for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b858d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b858d-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateCrst (  
    [out] IHostCrst** ppCrst  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b858d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b858d-105">Parameters</span></span>  
 `ppCrst`  
 <span data-ttu-id="b858d-106">à Pointeur vers l’adresse d’une instance [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) implémentée par l’hôte, ou null si la section critique n’a pas pu être créée.</span><span class="sxs-lookup"><span data-stu-id="b858d-106">[out] A pointer to the address of an [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance implemented by the host, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b858d-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="b858d-107">Return Value</span></span>  
  
|<span data-ttu-id="b858d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b858d-108">HRESULT</span></span>|<span data-ttu-id="b858d-109">Description</span><span class="sxs-lookup"><span data-stu-id="b858d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b858d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b858d-110">S_OK</span></span>|<span data-ttu-id="b858d-111">`CreateCrst`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="b858d-111">`CreateCrst` returned successfully.</span></span>|  
|<span data-ttu-id="b858d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b858d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b858d-113">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="b858d-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b858d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b858d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b858d-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="b858d-115">The call timed out.</span></span>|  
|<span data-ttu-id="b858d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b858d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b858d-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="b858d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b858d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b858d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b858d-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="b858d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b858d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b858d-120">E_FAIL</span></span>|<span data-ttu-id="b858d-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="b858d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b858d-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="b858d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b858d-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b858d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b858d-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="b858d-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="b858d-125">Mémoire disponible insuffisante pour créer la section critique demandée.</span><span class="sxs-lookup"><span data-stu-id="b858d-125">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b858d-126">Notes</span><span class="sxs-lookup"><span data-stu-id="b858d-126">Remarks</span></span>  
 <span data-ttu-id="b858d-127">Les objets de section critique fournissent une synchronisation similaire à celle fournie par un objet mutex, sauf que les sections critiques peuvent être utilisées uniquement par les threads d’un processus unique.</span><span class="sxs-lookup"><span data-stu-id="b858d-127">Critical section objects provide synchronization similar to that provided by a mutex object, except that critical sections can be used only by the threads of a single process.</span></span> <span data-ttu-id="b858d-128">`CreateCrst`reflète la fonction `InitializeCriticalSection` Win32.</span><span class="sxs-lookup"><span data-stu-id="b858d-128">`CreateCrst` mirrors the Win32 `InitializeCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b858d-129">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b858d-129">Requirements</span></span>  
 <span data-ttu-id="b858d-130">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b858d-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b858d-131">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b858d-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b858d-132">**Bibliothèque** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b858d-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b858d-133">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b858d-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b858d-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b858d-134">See also</span></span>

- [<span data-ttu-id="b858d-135">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="b858d-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="b858d-136">IHostCrst, interface</span><span class="sxs-lookup"><span data-stu-id="b858d-136">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="b858d-137">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="b858d-137">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="b858d-138">IHostSemaphore, interface</span><span class="sxs-lookup"><span data-stu-id="b858d-138">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="b858d-139">Mutex</span><span class="sxs-lookup"><span data-stu-id="b858d-139">Mutexes</span></span>](../../../standard/threading/mutexes.md)
- [<span data-ttu-id="b858d-140">Semaphore et SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="b858d-140">Semaphore and SemaphoreSlim</span></span>](../../../standard/threading/semaphore-and-semaphoreslim.md)
