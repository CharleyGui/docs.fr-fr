---
title: IHostSyncManager::SetCLRSyncManager, méthode
ms.date: 03/30/2017
api_name:
- IHostSyncManager.SetCLRSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::SetCLRSyncManager
helpviewer_keywords:
- IHostSyncManager::SetCLRSyncManager method [.NET Framework hosting]
- SetCLRSyncManager method [.NET Framework hosting]
ms.assetid: 2b8bbe76-a45d-4989-bacb-11df42f8798c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 66ce6ce322a0fb58f64d65501a33f58ad92bcd2e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764558"
---
# <a name="ihostsyncmanagersetclrsyncmanager-method"></a><span data-ttu-id="68742-102">IHostSyncManager::SetCLRSyncManager, méthode</span><span class="sxs-lookup"><span data-stu-id="68742-102">IHostSyncManager::SetCLRSyncManager Method</span></span>
<span data-ttu-id="68742-103">Définit le [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instance à associer à l’actuel [IHostSyncManager](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md) instance.</span><span class="sxs-lookup"><span data-stu-id="68742-103">Sets the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instance to associate with the current [IHostSyncManager](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68742-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68742-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRSyncManager (  
    [in] ICLRSyncManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68742-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="68742-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="68742-106">[in] Un pointeur vers un `ICLRSyncManager` instance fournie par le common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="68742-106">[in] A pointer to an `ICLRSyncManager` instance supplied by the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="68742-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="68742-107">Return Value</span></span>  
  
|<span data-ttu-id="68742-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="68742-108">HRESULT</span></span>|<span data-ttu-id="68742-109">Description</span><span class="sxs-lookup"><span data-stu-id="68742-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="68742-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="68742-110">S_OK</span></span>|<span data-ttu-id="68742-111">`SetCLRSyncManager` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="68742-111">`SetCLRSyncManager` returned successfully.</span></span>|  
|<span data-ttu-id="68742-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="68742-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="68742-113">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="68742-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="68742-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="68742-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="68742-115">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="68742-115">The call timed out.</span></span>|  
|<span data-ttu-id="68742-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="68742-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="68742-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="68742-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="68742-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="68742-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="68742-119">Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="68742-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="68742-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="68742-120">E_FAIL</span></span>|<span data-ttu-id="68742-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="68742-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="68742-122">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus.</span><span class="sxs-lookup"><span data-stu-id="68742-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="68742-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="68742-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68742-124">Notes</span><span class="sxs-lookup"><span data-stu-id="68742-124">Remarks</span></span>  
 <span data-ttu-id="68742-125">Pour faciliter la communication entre l’hôte et le CLR, les interfaces d’hébergement existent généralement par paires.</span><span class="sxs-lookup"><span data-stu-id="68742-125">To facilitate communication between the host and the CLR, hosting interfaces generally come in pairs.</span></span> <span data-ttu-id="68742-126">Un membre de la paire est implémenté par l’hôte, et l’autre membre est implémenté par le CLR.</span><span class="sxs-lookup"><span data-stu-id="68742-126">One member of the pair is implemented by the host, and the other member is implemented by the CLR.</span></span> <span data-ttu-id="68742-127">En tant qu’une implémentation côté hôte, le `IHostSyncManager` interface correspond à la `ICLRSyncManager` interface implémentée par le CLR.</span><span class="sxs-lookup"><span data-stu-id="68742-127">As a host-side implementation, the `IHostSyncManager` interface corresponds to the `ICLRSyncManager` interface implemented by the CLR.</span></span> <span data-ttu-id="68742-128">Le CLR appelle `SetCLRSyncManager` pour fournir un `ICLRSyncManager` instance de l’hôte à associer à l’actuel `IHostSyncManager` instance.</span><span class="sxs-lookup"><span data-stu-id="68742-128">The CLR calls `SetCLRSyncManager` to supply an `ICLRSyncManager` instance for the host to associate with the current `IHostSyncManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68742-129">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="68742-129">Requirements</span></span>  
 <span data-ttu-id="68742-130">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68742-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68742-131">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="68742-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="68742-132">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="68742-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="68742-133">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68742-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68742-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="68742-134">See also</span></span>

- [<span data-ttu-id="68742-135">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="68742-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="68742-136">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="68742-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
