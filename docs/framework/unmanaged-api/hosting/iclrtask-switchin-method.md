---
title: ICLRTask::SwitchIn, méthode
ms.date: 03/30/2017
api_name:
- ICLRTask.SwitchIn
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::SwitchIn
helpviewer_keywords:
- ICLRTask::SwitchIn method [.NET Framework hosting]
- SwitchIn method [.NET Framework hosting]
ms.assetid: 3d37ce20-aa65-4043-8f13-7c728b5d8a52
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f408dd5e4d383040d9e3c03cd5bba8ebd320610f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938368"
---
# <a name="iclrtaskswitchin-method"></a><span data-ttu-id="9df0a-102">ICLRTask::SwitchIn, méthode</span><span class="sxs-lookup"><span data-stu-id="9df0a-102">ICLRTask::SwitchIn Method</span></span>
<span data-ttu-id="9df0a-103">Avertit le common language runtime (CLR) que la tâche que [l’instance de](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) l’instance actuelle représente est désormais dans un état de fonctionnement.</span><span class="sxs-lookup"><span data-stu-id="9df0a-103">Notifies the common language runtime (CLR) that the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents is now in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9df0a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9df0a-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchIn (  
    [in] HANDLE threadHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9df0a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9df0a-105">Parameters</span></span>  
 `threadHandle`  
 <span data-ttu-id="9df0a-106">dans Handle vers le thread physique sur lequel la tâche représentée par l’instance actuelle `ICLRTask` s’exécute.</span><span class="sxs-lookup"><span data-stu-id="9df0a-106">[in] A handle to the physical thread on which the task represented by the current `ICLRTask` instance is executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9df0a-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="9df0a-107">Return Value</span></span>  
  
|<span data-ttu-id="9df0a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9df0a-108">HRESULT</span></span>|<span data-ttu-id="9df0a-109">Description</span><span class="sxs-lookup"><span data-stu-id="9df0a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9df0a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9df0a-110">S_OK</span></span>|<span data-ttu-id="9df0a-111">`SwitchIn`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="9df0a-111">`SwitchIn` returned successfully.</span></span>|  
|<span data-ttu-id="9df0a-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9df0a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9df0a-113">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="9df0a-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9df0a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9df0a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9df0a-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="9df0a-115">The call timed out.</span></span>|  
|<span data-ttu-id="9df0a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9df0a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9df0a-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="9df0a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9df0a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9df0a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9df0a-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="9df0a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9df0a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9df0a-120">E_FAIL</span></span>|<span data-ttu-id="9df0a-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="9df0a-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9df0a-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="9df0a-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9df0a-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9df0a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9df0a-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="9df0a-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="9df0a-125">`SwitchIn`a été appelé sans appel antérieur à la [méthode SwitchOut](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md).</span><span class="sxs-lookup"><span data-stu-id="9df0a-125">`SwitchIn` was called without an earlier call to [SwitchOut Method](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9df0a-126">Notes</span><span class="sxs-lookup"><span data-stu-id="9df0a-126">Remarks</span></span>  
 <span data-ttu-id="9df0a-127">Le `threadHandle` paramètre représente un handle vers le thread de système d’exploitation sur lequel la tâche représentée par `ICLRTask` l’instance actuelle a été planifiée.</span><span class="sxs-lookup"><span data-stu-id="9df0a-127">The `threadHandle` parameter represents a handle to the operating system thread on which the task represented by the current `ICLRTask` instance has been scheduled.</span></span> <span data-ttu-id="9df0a-128">Si l’emprunt d’identité s’est produit sur ce thread, vous devez appeler [IHostSecurityManager :: RevertToSelf](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md) avant de basculer dans la tâche.</span><span class="sxs-lookup"><span data-stu-id="9df0a-128">If impersonation has occurred on this thread, you must call [IHostSecurityManager::RevertToSelf](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md) before switching in the task.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9df0a-129">Un appel à `SwitchIn` sans appel antérieur à `SwitchOut` échoue avec une valeur HRESULT de HOST_E_INVALIDOPERATION.</span><span class="sxs-lookup"><span data-stu-id="9df0a-129">A call to `SwitchIn` without an earlier call to `SwitchOut` fails with an HRESULT value of HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9df0a-130">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9df0a-130">Requirements</span></span>  
 <span data-ttu-id="9df0a-131">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9df0a-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9df0a-132">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9df0a-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9df0a-133">**Bibliothèque** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9df0a-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9df0a-134">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9df0a-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9df0a-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9df0a-135">See also</span></span>

- [<span data-ttu-id="9df0a-136">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="9df0a-136">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="9df0a-137">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="9df0a-137">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="9df0a-138">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="9df0a-138">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="9df0a-139">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="9df0a-139">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
