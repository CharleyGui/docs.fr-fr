---
title: IHostSyncManager::CreateRWLockWriterEvent, méthode
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateRWLockWriterEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateRWLockWriterEvent
helpviewer_keywords:
- CreateRWLockWriterEvent method [.NET Framework hosting]
- IHostSyncManager::CreateRWLockWriterEvent method [.NET Framework hosting]
ms.assetid: 70e488c2-cf53-4dc0-ba52-74372d215c41
topic_type:
- apiref
ms.openlocfilehash: 13eb23c530a4fe1b491f41cc65cc94dacc9d34f4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192011"
---
# <a name="ihostsyncmanagercreaterwlockwriterevent-method"></a><span data-ttu-id="f9fd3-102">IHostSyncManager::CreateRWLockWriterEvent, méthode</span><span class="sxs-lookup"><span data-stu-id="f9fd3-102">IHostSyncManager::CreateRWLockWriterEvent Method</span></span>
<span data-ttu-id="f9fd3-103">Crée un objet d’événement à réinitialisation automatique pour l’implémentation d’un verrou de writer.</span><span class="sxs-lookup"><span data-stu-id="f9fd3-103">Creates an auto-reset event object for the implementation of a writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9fd3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f9fd3-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateRWLockWriterEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9fd3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f9fd3-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="f9fd3-106">dans Cookie à associer à l’événement de réinitialisation automatique.</span><span class="sxs-lookup"><span data-stu-id="f9fd3-106">[in] A cookie to associate with the auto-reset event.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="f9fd3-107">à Pointeur vers l’adresse d’une instance [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) , ou null si l’objet d’événement n’a pas pu être créé.</span><span class="sxs-lookup"><span data-stu-id="f9fd3-107">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f9fd3-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f9fd3-108">Return Value</span></span>  
  
|<span data-ttu-id="f9fd3-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f9fd3-109">HRESULT</span></span>|<span data-ttu-id="f9fd3-110">Description</span><span class="sxs-lookup"><span data-stu-id="f9fd3-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f9fd3-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f9fd3-111">S_OK</span></span>|<span data-ttu-id="f9fd3-112">`CreateRWLockWriterEvent` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="f9fd3-112">`CreateRWLockWriterEvent` returned successfully.</span></span>|  
|<span data-ttu-id="f9fd3-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f9fd3-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f9fd3-114">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="f9fd3-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f9fd3-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f9fd3-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f9fd3-116">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="f9fd3-116">The call timed out.</span></span>|  
|<span data-ttu-id="f9fd3-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f9fd3-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f9fd3-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="f9fd3-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f9fd3-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f9fd3-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f9fd3-120">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="f9fd3-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f9fd3-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f9fd3-121">E_FAIL</span></span>|<span data-ttu-id="f9fd3-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="f9fd3-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f9fd3-123">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="f9fd3-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f9fd3-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f9fd3-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f9fd3-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="f9fd3-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="f9fd3-126">Mémoire disponible insuffisante pour créer l’objet d’événement demandé.</span><span class="sxs-lookup"><span data-stu-id="f9fd3-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9fd3-127">Notes</span><span class="sxs-lookup"><span data-stu-id="f9fd3-127">Remarks</span></span>  
 <span data-ttu-id="f9fd3-128">Le CLR appelle la méthode `CreateRWLockWriterEvent` pour obtenir une référence à une instance `IHostAutoEvent` à utiliser dans son implémentation d’un verrou de writer.</span><span class="sxs-lookup"><span data-stu-id="f9fd3-128">The CLR calls the `CreateRWLockWriterEvent` method to get a reference to an `IHostAutoEvent` instance to use in its implementation of a writer lock.</span></span> <span data-ttu-id="f9fd3-129">L’hôte peut utiliser le cookie spécifié pour déterminer quelles tâches attendent sur le verrou en appelant les méthodes d’itération de l’interface [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="f9fd3-129">The host can use the specified cookie to determine which tasks are waiting on the lock by calling the iteration methods of the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9fd3-130">spécifications</span><span class="sxs-lookup"><span data-stu-id="f9fd3-130">Requirements</span></span>  
 <span data-ttu-id="f9fd3-131">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9fd3-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9fd3-132">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f9fd3-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f9fd3-133">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f9fd3-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f9fd3-134">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9fd3-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9fd3-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f9fd3-135">See also</span></span>

- [<span data-ttu-id="f9fd3-136">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="f9fd3-136">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="f9fd3-137">IHostAutoEvent, interface</span><span class="sxs-lookup"><span data-stu-id="f9fd3-137">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="f9fd3-138">IHostManualEvent, interface</span><span class="sxs-lookup"><span data-stu-id="f9fd3-138">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="f9fd3-139">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="f9fd3-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
