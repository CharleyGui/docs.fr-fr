---
title: IHostManualEvent::Wait, méthode
ms.date: 03/30/2017
api_name:
- IHostManualEvent.Wait
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent::Wait
helpviewer_keywords:
- IHostManualEvent::Wait method [.NET Framework hosting]
- Wait method, IHostManualEvent interface [.NET Framework hosting]
ms.assetid: 1fbb7d8b-8a23-4c2b-8376-1a70cd2d6030
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2242395a02254268c9492e534309c690a343ffbe
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767267"
---
# <a name="ihostmanualeventwait-method"></a><span data-ttu-id="f565a-102">IHostManualEvent::Wait, méthode</span><span class="sxs-lookup"><span data-stu-id="f565a-102">IHostManualEvent::Wait Method</span></span>
<span data-ttu-id="f565a-103">Fait en [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance à attendre jusqu'à ce qu’il appartient, ou un certain laps de temps.</span><span class="sxs-lookup"><span data-stu-id="f565a-103">Causes the current [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance to wait until it is owned, or a specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f565a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f565a-104">Syntax</span></span>  
  
```cpp  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f565a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f565a-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="f565a-106">[in] Le nombre de millisecondes à attendre avant de retourner, si actuel `IHostManualEvent` instance n’appartient pas.</span><span class="sxs-lookup"><span data-stu-id="f565a-106">[in] The number of milliseconds to wait before returning, if the current `IHostManualEvent` instance is not owned.</span></span>  
  
 `option`  
 <span data-ttu-id="f565a-107">[in] Parmi les [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) valeurs indiquant l’action de l’hôte doit effectuer si cette opération bloque.</span><span class="sxs-lookup"><span data-stu-id="f565a-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, indicating the action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f565a-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f565a-108">Return Value</span></span>  
  
|<span data-ttu-id="f565a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f565a-109">HRESULT</span></span>|<span data-ttu-id="f565a-110">Description</span><span class="sxs-lookup"><span data-stu-id="f565a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f565a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f565a-111">S_OK</span></span>|<span data-ttu-id="f565a-112">`Wait` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="f565a-112">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="f565a-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f565a-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f565a-114">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="f565a-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f565a-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f565a-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f565a-116">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="f565a-116">The call timed out.</span></span>|  
|<span data-ttu-id="f565a-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f565a-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f565a-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="f565a-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f565a-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f565a-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f565a-120">Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="f565a-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f565a-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f565a-121">E_FAIL</span></span>|<span data-ttu-id="f565a-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="f565a-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f565a-123">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus.</span><span class="sxs-lookup"><span data-stu-id="f565a-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f565a-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f565a-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f565a-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="f565a-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="f565a-126">L’hôte a détecté un interblocage pendant l’intervalle d’attente et a choisi actuel `IHostManualEvent` instance comme victime du blocage.</span><span class="sxs-lookup"><span data-stu-id="f565a-126">The host detected a deadlock during the wait interval, and chose the current `IHostManualEvent` instance as the deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f565a-127">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f565a-127">Requirements</span></span>  
 <span data-ttu-id="f565a-128">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f565a-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f565a-129">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f565a-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f565a-130">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f565a-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f565a-131">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f565a-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f565a-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f565a-132">See also</span></span>

- [<span data-ttu-id="f565a-133">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="f565a-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="f565a-134">IHostAutoEvent, interface</span><span class="sxs-lookup"><span data-stu-id="f565a-134">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="f565a-135">IHostManualEvent, interface</span><span class="sxs-lookup"><span data-stu-id="f565a-135">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="f565a-136">IHostSemaphore, interface</span><span class="sxs-lookup"><span data-stu-id="f565a-136">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="f565a-137">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="f565a-137">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
