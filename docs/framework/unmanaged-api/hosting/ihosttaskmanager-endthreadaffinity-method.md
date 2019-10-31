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
ms.openlocfilehash: c40febb78c1bc78a5a724f559eb95869e90bdad0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133089"
---
# <a name="ihosttaskmanagerendthreadaffinity-method"></a><span data-ttu-id="28476-102">IHostTaskManager::EndThreadAffinity, méthode</span><span class="sxs-lookup"><span data-stu-id="28476-102">IHostTaskManager::EndThreadAffinity Method</span></span>
<span data-ttu-id="28476-103">Avertit l’hôte que le code managé quitte la période pendant laquelle la tâche actuelle ne doit pas être déplacée vers un autre thread de système d’exploitation, à la suite d’un appel antérieur à [IHostTaskManager :: BeginThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md).</span><span class="sxs-lookup"><span data-stu-id="28476-103">Notifies the host that managed code is exiting the period in which the current task must not be moved to another operating system thread, following an earlier call to [IHostTaskManager::BeginThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28476-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="28476-104">Syntax</span></span>  
  
```cpp  
HRESULT EndThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="28476-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="28476-105">Return Value</span></span>  
  
|<span data-ttu-id="28476-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="28476-106">HRESULT</span></span>|<span data-ttu-id="28476-107">Description</span><span class="sxs-lookup"><span data-stu-id="28476-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="28476-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="28476-108">S_OK</span></span>|<span data-ttu-id="28476-109">`EndThreadAffinity` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="28476-109">`EndThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="28476-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="28476-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="28476-111">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="28476-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="28476-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="28476-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="28476-113">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="28476-113">The call timed out.</span></span>|  
|<span data-ttu-id="28476-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="28476-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="28476-115">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="28476-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="28476-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="28476-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="28476-117">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="28476-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="28476-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="28476-118">E_FAIL</span></span>|<span data-ttu-id="28476-119">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="28476-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="28476-120">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="28476-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="28476-121">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="28476-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="28476-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="28476-122">E_UNEXPECTED</span></span>|<span data-ttu-id="28476-123">`EndThreadAffinity` a été appelée sans appel correspondant antérieur à `BeginThreadAffinity`.</span><span class="sxs-lookup"><span data-stu-id="28476-123">`EndThreadAffinity` was called without an earlier corresponding call to `BeginThreadAffinity`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28476-124">Notes</span><span class="sxs-lookup"><span data-stu-id="28476-124">Remarks</span></span>  
 <span data-ttu-id="28476-125">Le CLR effectue un appel correspondant à `BeginThreadAffinity` sur la tâche actuelle avant d’appeler `EndThreadAffinity`.</span><span class="sxs-lookup"><span data-stu-id="28476-125">The CLR makes a corresponding call to `BeginThreadAffinity` on the current task before calling `EndThreadAffinity`.</span></span> <span data-ttu-id="28476-126">En l’absence d’un tel appel, l’implémentation de [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) par l’hôte doit retourner E_UNEXPECTED et ne pas effectuer d’action.</span><span class="sxs-lookup"><span data-stu-id="28476-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) should return E_UNEXPECTED, and take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28476-127">spécifications</span><span class="sxs-lookup"><span data-stu-id="28476-127">Requirements</span></span>  
 <span data-ttu-id="28476-128">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28476-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28476-129">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="28476-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="28476-130">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="28476-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="28476-131">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28476-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28476-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="28476-132">See also</span></span>

- <xref:System.Threading>
- [<span data-ttu-id="28476-133">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="28476-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="28476-134">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="28476-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="28476-135">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="28476-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="28476-136">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="28476-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
