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
ms.openlocfilehash: bf1b830f55110c00356527bc9caa41dfd94ae377
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130455"
---
# <a name="ihostgcmanagersuspensionstarting-method"></a><span data-ttu-id="4b646-102">IHostGCManager::SuspensionStarting, méthode</span><span class="sxs-lookup"><span data-stu-id="4b646-102">IHostGCManager::SuspensionStarting Method</span></span>
<span data-ttu-id="4b646-103">Avertit l’hôte que le common language runtime (CLR) interrompt l’exécution des tâches, pour effectuer une garbage collection.</span><span class="sxs-lookup"><span data-stu-id="4b646-103">Notifies the host that the common language runtime (CLR) is suspending execution of tasks, to perform a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b646-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4b646-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionStarting ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="4b646-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="4b646-105">Return Value</span></span>  
  
|<span data-ttu-id="4b646-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4b646-106">HRESULT</span></span>|<span data-ttu-id="4b646-107">Description</span><span class="sxs-lookup"><span data-stu-id="4b646-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4b646-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="4b646-108">S_OK</span></span>|<span data-ttu-id="4b646-109">`SuspensionStarting` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="4b646-109">`SuspensionStarting` returned successfully.</span></span>|  
|<span data-ttu-id="4b646-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4b646-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4b646-111">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="4b646-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4b646-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4b646-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4b646-113">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="4b646-113">The call timed out.</span></span>|  
|<span data-ttu-id="4b646-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4b646-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4b646-115">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="4b646-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4b646-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4b646-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4b646-117">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="4b646-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4b646-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4b646-118">E_FAIL</span></span>|<span data-ttu-id="4b646-119">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="4b646-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4b646-120">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="4b646-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4b646-121">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4b646-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b646-122">Notes</span><span class="sxs-lookup"><span data-stu-id="4b646-122">Remarks</span></span>  
 <span data-ttu-id="4b646-123">Le CLR appelle `SuspensionStarting` pour informer l’hôte que garbage collection se produit.</span><span class="sxs-lookup"><span data-stu-id="4b646-123">The CLR calls `SuspensionStarting` to inform the host that garbage collection is occurring.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4b646-124">Ne replanifiez pas cette tâche.</span><span class="sxs-lookup"><span data-stu-id="4b646-124">Do not reschedule this task.</span></span> <span data-ttu-id="4b646-125">L’hôte doit replanifier une tâche quand [ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md) est appelé.</span><span class="sxs-lookup"><span data-stu-id="4b646-125">The host must reschedule a task when [ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md) is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b646-126">spécifications</span><span class="sxs-lookup"><span data-stu-id="4b646-126">Requirements</span></span>  
 <span data-ttu-id="4b646-127">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b646-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b646-128">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4b646-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4b646-129">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4b646-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4b646-130">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b646-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b646-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4b646-131">See also</span></span>

- [<span data-ttu-id="4b646-132">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="4b646-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="4b646-133">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="4b646-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="4b646-134">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="4b646-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="4b646-135">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="4b646-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="4b646-136">IHostGCManager, interface</span><span class="sxs-lookup"><span data-stu-id="4b646-136">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
