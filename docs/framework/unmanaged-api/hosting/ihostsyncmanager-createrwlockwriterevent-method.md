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
ms.openlocfilehash: f00d166541f7955516e9d5c1dce2a4342c08ad0a
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803145"
---
# <a name="ihostsyncmanagercreaterwlockwriterevent-method"></a><span data-ttu-id="73cac-102">IHostSyncManager::CreateRWLockWriterEvent, méthode</span><span class="sxs-lookup"><span data-stu-id="73cac-102">IHostSyncManager::CreateRWLockWriterEvent Method</span></span>
<span data-ttu-id="73cac-103">Crée un objet d’événement à réinitialisation automatique pour l’implémentation d’un verrou de writer.</span><span class="sxs-lookup"><span data-stu-id="73cac-103">Creates an auto-reset event object for the implementation of a writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73cac-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73cac-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateRWLockWriterEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73cac-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="73cac-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="73cac-106">dans Cookie à associer à l’événement de réinitialisation automatique.</span><span class="sxs-lookup"><span data-stu-id="73cac-106">[in] A cookie to associate with the auto-reset event.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="73cac-107">à Pointeur vers l’adresse d’une instance [IHostAutoEvent](ihostautoevent-interface.md) , ou null si l’objet d’événement n’a pas pu être créé.</span><span class="sxs-lookup"><span data-stu-id="73cac-107">[out] A pointer to the address of an [IHostAutoEvent](ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="73cac-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="73cac-108">Return Value</span></span>  
  
|<span data-ttu-id="73cac-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="73cac-109">HRESULT</span></span>|<span data-ttu-id="73cac-110">Description</span><span class="sxs-lookup"><span data-stu-id="73cac-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="73cac-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="73cac-111">S_OK</span></span>|<span data-ttu-id="73cac-112">`CreateRWLockWriterEvent`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="73cac-112">`CreateRWLockWriterEvent` returned successfully.</span></span>|  
|<span data-ttu-id="73cac-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="73cac-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="73cac-114">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="73cac-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="73cac-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="73cac-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="73cac-116">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="73cac-116">The call timed out.</span></span>|  
|<span data-ttu-id="73cac-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="73cac-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="73cac-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="73cac-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="73cac-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="73cac-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="73cac-120">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="73cac-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="73cac-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="73cac-121">E_FAIL</span></span>|<span data-ttu-id="73cac-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="73cac-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="73cac-123">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="73cac-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="73cac-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="73cac-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="73cac-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="73cac-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="73cac-126">Mémoire disponible insuffisante pour créer l’objet d’événement demandé.</span><span class="sxs-lookup"><span data-stu-id="73cac-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73cac-127">Notes</span><span class="sxs-lookup"><span data-stu-id="73cac-127">Remarks</span></span>  
 <span data-ttu-id="73cac-128">Le CLR appelle la `CreateRWLockWriterEvent` méthode pour obtenir une référence à une `IHostAutoEvent` instance à utiliser dans son implémentation d’un verrou de writer.</span><span class="sxs-lookup"><span data-stu-id="73cac-128">The CLR calls the `CreateRWLockWriterEvent` method to get a reference to an `IHostAutoEvent` instance to use in its implementation of a writer lock.</span></span> <span data-ttu-id="73cac-129">L’hôte peut utiliser le cookie spécifié pour déterminer quelles tâches attendent sur le verrou en appelant les méthodes d’itération de l’interface [ICLRSyncManager](iclrsyncmanager-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="73cac-129">The host can use the specified cookie to determine which tasks are waiting on the lock by calling the iteration methods of the [ICLRSyncManager](iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73cac-130">Spécifications</span><span class="sxs-lookup"><span data-stu-id="73cac-130">Requirements</span></span>  
 <span data-ttu-id="73cac-131">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73cac-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73cac-132">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="73cac-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="73cac-133">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="73cac-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="73cac-134">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73cac-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73cac-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="73cac-135">See also</span></span>

- [<span data-ttu-id="73cac-136">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="73cac-136">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="73cac-137">IHostAutoEvent, interface</span><span class="sxs-lookup"><span data-stu-id="73cac-137">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="73cac-138">IHostManualEvent, interface</span><span class="sxs-lookup"><span data-stu-id="73cac-138">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="73cac-139">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="73cac-139">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
