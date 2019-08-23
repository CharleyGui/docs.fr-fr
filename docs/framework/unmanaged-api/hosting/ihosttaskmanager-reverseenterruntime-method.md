---
title: IHostTaskManager::ReverseEnterRuntime, méthode
ms.date: 03/30/2017
api_name:
- IHostTaskManager.ReverseEnterRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::ReverseEnterRuntime
helpviewer_keywords:
- IHostTaskManager::ReverseEnterRuntime method [.NET Framework hosting]
- ReverseEnterRuntime method [.NET Framework hosting]
ms.assetid: b1e26bff-d3ea-436e-9867-29720df999f4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6e5beabb5ac1b5a4b2a34ae8e18b7fad7c86504
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959053"
---
# <a name="ihosttaskmanagerreverseenterruntime-method"></a><span data-ttu-id="08364-102">IHostTaskManager::ReverseEnterRuntime, méthode</span><span class="sxs-lookup"><span data-stu-id="08364-102">IHostTaskManager::ReverseEnterRuntime Method</span></span>
<span data-ttu-id="08364-103">Indique à l’hôte qu’un appel est effectué dans le common language runtime (CLR) à partir du code non managé.</span><span class="sxs-lookup"><span data-stu-id="08364-103">Notifies the host that a call is being made into the common language runtime (CLR) from unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08364-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08364-104">Syntax</span></span>  
  
```cpp  
HRESULT ReverseEnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="08364-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="08364-105">Return Value</span></span>  
  
|<span data-ttu-id="08364-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="08364-106">HRESULT</span></span>|<span data-ttu-id="08364-107">Description</span><span class="sxs-lookup"><span data-stu-id="08364-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="08364-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="08364-108">S_OK</span></span>|<span data-ttu-id="08364-109">`ReverseEnterRuntime`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="08364-109">`ReverseEnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="08364-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="08364-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="08364-111">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="08364-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="08364-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="08364-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="08364-113">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="08364-113">The call timed out.</span></span>|  
|<span data-ttu-id="08364-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="08364-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="08364-115">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="08364-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="08364-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="08364-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="08364-117">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="08364-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="08364-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="08364-118">E_FAIL</span></span>|<span data-ttu-id="08364-119">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="08364-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="08364-120">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="08364-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="08364-121">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="08364-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="08364-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="08364-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="08364-123">La mémoire disponible est insuffisante pour terminer l’allocation de ressources demandée.</span><span class="sxs-lookup"><span data-stu-id="08364-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08364-124">Notes</span><span class="sxs-lookup"><span data-stu-id="08364-124">Remarks</span></span>  
 <span data-ttu-id="08364-125">Si l’appel dans le CLR est effectué à partir d’une séquence provenant du code managé, chaque appel à `ReverseEnterRuntime` correspond à un appel à [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="08364-125">If the call into the CLR is made from a sequence that originated in managed code, each call to `ReverseEnterRuntime` corresponds to a call to [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="08364-126">Les appels peuvent provenir du code non managé sans être imbriqués.</span><span class="sxs-lookup"><span data-stu-id="08364-126">Calls can originate from unmanaged code without being nested.</span></span> <span data-ttu-id="08364-127">Dans ce cas, il n’y a aucun appel à [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)ou `ReverseLeaveRuntime`, et le nombre d’appels `ReverseEnterRuntime` à n’est pas égal au nombre d' `ReverseLeaveRuntime`appels à.</span><span class="sxs-lookup"><span data-stu-id="08364-127">In this case, there is no call to [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), or `ReverseLeaveRuntime`, and the number of calls to `ReverseEnterRuntime` does not equal the number of calls to `ReverseLeaveRuntime`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08364-128">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="08364-128">Requirements</span></span>  
 <span data-ttu-id="08364-129">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08364-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08364-130">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="08364-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="08364-131">**Bibliothèque** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="08364-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="08364-132">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08364-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08364-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="08364-133">See also</span></span>

- [<span data-ttu-id="08364-134">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="08364-134">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="08364-135">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="08364-135">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="08364-136">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="08364-136">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="08364-137">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="08364-137">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
