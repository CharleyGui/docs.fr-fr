---
title: IHostGCManager::ThreadIsBlockingForSuspension, méthode
ms.date: 03/30/2017
api_name:
- IHostGCManager.ThreadIsBlockingForSuspension
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager::ThreadIsBlockingForSuspension
helpviewer_keywords:
- IHostGCManager::ThreadIsBlockingForSuspension method [.NET Framework hosting]
- ThreadIsBlockingForSuspension method [.NET Framework hosting]
ms.assetid: 2657d45d-26d2-4d0a-8473-32b652e3321d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c0c59d9f5abb200b17d3c46915e73fd3b9e9c8fd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780579"
---
# <a name="ihostgcmanagerthreadisblockingforsuspension-method"></a><span data-ttu-id="25ef9-102">IHostGCManager::ThreadIsBlockingForSuspension, méthode</span><span class="sxs-lookup"><span data-stu-id="25ef9-102">IHostGCManager::ThreadIsBlockingForSuspension Method</span></span>
<span data-ttu-id="25ef9-103">Avertit l’hôte que le thread à partir duquel l’appel de méthode a été effectué sur le point de bloquer pendant un garbage collection.</span><span class="sxs-lookup"><span data-stu-id="25ef9-103">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25ef9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25ef9-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadIsBlockingForSuspension ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="25ef9-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="25ef9-105">Return Value</span></span>  
  
|<span data-ttu-id="25ef9-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="25ef9-106">HRESULT</span></span>|<span data-ttu-id="25ef9-107">Description</span><span class="sxs-lookup"><span data-stu-id="25ef9-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="25ef9-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="25ef9-108">S_OK</span></span>|<span data-ttu-id="25ef9-109">`ThreadIsBlockingForSuspension` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="25ef9-109">`ThreadIsBlockingForSuspension` returned successfully.</span></span>|  
|<span data-ttu-id="25ef9-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="25ef9-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="25ef9-111">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="25ef9-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="25ef9-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="25ef9-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="25ef9-113">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="25ef9-113">The call timed out.</span></span>|  
|<span data-ttu-id="25ef9-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="25ef9-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="25ef9-115">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="25ef9-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="25ef9-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="25ef9-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="25ef9-117">Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="25ef9-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="25ef9-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="25ef9-118">E_FAIL</span></span>|<span data-ttu-id="25ef9-119">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="25ef9-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="25ef9-120">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus.</span><span class="sxs-lookup"><span data-stu-id="25ef9-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="25ef9-121">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="25ef9-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25ef9-122">Notes</span><span class="sxs-lookup"><span data-stu-id="25ef9-122">Remarks</span></span>  
 <span data-ttu-id="25ef9-123">Le CLR appelle généralement la `ThreadIsBlockForSuspension` méthode dans la préparation d’une garbage collection, pour permettre à l’hôte de replanifier le thread pour les tâches non managées.</span><span class="sxs-lookup"><span data-stu-id="25ef9-123">The CLR typically calls the `ThreadIsBlockForSuspension` method in preparation for a garbage collection, to give the host an opportunity to reschedule the thread for unmanaged tasks.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="25ef9-124">L’hôte peut replanifier des tâches uniquement après un appel à `ThreadIsBlockingForSuspension`.</span><span class="sxs-lookup"><span data-stu-id="25ef9-124">The host can reschedule tasks only after a call to `ThreadIsBlockingForSuspension`.</span></span> <span data-ttu-id="25ef9-125">Une fois le runtime appelle [SuspensionStarting](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md), l’hôte ne doit pas replanifier une tâche.</span><span class="sxs-lookup"><span data-stu-id="25ef9-125">After the runtime calls [SuspensionStarting](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md), the host must not reschedule a task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25ef9-126">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="25ef9-126">Requirements</span></span>  
 <span data-ttu-id="25ef9-127">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25ef9-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25ef9-128">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="25ef9-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="25ef9-129">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="25ef9-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="25ef9-130">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25ef9-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25ef9-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="25ef9-131">See also</span></span>

- [<span data-ttu-id="25ef9-132">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="25ef9-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="25ef9-133">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="25ef9-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="25ef9-134">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="25ef9-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="25ef9-135">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="25ef9-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="25ef9-136">IHostGCManager, interface</span><span class="sxs-lookup"><span data-stu-id="25ef9-136">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
