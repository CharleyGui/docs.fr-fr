---
title: IHostSyncManager::CreateRWLockReaderEvent, méthode
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateRWLockReaderEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateRWLockReaderEvent
helpviewer_keywords:
- CreateRWLockReaderEvent method [.NET Framework hosting]
- IHostSyncManager::CreateRWLockReaderEvent method [.NET Framework hosting]
ms.assetid: 68c4ea19-c47c-45c6-b420-d3a2ba1c2d50
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3e4095e0af13149a852ca055aa6a5e1e2d6848a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753414"
---
# <a name="ihostsyncmanagercreaterwlockreaderevent-method"></a><span data-ttu-id="f0ed8-102">IHostSyncManager::CreateRWLockReaderEvent, méthode</span><span class="sxs-lookup"><span data-stu-id="f0ed8-102">IHostSyncManager::CreateRWLockReaderEvent Method</span></span>
<span data-ttu-id="f0ed8-103">Crée un objet d’événement de réinitialisation manuelle pour l’implémentation d’un verrou de lecteur.</span><span class="sxs-lookup"><span data-stu-id="f0ed8-103">Creates a manual-reset event object for the implementation of a reader lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0ed8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f0ed8-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateRWLockReaderEvent (  
    [in]  BOOL bInitialState,  
    [in]  SIZE_T cookie,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0ed8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f0ed8-105">Parameters</span></span>  
 `bInitialState`  
 <span data-ttu-id="f0ed8-106">[in] `true`si `ppEvent` doit être signalé ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="f0ed8-106">[in] `true`, if `ppEvent` should be signaled; otherwise, `false`.</span></span>  
  
 `cookie`  
 <span data-ttu-id="f0ed8-107">[in] Cookie à associer avec le verrou de lecteur.</span><span class="sxs-lookup"><span data-stu-id="f0ed8-107">[in] A cookie to associate with the reader lock.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="f0ed8-108">[out] Un pointeur vers l’adresse d’un [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) d’instance, ou null si l’objet d’événement n’a pas pu être créé.</span><span class="sxs-lookup"><span data-stu-id="f0ed8-108">[out] A pointer to the address of an [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f0ed8-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f0ed8-109">Return Value</span></span>  
  
|<span data-ttu-id="f0ed8-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f0ed8-110">HRESULT</span></span>|<span data-ttu-id="f0ed8-111">Description</span><span class="sxs-lookup"><span data-stu-id="f0ed8-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f0ed8-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="f0ed8-112">S_OK</span></span>|<span data-ttu-id="f0ed8-113">`CreateRWLockReaderEvent` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="f0ed8-113">`CreateRWLockReaderEvent` returned successfully.</span></span>|  
|<span data-ttu-id="f0ed8-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f0ed8-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f0ed8-115">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="f0ed8-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f0ed8-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f0ed8-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f0ed8-117">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="f0ed8-117">The call timed out.</span></span>|  
|<span data-ttu-id="f0ed8-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f0ed8-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f0ed8-119">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="f0ed8-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f0ed8-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f0ed8-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f0ed8-121">Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="f0ed8-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f0ed8-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f0ed8-122">E_FAIL</span></span>|<span data-ttu-id="f0ed8-123">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="f0ed8-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f0ed8-124">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus.</span><span class="sxs-lookup"><span data-stu-id="f0ed8-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f0ed8-125">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f0ed8-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f0ed8-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="f0ed8-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="f0ed8-127">Pas assez de mémoire n’était disponible pour créer l’objet événement demandé.</span><span class="sxs-lookup"><span data-stu-id="f0ed8-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0ed8-128">Notes</span><span class="sxs-lookup"><span data-stu-id="f0ed8-128">Remarks</span></span>  
 <span data-ttu-id="f0ed8-129">Le CLR appelle `CreateRWLockReaderEvent` pour obtenir une référence à un `IHostManualEvent` instance à utiliser dans son implémentation d’un verrou de lecteur.</span><span class="sxs-lookup"><span data-stu-id="f0ed8-129">The CLR calls `CreateRWLockReaderEvent` to get a reference to an `IHostManualEvent` instance to use in its implementation of a reader lock.</span></span> <span data-ttu-id="f0ed8-130">L’hôte peut utiliser le cookie pour déterminer quelles tâches attendent le verrou de lecteur en interrogeant le [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="f0ed8-130">The host can use the cookie to determine which tasks are waiting on the reader lock by querying the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0ed8-131">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f0ed8-131">Requirements</span></span>  
 <span data-ttu-id="f0ed8-132">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0ed8-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0ed8-133">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f0ed8-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f0ed8-134">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f0ed8-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f0ed8-135">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0ed8-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0ed8-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f0ed8-136">See also</span></span>

- [<span data-ttu-id="f0ed8-137">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="f0ed8-137">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="f0ed8-138">IHostAutoEvent, interface</span><span class="sxs-lookup"><span data-stu-id="f0ed8-138">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="f0ed8-139">IHostManualEvent, interface</span><span class="sxs-lookup"><span data-stu-id="f0ed8-139">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="f0ed8-140">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="f0ed8-140">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
