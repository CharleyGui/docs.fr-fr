---
title: ICLRSyncManager::GetMonitorOwner, méthode
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.GetMonitorOwner
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::GetMonitorOwner
helpviewer_keywords:
- ICLRSyncManager::GetMonitorOwner method [.NET Framework hosting]
- GetMonitorOwner method [.NET Framework hosting]
ms.assetid: 840983a4-396d-47b4-86a0-d35f9b437cdb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2e08af840d1c4a654fa9b9ff8b2064f5265afaf9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943243"
---
# <a name="iclrsyncmanagergetmonitorowner-method"></a><span data-ttu-id="95531-102">ICLRSyncManager::GetMonitorOwner, méthode</span><span class="sxs-lookup"><span data-stu-id="95531-102">ICLRSyncManager::GetMonitorOwner Method</span></span>
<span data-ttu-id="95531-103">Obtient l’instance [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) qui possède le moniteur identifié par le cookie spécifié.</span><span class="sxs-lookup"><span data-stu-id="95531-103">Gets the [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that owns the monitor identified by the specified cookie.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95531-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95531-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMonitorOwner (  
    [in]  SIZE_T     cookie,  
    [out] IHostTask *ppOwnerHostTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95531-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="95531-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="95531-106">dans Cookie associé à l’analyse.</span><span class="sxs-lookup"><span data-stu-id="95531-106">[in] The cookie associated with the monitor.</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="95531-107">à Pointeur vers `IHostTask` qui possède actuellement le moniteur, ou null si aucune tâche n’est propriétaire.</span><span class="sxs-lookup"><span data-stu-id="95531-107">[out] A pointer to the `IHostTask` that currently owns the monitor, or null if no task has ownership.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="95531-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="95531-108">Return Value</span></span>  
  
|<span data-ttu-id="95531-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="95531-109">HRESULT</span></span>|<span data-ttu-id="95531-110">Description</span><span class="sxs-lookup"><span data-stu-id="95531-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="95531-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="95531-111">S_OK</span></span>|<span data-ttu-id="95531-112">`GetMonitorOwner`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="95531-112">`GetMonitorOwner` returned successfully.</span></span>|  
|<span data-ttu-id="95531-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="95531-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="95531-114">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="95531-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="95531-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="95531-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="95531-116">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="95531-116">The call timed out.</span></span>|  
|<span data-ttu-id="95531-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="95531-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="95531-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="95531-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="95531-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="95531-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="95531-120">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="95531-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="95531-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="95531-121">E_FAIL</span></span>|<span data-ttu-id="95531-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="95531-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="95531-123">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="95531-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="95531-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="95531-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95531-125">Notes</span><span class="sxs-lookup"><span data-stu-id="95531-125">Remarks</span></span>  
 <span data-ttu-id="95531-126">L’hôte appelle `GetMonitorOwner` généralement dans le cadre d’un mécanisme de détection des verrous mortels.</span><span class="sxs-lookup"><span data-stu-id="95531-126">The host typically calls `GetMonitorOwner` as part of a deadlock-detection mechanism.</span></span> <span data-ttu-id="95531-127">Le cookie est associé à une analyse lorsqu’il est créé à l’aide d’un appel à [IHostSyncManager:: CreateMonitorEvent](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md).</span><span class="sxs-lookup"><span data-stu-id="95531-127">The cookie is associated with a monitor when it is created by using a call to [IHostSyncManager::CreateMonitorEvent](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="95531-128">Un appel pour libérer l’événement sous-jacent du moniteur peut se bloquer, mais n’interbloquera pas, si un appel à cette méthode est actuellement en vigueur sur le cookie associé à cette analyse.</span><span class="sxs-lookup"><span data-stu-id="95531-128">A call to release the event underlying the monitor might block—but will not deadlock—if a call to this method is currently in effect on the cookie associated with that monitor.</span></span> <span data-ttu-id="95531-129">D’autres tâches peuvent également se bloquer si elles essaient d’acquérir ce moniteur.</span><span class="sxs-lookup"><span data-stu-id="95531-129">Other tasks might also block if they attempt to acquire this monitor.</span></span>  
  
 <span data-ttu-id="95531-130">`GetMonitorOwner`retourne toujours immédiatement et peut être appelé à tout moment après un appel `CreateMonitorEvent`à.</span><span class="sxs-lookup"><span data-stu-id="95531-130">`GetMonitorOwner` always returns immediately and can be called any time after a call to `CreateMonitorEvent`.</span></span> <span data-ttu-id="95531-131">L’hôte n’a pas besoin d’attendre qu’une tâche attende l’événement.</span><span class="sxs-lookup"><span data-stu-id="95531-131">The host does not need to wait until a task is waiting on the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95531-132">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="95531-132">Requirements</span></span>  
 <span data-ttu-id="95531-133">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95531-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95531-134">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="95531-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="95531-135">**Bibliothèque** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="95531-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="95531-136">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95531-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95531-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95531-137">See also</span></span>

- [<span data-ttu-id="95531-138">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="95531-138">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="95531-139">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="95531-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
