---
title: IHostSemaphore::Wait, méthode
ms.date: 03/30/2017
api_name:
- IHostSemaphore.Wait
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSemaphore::Wait
helpviewer_keywords:
- IHostSemaphore::Wait method [.NET Framework hosting]
- Wait method, IHostSemaphore interface [.NET Framework hosting]
ms.assetid: 0da962a3-ce55-44dd-ab7a-14ad7105af4a
topic_type:
- apiref
ms.openlocfilehash: bf09f7bc6c3e3aabfc16f9cad277c46be024b01d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139456"
---
# <a name="ihostsemaphorewait-method"></a><span data-ttu-id="9967a-102">IHostSemaphore::Wait, méthode</span><span class="sxs-lookup"><span data-stu-id="9967a-102">IHostSemaphore::Wait Method</span></span>
<span data-ttu-id="9967a-103">Entraîne l’attente de l’instance [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) actuelle jusqu’à ce qu’elle appartienne ou que la durée spécifiée soit écoulée.</span><span class="sxs-lookup"><span data-stu-id="9967a-103">Causes the current [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) instance to wait until it is owned or the specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9967a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9967a-104">Syntax</span></span>  
  
```cpp  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9967a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9967a-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="9967a-106">dans Nombre de millisecondes à attendre avant de retourner, si l’instance de `IHostSemaphore` actuelle n’appartient pas.</span><span class="sxs-lookup"><span data-stu-id="9967a-106">[in] The number of milliseconds to wait before returning, if the current `IHostSemaphore` instance is not owned.</span></span>  
  
 `option`  
 <span data-ttu-id="9967a-107">dans L’une des valeurs [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) , en spécifiant l’action que l’hôte doit effectuer si cette opération bloque.</span><span class="sxs-lookup"><span data-stu-id="9967a-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, specifying what action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9967a-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="9967a-108">Return Value</span></span>  
  
|<span data-ttu-id="9967a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9967a-109">HRESULT</span></span>|<span data-ttu-id="9967a-110">Description</span><span class="sxs-lookup"><span data-stu-id="9967a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9967a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="9967a-111">S_OK</span></span>|<span data-ttu-id="9967a-112">`Wait` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="9967a-112">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="9967a-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9967a-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9967a-114">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="9967a-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9967a-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9967a-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9967a-116">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="9967a-116">The call timed out.</span></span>|  
|<span data-ttu-id="9967a-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9967a-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9967a-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="9967a-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9967a-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9967a-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9967a-120">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="9967a-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9967a-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9967a-121">E_FAIL</span></span>|<span data-ttu-id="9967a-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="9967a-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9967a-123">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="9967a-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9967a-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9967a-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9967a-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="9967a-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="9967a-126">L’hôte a détecté un blocage pendant l’intervalle d’attente et a choisi l’instance de `IHostSemaphore` actuelle comme victime de blocage.</span><span class="sxs-lookup"><span data-stu-id="9967a-126">The host detected a deadlock during the wait interval, and chose the current `IHostSemaphore` instance as a deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9967a-127">spécifications</span><span class="sxs-lookup"><span data-stu-id="9967a-127">Requirements</span></span>  
 <span data-ttu-id="9967a-128">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9967a-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9967a-129">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9967a-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9967a-130">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9967a-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9967a-131">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9967a-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9967a-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9967a-132">See also</span></span>

- [<span data-ttu-id="9967a-133">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="9967a-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="9967a-134">IHostAutoEvent, interface</span><span class="sxs-lookup"><span data-stu-id="9967a-134">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="9967a-135">IHostManualEvent, interface</span><span class="sxs-lookup"><span data-stu-id="9967a-135">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="9967a-136">IHostSemaphore, interface</span><span class="sxs-lookup"><span data-stu-id="9967a-136">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="9967a-137">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="9967a-137">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
