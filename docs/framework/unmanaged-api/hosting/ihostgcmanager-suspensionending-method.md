---
title: IHostGCManager::SuspensionEnding, méthode
ms.date: 03/30/2017
api_name:
- IHostGCManager.SuspensionEnding
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager::SuspensionEnding
helpviewer_keywords:
- SuspensionEnding method, IHostGCManager interface [.NET Framework hosting]
- IHostGCManager::SuspensionEnding method [.NET Framework hosting]
ms.assetid: 8849a1db-17f0-44b7-880a-bd36d431eb91
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9a815d1a5e8b40aee84ca2b9971ae4be7fb2c725
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763732"
---
# <a name="ihostgcmanagersuspensionending-method"></a><span data-ttu-id="899c5-102">IHostGCManager::SuspensionEnding, méthode</span><span class="sxs-lookup"><span data-stu-id="899c5-102">IHostGCManager::SuspensionEnding Method</span></span>
<span data-ttu-id="899c5-103">Avertit l’hôte que le common language runtime (CLR) reprend l’exécution de tâches sur les threads qui avaient été interrompus pour un garbage collection.</span><span class="sxs-lookup"><span data-stu-id="899c5-103">Notifies the host that the common language runtime (CLR) is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="899c5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="899c5-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionEnding (  
    [in] DWORD generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="899c5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="899c5-105">Parameters</span></span>  
 `generation`  
 <span data-ttu-id="899c5-106">[in] Génération de garbage collection qui est en train de se terminer, à partir de laquelle le thread reprend.</span><span class="sxs-lookup"><span data-stu-id="899c5-106">[in] The garbage collection generation that is just finishing, from which the thread is resuming.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="899c5-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="899c5-107">Return Value</span></span>  
  
|<span data-ttu-id="899c5-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="899c5-108">HRESULT</span></span>|<span data-ttu-id="899c5-109">Description</span><span class="sxs-lookup"><span data-stu-id="899c5-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="899c5-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="899c5-110">S_OK</span></span>|<span data-ttu-id="899c5-111">`SuspensionEnding` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="899c5-111">`SuspensionEnding` returned successfully.</span></span>|  
|<span data-ttu-id="899c5-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="899c5-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="899c5-113">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="899c5-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="899c5-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="899c5-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="899c5-115">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="899c5-115">The call timed out.</span></span>|  
|<span data-ttu-id="899c5-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="899c5-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="899c5-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="899c5-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="899c5-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="899c5-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="899c5-119">Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="899c5-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="899c5-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="899c5-120">E_FAIL</span></span>|<span data-ttu-id="899c5-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="899c5-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="899c5-122">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus.</span><span class="sxs-lookup"><span data-stu-id="899c5-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="899c5-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="899c5-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="899c5-124">Notes</span><span class="sxs-lookup"><span data-stu-id="899c5-124">Remarks</span></span>  
 <span data-ttu-id="899c5-125">Le CLR appelle `SuspensionEnding` une fois qu’il effectue un garbage collection, pour informer l’hôte que le thread reprend l’exécution.</span><span class="sxs-lookup"><span data-stu-id="899c5-125">The CLR calls `SuspensionEnding` after it performs a garbage collection, to inform the host that the thread is resuming execution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="899c5-126">Ne replanifiez pas le thread de de que l’appel de méthode a été effectué à partir.</span><span class="sxs-lookup"><span data-stu-id="899c5-126">Do not reschedule the thread the method call was made from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="899c5-127">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="899c5-127">Requirements</span></span>  
 <span data-ttu-id="899c5-128">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="899c5-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="899c5-129">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="899c5-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="899c5-130">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="899c5-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="899c5-131">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="899c5-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="899c5-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="899c5-132">See also</span></span>

- [<span data-ttu-id="899c5-133">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="899c5-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="899c5-134">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="899c5-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="899c5-135">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="899c5-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="899c5-136">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="899c5-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="899c5-137">IHostGCManager, interface</span><span class="sxs-lookup"><span data-stu-id="899c5-137">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
