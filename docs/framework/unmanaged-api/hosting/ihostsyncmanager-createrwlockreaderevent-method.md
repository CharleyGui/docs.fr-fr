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
ms.openlocfilehash: 7c9bf2186d3dc4500694225ea4023df3609b9010
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704381"
---
# <a name="ihostsyncmanagercreaterwlockreaderevent-method"></a><span data-ttu-id="b1a6d-102">IHostSyncManager::CreateRWLockReaderEvent, méthode</span><span class="sxs-lookup"><span data-stu-id="b1a6d-102">IHostSyncManager::CreateRWLockReaderEvent Method</span></span>

<span data-ttu-id="b1a6d-103">Crée un objet d’événement de réinitialisation manuelle pour l’implémentation d’un verrou de lecteur.</span><span class="sxs-lookup"><span data-stu-id="b1a6d-103">Creates a manual-reset event object for the implementation of a reader lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1a6d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1a6d-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateRWLockReaderEvent (  
    [in]  BOOL bInitialState,  
    [in]  SIZE_T cookie,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1a6d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b1a6d-105">Parameters</span></span>  

 `bInitialState`  
 <span data-ttu-id="b1a6d-106">[in] `true` , si `ppEvent` doit être signalé ; sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="b1a6d-106">[in] `true`, if `ppEvent` should be signaled; otherwise, `false`.</span></span>  
  
 `cookie`  
 <span data-ttu-id="b1a6d-107">dans Cookie à associer au verrou de lecteur.</span><span class="sxs-lookup"><span data-stu-id="b1a6d-107">[in] A cookie to associate with the reader lock.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="b1a6d-108">à Pointeur vers l’adresse d’une instance [IHostManualEvent](ihostmanualevent-interface.md) , ou null si l’objet d’événement n’a pas pu être créé.</span><span class="sxs-lookup"><span data-stu-id="b1a6d-108">[out] A pointer to the address of an [IHostManualEvent](ihostmanualevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b1a6d-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="b1a6d-109">Return Value</span></span>  
  
|<span data-ttu-id="b1a6d-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b1a6d-110">HRESULT</span></span>|<span data-ttu-id="b1a6d-111">Description</span><span class="sxs-lookup"><span data-stu-id="b1a6d-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b1a6d-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="b1a6d-112">S_OK</span></span>|<span data-ttu-id="b1a6d-113">`CreateRWLockReaderEvent` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="b1a6d-113">`CreateRWLockReaderEvent` returned successfully.</span></span>|  
|<span data-ttu-id="b1a6d-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b1a6d-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b1a6d-115">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="b1a6d-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b1a6d-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b1a6d-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b1a6d-117">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="b1a6d-117">The call timed out.</span></span>|  
|<span data-ttu-id="b1a6d-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b1a6d-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b1a6d-119">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="b1a6d-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b1a6d-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b1a6d-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b1a6d-121">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="b1a6d-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b1a6d-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b1a6d-122">E_FAIL</span></span>|<span data-ttu-id="b1a6d-123">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="b1a6d-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b1a6d-124">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="b1a6d-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b1a6d-125">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b1a6d-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b1a6d-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="b1a6d-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="b1a6d-127">Mémoire disponible insuffisante pour créer l’objet d’événement demandé.</span><span class="sxs-lookup"><span data-stu-id="b1a6d-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1a6d-128">Remarques</span><span class="sxs-lookup"><span data-stu-id="b1a6d-128">Remarks</span></span>  

 <span data-ttu-id="b1a6d-129">Le CLR appelle `CreateRWLockReaderEvent` pour obtenir une référence à une `IHostManualEvent` instance à utiliser dans son implémentation d’un verrou de lecteur.</span><span class="sxs-lookup"><span data-stu-id="b1a6d-129">The CLR calls `CreateRWLockReaderEvent` to get a reference to an `IHostManualEvent` instance to use in its implementation of a reader lock.</span></span> <span data-ttu-id="b1a6d-130">L’hôte peut utiliser le cookie pour déterminer quelles tâches attendent le verrou du lecteur en interrogeant l’interface [ICLRSyncManager](iclrsyncmanager-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="b1a6d-130">The host can use the cookie to determine which tasks are waiting on the reader lock by querying the [ICLRSyncManager](iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1a6d-131">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b1a6d-131">Requirements</span></span>  

 <span data-ttu-id="b1a6d-132">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1a6d-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1a6d-133">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b1a6d-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b1a6d-134">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b1a6d-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b1a6d-135">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1a6d-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1a6d-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b1a6d-136">See also</span></span>

- [<span data-ttu-id="b1a6d-137">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="b1a6d-137">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="b1a6d-138">IHostAutoEvent, interface</span><span class="sxs-lookup"><span data-stu-id="b1a6d-138">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="b1a6d-139">IHostManualEvent, interface</span><span class="sxs-lookup"><span data-stu-id="b1a6d-139">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="b1a6d-140">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="b1a6d-140">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
