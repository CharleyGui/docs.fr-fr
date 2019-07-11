---
title: IHostGCManager::SuspensionStarting, méthode
ms.date: 03/30/2017
api_name:
- IHostGCManager.SuspensionStarting
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager::SuspensionStarting
helpviewer_keywords:
- SuspensionStarting method, IHostGCManager interface [.NET Framework hosting]
- IHostGCManager::SuspensionStarting method [.NET Framework hosting]
ms.assetid: c381f524-94cf-4fa2-9298-50f847a03431
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 00322a75c4a15e42c89ff5a8680171a168a37613
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758700"
---
# <a name="ihostgcmanagersuspensionstarting-method"></a><span data-ttu-id="6a7d0-102">IHostGCManager::SuspensionStarting, méthode</span><span class="sxs-lookup"><span data-stu-id="6a7d0-102">IHostGCManager::SuspensionStarting Method</span></span>
<span data-ttu-id="6a7d0-103">Avertit l’hôte que le common language runtime (CLR) interrompt l’exécution de tâches pour effectuer un garbage collection.</span><span class="sxs-lookup"><span data-stu-id="6a7d0-103">Notifies the host that the common language runtime (CLR) is suspending execution of tasks, to perform a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a7d0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a7d0-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionStarting ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="6a7d0-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="6a7d0-105">Return Value</span></span>  
  
|<span data-ttu-id="6a7d0-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6a7d0-106">HRESULT</span></span>|<span data-ttu-id="6a7d0-107">Description</span><span class="sxs-lookup"><span data-stu-id="6a7d0-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6a7d0-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="6a7d0-108">S_OK</span></span>|<span data-ttu-id="6a7d0-109">`SuspensionStarting` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="6a7d0-109">`SuspensionStarting` returned successfully.</span></span>|  
|<span data-ttu-id="6a7d0-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6a7d0-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6a7d0-111">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="6a7d0-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6a7d0-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6a7d0-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6a7d0-113">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="6a7d0-113">The call timed out.</span></span>|  
|<span data-ttu-id="6a7d0-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6a7d0-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6a7d0-115">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="6a7d0-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6a7d0-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6a7d0-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6a7d0-117">Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="6a7d0-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6a7d0-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6a7d0-118">E_FAIL</span></span>|<span data-ttu-id="6a7d0-119">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="6a7d0-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6a7d0-120">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus.</span><span class="sxs-lookup"><span data-stu-id="6a7d0-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6a7d0-121">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6a7d0-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6a7d0-122">Notes</span><span class="sxs-lookup"><span data-stu-id="6a7d0-122">Remarks</span></span>  
 <span data-ttu-id="6a7d0-123">Le CLR appelle `SuspensionStarting` pour informer l’hôte que le garbage collection se produit.</span><span class="sxs-lookup"><span data-stu-id="6a7d0-123">The CLR calls `SuspensionStarting` to inform the host that garbage collection is occurring.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6a7d0-124">Ne replanifiez pas cette tâche.</span><span class="sxs-lookup"><span data-stu-id="6a7d0-124">Do not reschedule this task.</span></span> <span data-ttu-id="6a7d0-125">L’hôte doit replanifier une tâche lorsque [ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md) est appelée.</span><span class="sxs-lookup"><span data-stu-id="6a7d0-125">The host must reschedule a task when [ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md) is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a7d0-126">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6a7d0-126">Requirements</span></span>  
 <span data-ttu-id="6a7d0-127">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a7d0-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a7d0-128">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6a7d0-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6a7d0-129">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6a7d0-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6a7d0-130">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a7d0-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a7d0-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6a7d0-131">See also</span></span>

- [<span data-ttu-id="6a7d0-132">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="6a7d0-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="6a7d0-133">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="6a7d0-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="6a7d0-134">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="6a7d0-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="6a7d0-135">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="6a7d0-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="6a7d0-136">IHostGCManager, interface</span><span class="sxs-lookup"><span data-stu-id="6a7d0-136">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
