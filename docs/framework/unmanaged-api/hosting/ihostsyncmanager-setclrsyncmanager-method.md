---
title: IHostSyncManager::SetCLRSyncManager, méthode
ms.date: 03/30/2017
api_name:
- IHostSyncManager.SetCLRSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::SetCLRSyncManager
helpviewer_keywords:
- IHostSyncManager::SetCLRSyncManager method [.NET Framework hosting]
- SetCLRSyncManager method [.NET Framework hosting]
ms.assetid: 2b8bbe76-a45d-4989-bacb-11df42f8798c
topic_type:
- apiref
ms.openlocfilehash: 7f1832b22a1b80855f48eba6d39bff64da6fa5f9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501441"
---
# <a name="ihostsyncmanagersetclrsyncmanager-method"></a><span data-ttu-id="11c86-102">IHostSyncManager::SetCLRSyncManager, méthode</span><span class="sxs-lookup"><span data-stu-id="11c86-102">IHostSyncManager::SetCLRSyncManager Method</span></span>
<span data-ttu-id="11c86-103">Définit l’instance [ICLRSyncManager](iclrsyncmanager-interface.md) à associer à l’instance [IHostSyncManager](ihostsyncmanager-interface.md) actuelle.</span><span class="sxs-lookup"><span data-stu-id="11c86-103">Sets the [ICLRSyncManager](iclrsyncmanager-interface.md) instance to associate with the current [IHostSyncManager](ihostsyncmanager-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11c86-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11c86-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRSyncManager (  
    [in] ICLRSyncManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11c86-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="11c86-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="11c86-106">dans Pointeur vers une `ICLRSyncManager` instance fournie par le Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="11c86-106">[in] A pointer to an `ICLRSyncManager` instance supplied by the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="11c86-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="11c86-107">Return Value</span></span>  
  
|<span data-ttu-id="11c86-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="11c86-108">HRESULT</span></span>|<span data-ttu-id="11c86-109">Description</span><span class="sxs-lookup"><span data-stu-id="11c86-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="11c86-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="11c86-110">S_OK</span></span>|<span data-ttu-id="11c86-111">`SetCLRSyncManager`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="11c86-111">`SetCLRSyncManager` returned successfully.</span></span>|  
|<span data-ttu-id="11c86-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="11c86-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="11c86-113">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="11c86-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="11c86-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="11c86-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="11c86-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="11c86-115">The call timed out.</span></span>|  
|<span data-ttu-id="11c86-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="11c86-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="11c86-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="11c86-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="11c86-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="11c86-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="11c86-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="11c86-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="11c86-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="11c86-120">E_FAIL</span></span>|<span data-ttu-id="11c86-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="11c86-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="11c86-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="11c86-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="11c86-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="11c86-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11c86-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="11c86-124">Remarks</span></span>  
 <span data-ttu-id="11c86-125">Pour faciliter la communication entre l’hôte et le CLR, les interfaces d’hébergement sont généralement des paires.</span><span class="sxs-lookup"><span data-stu-id="11c86-125">To facilitate communication between the host and the CLR, hosting interfaces generally come in pairs.</span></span> <span data-ttu-id="11c86-126">Un membre de la paire est implémenté par l’hôte, et l’autre membre est implémenté par le CLR.</span><span class="sxs-lookup"><span data-stu-id="11c86-126">One member of the pair is implemented by the host, and the other member is implemented by the CLR.</span></span> <span data-ttu-id="11c86-127">En tant qu’implémentation côté hôte, l' `IHostSyncManager` interface correspond à l' `ICLRSyncManager` interface implémentée par le CLR.</span><span class="sxs-lookup"><span data-stu-id="11c86-127">As a host-side implementation, the `IHostSyncManager` interface corresponds to the `ICLRSyncManager` interface implemented by the CLR.</span></span> <span data-ttu-id="11c86-128">Le CLR appelle `SetCLRSyncManager` pour fournir une `ICLRSyncManager` instance que l’hôte doit associer à l' `IHostSyncManager` instance actuelle.</span><span class="sxs-lookup"><span data-stu-id="11c86-128">The CLR calls `SetCLRSyncManager` to supply an `ICLRSyncManager` instance for the host to associate with the current `IHostSyncManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11c86-129">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="11c86-129">Requirements</span></span>  
 <span data-ttu-id="11c86-130">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11c86-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11c86-131">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="11c86-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="11c86-132">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="11c86-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="11c86-133">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11c86-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11c86-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="11c86-134">See also</span></span>

- [<span data-ttu-id="11c86-135">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="11c86-135">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="11c86-136">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="11c86-136">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
