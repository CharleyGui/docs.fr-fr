---
title: IHostSyncManager::CreateSemaphore, méthode
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateSemaphore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateSemaphore
helpviewer_keywords:
- CreateSemaphore method [.NET Framework hosting]
- IHostSyncManager::CreateSemaphore method [.NET Framework hosting]
ms.assetid: 37679e94-5ff9-4173-8fa5-457febeb89bf
topic_type:
- apiref
ms.openlocfilehash: 02066d3923714e66bf287f1435b7854280c97cb7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195833"
---
# <a name="ihostsyncmanagercreatesemaphore-method"></a><span data-ttu-id="6e21d-102">IHostSyncManager::CreateSemaphore, méthode</span><span class="sxs-lookup"><span data-stu-id="6e21d-102">IHostSyncManager::CreateSemaphore Method</span></span>
<span data-ttu-id="6e21d-103">Crée un objet [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) pour le Common Language Runtime (CLR) à utiliser comme sémaphore pour les événements d’attente.</span><span class="sxs-lookup"><span data-stu-id="6e21d-103">Creates an [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) object for the common language runtime (CLR) to use as a semaphore for wait events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e21d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6e21d-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateSemaphore (  
    [in]  DWORD dwInitial,  
    [in]  DWORD dwMax,  
    [out] IHostSemaphore **ppSemaphore  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e21d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6e21d-105">Parameters</span></span>  
 `dwInitial`  
 <span data-ttu-id="6e21d-106">dans Nombre initial de `ppSemaphore`.</span><span class="sxs-lookup"><span data-stu-id="6e21d-106">[in] The initial count for `ppSemaphore`.</span></span>  
  
 `dwMax`  
 <span data-ttu-id="6e21d-107">dans Nombre maximal de `ppSemaphore`.</span><span class="sxs-lookup"><span data-stu-id="6e21d-107">[in] The maximum count for `ppSemaphore`.</span></span>  
  
 `ppSemaphore`  
 <span data-ttu-id="6e21d-108">à Pointeur vers l’adresse d’une instance de `IHostSemaphore`, ou null si le sémaphore n’a pas pu être créé.</span><span class="sxs-lookup"><span data-stu-id="6e21d-108">[out] A pointer to the address of an `IHostSemaphore` instance, or null if the semaphore could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6e21d-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="6e21d-109">Return Value</span></span>  
  
|<span data-ttu-id="6e21d-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6e21d-110">HRESULT</span></span>|<span data-ttu-id="6e21d-111">Description</span><span class="sxs-lookup"><span data-stu-id="6e21d-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6e21d-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="6e21d-112">S_OK</span></span>|<span data-ttu-id="6e21d-113">`CreateSemaphore` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="6e21d-113">`CreateSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="6e21d-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6e21d-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6e21d-115">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="6e21d-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6e21d-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6e21d-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6e21d-117">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="6e21d-117">The call timed out.</span></span>|  
|<span data-ttu-id="6e21d-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6e21d-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6e21d-119">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="6e21d-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6e21d-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6e21d-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6e21d-121">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="6e21d-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6e21d-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6e21d-122">E_FAIL</span></span>|<span data-ttu-id="6e21d-123">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="6e21d-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6e21d-124">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="6e21d-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6e21d-125">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6e21d-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6e21d-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="6e21d-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="6e21d-127">Mémoire disponible insuffisante pour créer l’objet d’événement demandé.</span><span class="sxs-lookup"><span data-stu-id="6e21d-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e21d-128">Notes</span><span class="sxs-lookup"><span data-stu-id="6e21d-128">Remarks</span></span>  
 <span data-ttu-id="6e21d-129">`CreateSemaphore` reflète la fonction Win32 qui porte le même nom.</span><span class="sxs-lookup"><span data-stu-id="6e21d-129">`CreateSemaphore` mirrors the Win32 function that has the same name.</span></span> <span data-ttu-id="6e21d-130">Les paramètres `dwInitial` et `dwMax` utilisent la même sémantique pour le nombre de sémaphores que les paramètres `lInitialCount` et `lMaximumCount` Win32, respectivement.</span><span class="sxs-lookup"><span data-stu-id="6e21d-130">The `dwInitial` and `dwMax` parameters use the same semantics for the semaphore count as the Win32 `lInitialCount` and `lMaximumCount` parameters, respectively.</span></span> <span data-ttu-id="6e21d-131">`dwInitial` doit être compris entre zéro et `dwMax`, inclus.</span><span class="sxs-lookup"><span data-stu-id="6e21d-131">`dwInitial` must be between zero and `dwMax`, inclusive.</span></span> <span data-ttu-id="6e21d-132">`dwMax` doit être supérieur à zéro.</span><span class="sxs-lookup"><span data-stu-id="6e21d-132">`dwMax` must be greater than zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e21d-133">spécifications</span><span class="sxs-lookup"><span data-stu-id="6e21d-133">Requirements</span></span>  
 <span data-ttu-id="6e21d-134">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e21d-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e21d-135">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6e21d-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6e21d-136">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6e21d-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6e21d-137">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e21d-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e21d-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6e21d-138">See also</span></span>

- [<span data-ttu-id="6e21d-139">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="6e21d-139">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="6e21d-140">IHostSemaphore, interface</span><span class="sxs-lookup"><span data-stu-id="6e21d-140">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="6e21d-141">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="6e21d-141">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
