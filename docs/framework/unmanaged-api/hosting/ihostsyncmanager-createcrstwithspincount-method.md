---
title: IHostSyncManager::CreateCrstWithSpinCount, méthode
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateCrstWithSpinCount
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateCrstWithSpinCount
helpviewer_keywords:
- CreateCrstWithSpinCount method [.NET Framework hosting]
- IHostSyncManager::CreateCrstWithSpinCount method [.NET Framework hosting]
ms.assetid: 7280fa8c-3639-4abf-91cb-bc343da742d1
topic_type:
- apiref
ms.openlocfilehash: 632b8d43ed459d489825dc796d39864e2ed15ec3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139411"
---
# <a name="ihostsyncmanagercreatecrstwithspincount-method"></a><span data-ttu-id="79a43-102">IHostSyncManager::CreateCrstWithSpinCount, méthode</span><span class="sxs-lookup"><span data-stu-id="79a43-102">IHostSyncManager::CreateCrstWithSpinCount Method</span></span>
<span data-ttu-id="79a43-103">Crée un objet de section critique avec le nombre de spins pour la synchronisation.</span><span class="sxs-lookup"><span data-stu-id="79a43-103">Creates a critical section object with spin count for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79a43-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="79a43-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateCrstWithSpinCount (  
    [in]  DWORD dwSpinCount,  
    [out] IHostCrst** ppCrst  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79a43-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="79a43-105">Parameters</span></span>  
 `dwSpinCount`  
 <span data-ttu-id="79a43-106">dans Spécifie le nombre de spins pour l’objet de section critique.</span><span class="sxs-lookup"><span data-stu-id="79a43-106">[in] Specifies the spin count for the critical section object.</span></span>  
  
 `ppCrst`  
 <span data-ttu-id="79a43-107">à Pointeur vers l’adresse d’une instance [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) , ou null si la section critique n’a pas pu être créée.</span><span class="sxs-lookup"><span data-stu-id="79a43-107">[out] A pointer to the address of an [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="79a43-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="79a43-108">Return Value</span></span>  
  
|<span data-ttu-id="79a43-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="79a43-109">HRESULT</span></span>|<span data-ttu-id="79a43-110">Description</span><span class="sxs-lookup"><span data-stu-id="79a43-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="79a43-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="79a43-111">S_OK</span></span>|<span data-ttu-id="79a43-112">`CreateCrstWithSpinCount` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="79a43-112">`CreateCrstWithSpinCount` returned successfully.</span></span>|  
|<span data-ttu-id="79a43-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="79a43-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="79a43-114">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="79a43-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="79a43-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="79a43-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="79a43-116">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="79a43-116">The call timed out.</span></span>|  
|<span data-ttu-id="79a43-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="79a43-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="79a43-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="79a43-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="79a43-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="79a43-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="79a43-120">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="79a43-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="79a43-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="79a43-121">E_FAIL</span></span>|<span data-ttu-id="79a43-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="79a43-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="79a43-123">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="79a43-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="79a43-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="79a43-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="79a43-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="79a43-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="79a43-126">Mémoire disponible insuffisante pour créer la section critique demandée.</span><span class="sxs-lookup"><span data-stu-id="79a43-126">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="79a43-127">Notes</span><span class="sxs-lookup"><span data-stu-id="79a43-127">Remarks</span></span>  
 <span data-ttu-id="79a43-128">Un nombre de spins est utilisé uniquement sur un système multiprocesseur.</span><span class="sxs-lookup"><span data-stu-id="79a43-128">A spin count is used only on a multi-processor system.</span></span> <span data-ttu-id="79a43-129">Le nombre de spins spécifie le nombre de fois qu’un thread appelant doit tourner avant d’effectuer une opération d’attente sur un sémaphore associé à une section critique non disponible.</span><span class="sxs-lookup"><span data-stu-id="79a43-129">The spin count specifies the number of times a calling thread must spin before it performs a wait operation on a semaphore that is associated with an unavailable critical section.</span></span> <span data-ttu-id="79a43-130">Si la section critique devient libre pendant l’opération de rotation, le thread appelant évite l’opération d’attente.</span><span class="sxs-lookup"><span data-stu-id="79a43-130">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span> <span data-ttu-id="79a43-131">`CreateCrstWithSpinCount` reflète la fonction Win32 `InitializeCriticalSectionAndSpinCount`.</span><span class="sxs-lookup"><span data-stu-id="79a43-131">`CreateCrstWithSpinCount` mirrors the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79a43-132">spécifications</span><span class="sxs-lookup"><span data-stu-id="79a43-132">Requirements</span></span>  
 <span data-ttu-id="79a43-133">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79a43-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79a43-134">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="79a43-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="79a43-135">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="79a43-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="79a43-136">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79a43-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79a43-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="79a43-137">See also</span></span>

- [<span data-ttu-id="79a43-138">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="79a43-138">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="79a43-139">IHostSemaphore, interface</span><span class="sxs-lookup"><span data-stu-id="79a43-139">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="79a43-140">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="79a43-140">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
