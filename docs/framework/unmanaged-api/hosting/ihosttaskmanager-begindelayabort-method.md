---
title: IHostTaskManager::BeginDelayAbort, méthode
ms.date: 03/30/2017
api_name:
- IHostTaskManager.BeginDelayAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::BeginDelayAbort
helpviewer_keywords:
- BeginDelayAbort method [.NET Framework hosting]
- IHostTaskManager::BeginDelayAbort method [.NET Framework hosting]
ms.assetid: 75f42a8b-ed68-4718-a030-a179cfba7d72
topic_type:
- apiref
ms.openlocfilehash: b765d5449cebbdec5f106a8e4743fee2f0ee5521
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133140"
---
# <a name="ihosttaskmanagerbegindelayabort-method"></a><span data-ttu-id="9eb3a-102">IHostTaskManager::BeginDelayAbort, méthode</span><span class="sxs-lookup"><span data-stu-id="9eb3a-102">IHostTaskManager::BeginDelayAbort Method</span></span>
<span data-ttu-id="9eb3a-103">Indique à l’hôte que le code managé entre dans une période dans laquelle la tâche en cours ne doit pas être abandonnée.</span><span class="sxs-lookup"><span data-stu-id="9eb3a-103">Notifies the host that managed code is entering a period in which the current task must not be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9eb3a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9eb3a-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="9eb3a-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="9eb3a-105">Return Value</span></span>  
  
|<span data-ttu-id="9eb3a-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9eb3a-106">HRESULT</span></span>|<span data-ttu-id="9eb3a-107">Description</span><span class="sxs-lookup"><span data-stu-id="9eb3a-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9eb3a-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="9eb3a-108">S_OK</span></span>|<span data-ttu-id="9eb3a-109">`BeginDelayAbort` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="9eb3a-109">`BeginDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="9eb3a-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9eb3a-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9eb3a-111">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="9eb3a-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9eb3a-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9eb3a-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9eb3a-113">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="9eb3a-113">The call timed out.</span></span>|  
|<span data-ttu-id="9eb3a-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9eb3a-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9eb3a-115">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="9eb3a-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9eb3a-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9eb3a-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9eb3a-117">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="9eb3a-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9eb3a-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9eb3a-118">E_FAIL</span></span>|<span data-ttu-id="9eb3a-119">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="9eb3a-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9eb3a-120">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="9eb3a-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9eb3a-121">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9eb3a-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9eb3a-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="9eb3a-122">E_UNEXPECTED</span></span>|<span data-ttu-id="9eb3a-123">`BeginDelayAbort` a déjà été appelé, mais l’appel correspondant à [EndDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md) n’a pas encore été reçu.</span><span class="sxs-lookup"><span data-stu-id="9eb3a-123">`BeginDelayAbort` has already been called, but the corresponding call to [EndDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md) has not yet been received.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9eb3a-124">Notes</span><span class="sxs-lookup"><span data-stu-id="9eb3a-124">Remarks</span></span>  
 <span data-ttu-id="9eb3a-125">L’hôte ne doit pas abandonner la tâche en cours tant que `EndDelayAbort` n’est pas appelé.</span><span class="sxs-lookup"><span data-stu-id="9eb3a-125">The host must not abort the current task until `EndDelayAbort` is called.</span></span> <span data-ttu-id="9eb3a-126">Si un autre appel à `BeginDelayAbort` est effectué sans appel intermédiaire à `EndDelayAbort`, l’hôte doit retourner E_UNEXPECTED à partir de `BeginDelayAbort`et ne doit effectuer aucune action.</span><span class="sxs-lookup"><span data-stu-id="9eb3a-126">If another call to `BeginDelayAbort` is made without an intervening call to `EndDelayAbort`, the host should return E_UNEXPECTED from `BeginDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9eb3a-127">spécifications</span><span class="sxs-lookup"><span data-stu-id="9eb3a-127">Requirements</span></span>  
 <span data-ttu-id="9eb3a-128">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9eb3a-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9eb3a-129">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9eb3a-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9eb3a-130">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9eb3a-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9eb3a-131">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9eb3a-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9eb3a-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9eb3a-132">See also</span></span>

- [<span data-ttu-id="9eb3a-133">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="9eb3a-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="9eb3a-134">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="9eb3a-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="9eb3a-135">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="9eb3a-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
