---
title: IHostTaskManager::EndThreadAffinity, méthode
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EndThreadAffinity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EndThreadAffinity
helpviewer_keywords:
- EndThreadAffinity method [.NET Framework hosting]
- IHostTaskManager::EndThreadAffinity method [.NET Framework hosting]
ms.assetid: 7738a904-0cd7-4fde-a3eb-2323a5533157
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b50e08e6fe0db7d16c87d9acccf77e2b15094039
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749638"
---
# <a name="ihosttaskmanagerendthreadaffinity-method"></a><span data-ttu-id="c2b6f-102">IHostTaskManager::EndThreadAffinity, méthode</span><span class="sxs-lookup"><span data-stu-id="c2b6f-102">IHostTaskManager::EndThreadAffinity Method</span></span>
<span data-ttu-id="c2b6f-103">Avertit l’hôte que le code managé sort de la période dans laquelle la tâche actuelle ne doit pas être déplacée vers un autre thread de système d’exploitation, à la suite d’un appel précédent à [IHostTaskManager::BeginThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md).</span><span class="sxs-lookup"><span data-stu-id="c2b6f-103">Notifies the host that managed code is exiting the period in which the current task must not be moved to another operating system thread, following an earlier call to [IHostTaskManager::BeginThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2b6f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c2b6f-104">Syntax</span></span>  
  
```cpp  
HRESULT EndThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="c2b6f-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c2b6f-105">Return Value</span></span>  
  
|<span data-ttu-id="c2b6f-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c2b6f-106">HRESULT</span></span>|<span data-ttu-id="c2b6f-107">Description</span><span class="sxs-lookup"><span data-stu-id="c2b6f-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c2b6f-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="c2b6f-108">S_OK</span></span>|<span data-ttu-id="c2b6f-109">`EndThreadAffinity` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="c2b6f-109">`EndThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="c2b6f-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c2b6f-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c2b6f-111">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="c2b6f-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c2b6f-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c2b6f-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c2b6f-113">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="c2b6f-113">The call timed out.</span></span>|  
|<span data-ttu-id="c2b6f-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c2b6f-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c2b6f-115">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="c2b6f-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c2b6f-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c2b6f-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c2b6f-117">Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="c2b6f-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c2b6f-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c2b6f-118">E_FAIL</span></span>|<span data-ttu-id="c2b6f-119">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="c2b6f-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c2b6f-120">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus.</span><span class="sxs-lookup"><span data-stu-id="c2b6f-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c2b6f-121">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c2b6f-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c2b6f-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="c2b6f-122">E_UNEXPECTED</span></span>|<span data-ttu-id="c2b6f-123">`EndThreadAffinity` a été appelée sans appel antérieur correspondant à `BeginThreadAffinity`.</span><span class="sxs-lookup"><span data-stu-id="c2b6f-123">`EndThreadAffinity` was called without an earlier corresponding call to `BeginThreadAffinity`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2b6f-124">Notes</span><span class="sxs-lookup"><span data-stu-id="c2b6f-124">Remarks</span></span>  
 <span data-ttu-id="c2b6f-125">Le CLR effectue un appel correspondant à `BeginThreadAffinity` sur la tâche en cours avant d’appeler `EndThreadAffinity`.</span><span class="sxs-lookup"><span data-stu-id="c2b6f-125">The CLR makes a corresponding call to `BeginThreadAffinity` on the current task before calling `EndThreadAffinity`.</span></span> <span data-ttu-id="c2b6f-126">En l’absence d’un tel appel correspondant, implémentation de l’hôte de [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) doit retourner E_UNEXPECTED et ne rien faire.</span><span class="sxs-lookup"><span data-stu-id="c2b6f-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) should return E_UNEXPECTED, and take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2b6f-127">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c2b6f-127">Requirements</span></span>  
 <span data-ttu-id="c2b6f-128">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2b6f-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2b6f-129">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c2b6f-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c2b6f-130">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c2b6f-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c2b6f-131">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2b6f-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2b6f-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c2b6f-132">See also</span></span>

- <xref:System.Threading>
- [<span data-ttu-id="c2b6f-133">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="c2b6f-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="c2b6f-134">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="c2b6f-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="c2b6f-135">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="c2b6f-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="c2b6f-136">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="c2b6f-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
