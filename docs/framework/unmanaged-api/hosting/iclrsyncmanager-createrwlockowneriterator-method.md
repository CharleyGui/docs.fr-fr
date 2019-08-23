---
title: ICLRSyncManager::CreateRWLockOwnerIterator, méthode
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.CreateRWLockOwnerIterator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::CreateRWLockOwnerIterator
helpviewer_keywords:
- ICLRSyncManager::CreateRWLockOwnerIterator method [.NET Framework hosting]
- CreateRWLockOwnerIterator method [.NET Framework hosting]
ms.assetid: b5535b87-9439-424e-b9b3-7d6fafb9819e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 64179e132cfaffbb1fcdc2cd0a47bbcc11be2ff0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943271"
---
# <a name="iclrsyncmanagercreaterwlockowneriterator-method"></a><span data-ttu-id="9e228-102">ICLRSyncManager::CreateRWLockOwnerIterator, méthode</span><span class="sxs-lookup"><span data-stu-id="9e228-102">ICLRSyncManager::CreateRWLockOwnerIterator Method</span></span>
<span data-ttu-id="9e228-103">Demande que le common language runtime (CLR) crée un itérateur que l’hôte doit utiliser pour déterminer l’ensemble des tâches en attente sur un verrou de lecteur-writer.</span><span class="sxs-lookup"><span data-stu-id="9e228-103">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e228-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9e228-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateRWLockOwnerIterator (  
    [in]  SIZE_T    cookie,  
    [out] SIZE_T   *pIterator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e228-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9e228-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="9e228-106">dans Cookie associé au verrou lecteur-writer souhaité.</span><span class="sxs-lookup"><span data-stu-id="9e228-106">[in] The cookie associated with the desired reader-writer lock.</span></span>  
  
 `pIterator`  
 <span data-ttu-id="9e228-107">à Pointeur vers un itérateur qui peut être passé aux méthodes [GetRWLockOwnerNext,](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md) et [DeleteRWLockOwnerIterator,](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) .</span><span class="sxs-lookup"><span data-stu-id="9e228-107">[out] A pointer to an iterator that can be passed to the [GetRWLockOwnerNext](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md) and [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) methods.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9e228-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="9e228-108">Return Value</span></span>  
  
|<span data-ttu-id="9e228-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9e228-109">HRESULT</span></span>|<span data-ttu-id="9e228-110">Description</span><span class="sxs-lookup"><span data-stu-id="9e228-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9e228-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="9e228-111">S_OK</span></span>|<span data-ttu-id="9e228-112">`CreateRWLockOwnerIterator`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="9e228-112">`CreateRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="9e228-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9e228-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9e228-114">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="9e228-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9e228-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9e228-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9e228-116">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="9e228-116">The call timed out.</span></span>|  
|<span data-ttu-id="9e228-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9e228-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9e228-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="9e228-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9e228-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9e228-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9e228-120">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="9e228-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9e228-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9e228-121">E_FAIL</span></span>|<span data-ttu-id="9e228-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="9e228-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9e228-123">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="9e228-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9e228-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9e228-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9e228-125">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="9e228-125">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="9e228-126">`CreateRWLockOwnerIterator`a été appelé sur un thread qui exécute actuellement du code managé.</span><span class="sxs-lookup"><span data-stu-id="9e228-126">`CreateRWLockOwnerIterator` was called on a thread that is currently running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e228-127">Notes</span><span class="sxs-lookup"><span data-stu-id="9e228-127">Remarks</span></span>  
 <span data-ttu-id="9e228-128">En général, les `CreateRWLockOwnerIterator`hôtes `DeleteRWLockOwnerIterator`appellent les `GetRWLockOwnerNext` méthodes, et Pendant la détection des verrous mortels.</span><span class="sxs-lookup"><span data-stu-id="9e228-128">Hosts typically call the `CreateRWLockOwnerIterator`, `DeleteRWLockOwnerIterator`, and `GetRWLockOwnerNext` methods during deadlock detection.</span></span> <span data-ttu-id="9e228-129">L’hôte est chargé de s’assurer que le verrou lecteur-writer est toujours valide, car le CLR n’effectue aucune tentative de maintien du verrou de lecture-écriture.</span><span class="sxs-lookup"><span data-stu-id="9e228-129">The host is responsible for ensuring that the reader-writer lock is still valid, because the CLR makes no attempt to keep the reader-writer lock alive.</span></span> <span data-ttu-id="9e228-130">Plusieurs stratégies sont disponibles pour l’hôte afin de garantir la validité du verrou:</span><span class="sxs-lookup"><span data-stu-id="9e228-130">Several strategies are available for the host to ensure the validity of the lock:</span></span>  
  
- <span data-ttu-id="9e228-131">L’hôte peut bloquer les appels de version sur le verrou lecteur-writer (par exemple, [IHostSemaphore:: ReleaseSemaphore,](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)) tout en veillant à ce que ce bloc ne provoque pas d’interblocage.</span><span class="sxs-lookup"><span data-stu-id="9e228-131">The host can block release calls on the reader-writer lock (for example, [IHostSemaphore::ReleaseSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)) while ensuring that this block does not cause deadlock.</span></span>  
  
- <span data-ttu-id="9e228-132">L’hôte peut empêcher la sortie d’attendre l’objet d’événement associé au verrou lecteur-writer, ce qui garantit que ce bloc ne provoque pas d’interblocage.</span><span class="sxs-lookup"><span data-stu-id="9e228-132">The host can block the exit from waiting on the event object associated with the reader-writer lock, again ensuring that this block does not cause deadlock.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9e228-133">`CreateRWLockOwnerIterator`doit être appelé uniquement sur les threads qui exécutent actuellement du code non managé.</span><span class="sxs-lookup"><span data-stu-id="9e228-133">`CreateRWLockOwnerIterator` must be called only on threads that are currently executing unmanaged code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e228-134">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9e228-134">Requirements</span></span>  
 <span data-ttu-id="9e228-135">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e228-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e228-136">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9e228-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9e228-137">**Bibliothèque** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9e228-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9e228-138">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e228-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e228-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9e228-139">See also</span></span>

- [<span data-ttu-id="9e228-140">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="9e228-140">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="9e228-141">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="9e228-141">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
