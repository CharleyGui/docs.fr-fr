---
title: IHostSyncManager::CreateCrst, méthode
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateCrst
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateCrst
helpviewer_keywords:
- CreateCrst method [.NET Framework hosting]
- IHostSyncManager::CreateCrst method [.NET Framework hosting]
ms.assetid: ac278cc8-2540-4a6c-b5c6-b90c3970b4f4
topic_type:
- apiref
ms.openlocfilehash: 27861a9258916f4c188d981c44833e5be4c507f2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95682875"
---
# <a name="ihostsyncmanagercreatecrst-method"></a><span data-ttu-id="471fc-102">IHostSyncManager::CreateCrst, méthode</span><span class="sxs-lookup"><span data-stu-id="471fc-102">IHostSyncManager::CreateCrst Method</span></span>

<span data-ttu-id="471fc-103">Crée un objet de section critique pour la synchronisation.</span><span class="sxs-lookup"><span data-stu-id="471fc-103">Creates a critical section object for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="471fc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="471fc-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateCrst (  
    [out] IHostCrst** ppCrst  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="471fc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="471fc-105">Parameters</span></span>  

 `ppCrst`  
 <span data-ttu-id="471fc-106">à Pointeur vers l’adresse d’une instance [IHostCrst](ihostcrst-interface.md) implémentée par l’hôte, ou null si la section critique n’a pas pu être créée.</span><span class="sxs-lookup"><span data-stu-id="471fc-106">[out] A pointer to the address of an [IHostCrst](ihostcrst-interface.md) instance implemented by the host, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="471fc-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="471fc-107">Return Value</span></span>  
  
|<span data-ttu-id="471fc-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="471fc-108">HRESULT</span></span>|<span data-ttu-id="471fc-109">Description</span><span class="sxs-lookup"><span data-stu-id="471fc-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="471fc-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="471fc-110">S_OK</span></span>|<span data-ttu-id="471fc-111">`CreateCrst` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="471fc-111">`CreateCrst` returned successfully.</span></span>|  
|<span data-ttu-id="471fc-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="471fc-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="471fc-113">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="471fc-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="471fc-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="471fc-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="471fc-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="471fc-115">The call timed out.</span></span>|  
|<span data-ttu-id="471fc-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="471fc-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="471fc-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="471fc-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="471fc-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="471fc-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="471fc-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="471fc-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="471fc-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="471fc-120">E_FAIL</span></span>|<span data-ttu-id="471fc-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="471fc-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="471fc-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="471fc-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="471fc-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="471fc-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="471fc-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="471fc-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="471fc-125">Mémoire disponible insuffisante pour créer la section critique demandée.</span><span class="sxs-lookup"><span data-stu-id="471fc-125">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="471fc-126">Remarques</span><span class="sxs-lookup"><span data-stu-id="471fc-126">Remarks</span></span>  

 <span data-ttu-id="471fc-127">Les objets de section critique fournissent une synchronisation similaire à celle fournie par un objet mutex, sauf que les sections critiques peuvent être utilisées uniquement par les threads d’un processus unique.</span><span class="sxs-lookup"><span data-stu-id="471fc-127">Critical section objects provide synchronization similar to that provided by a mutex object, except that critical sections can be used only by the threads of a single process.</span></span> <span data-ttu-id="471fc-128">`CreateCrst` reflète la `InitializeCriticalSection` fonction Win32.</span><span class="sxs-lookup"><span data-stu-id="471fc-128">`CreateCrst` mirrors the Win32 `InitializeCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="471fc-129">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="471fc-129">Requirements</span></span>  

 <span data-ttu-id="471fc-130">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="471fc-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="471fc-131">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="471fc-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="471fc-132">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="471fc-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="471fc-133">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="471fc-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="471fc-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="471fc-134">See also</span></span>

- [<span data-ttu-id="471fc-135">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="471fc-135">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="471fc-136">IHostCrst, interface</span><span class="sxs-lookup"><span data-stu-id="471fc-136">IHostCrst Interface</span></span>](ihostcrst-interface.md)
- [<span data-ttu-id="471fc-137">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="471fc-137">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="471fc-138">IHostSemaphore, interface</span><span class="sxs-lookup"><span data-stu-id="471fc-138">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="471fc-139">Mutex</span><span class="sxs-lookup"><span data-stu-id="471fc-139">Mutexes</span></span>](../../../standard/threading/mutexes.md)
- [<span data-ttu-id="471fc-140">Semaphore et SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="471fc-140">Semaphore and SemaphoreSlim</span></span>](../../../standard/threading/semaphore-and-semaphoreslim.md)
