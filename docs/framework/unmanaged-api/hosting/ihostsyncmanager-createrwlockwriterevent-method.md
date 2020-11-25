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
ms.openlocfilehash: 5b5faf14337f78d9b176787528ae8947f5810ba6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704368"
---
# <a name="ihostsyncmanagercreaterwlockwriterevent-method"></a><span data-ttu-id="563a3-102">IHostSyncManager::CreateRWLockWriterEvent, méthode</span><span class="sxs-lookup"><span data-stu-id="563a3-102">IHostSyncManager::CreateRWLockWriterEvent Method</span></span>

<span data-ttu-id="563a3-103">Crée un objet d’événement à réinitialisation automatique pour l’implémentation d’un verrou de writer.</span><span class="sxs-lookup"><span data-stu-id="563a3-103">Creates an auto-reset event object for the implementation of a writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="563a3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="563a3-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateRWLockWriterEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="563a3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="563a3-105">Parameters</span></span>  

 `cookie`  
 <span data-ttu-id="563a3-106">dans Cookie à associer à l’événement de réinitialisation automatique.</span><span class="sxs-lookup"><span data-stu-id="563a3-106">[in] A cookie to associate with the auto-reset event.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="563a3-107">à Pointeur vers l’adresse d’une instance [IHostAutoEvent](ihostautoevent-interface.md) , ou null si l’objet d’événement n’a pas pu être créé.</span><span class="sxs-lookup"><span data-stu-id="563a3-107">[out] A pointer to the address of an [IHostAutoEvent](ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="563a3-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="563a3-108">Return Value</span></span>  
  
|<span data-ttu-id="563a3-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="563a3-109">HRESULT</span></span>|<span data-ttu-id="563a3-110">Description</span><span class="sxs-lookup"><span data-stu-id="563a3-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="563a3-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="563a3-111">S_OK</span></span>|<span data-ttu-id="563a3-112">`CreateRWLockWriterEvent` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="563a3-112">`CreateRWLockWriterEvent` returned successfully.</span></span>|  
|<span data-ttu-id="563a3-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="563a3-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="563a3-114">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="563a3-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="563a3-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="563a3-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="563a3-116">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="563a3-116">The call timed out.</span></span>|  
|<span data-ttu-id="563a3-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="563a3-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="563a3-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="563a3-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="563a3-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="563a3-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="563a3-120">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="563a3-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="563a3-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="563a3-121">E_FAIL</span></span>|<span data-ttu-id="563a3-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="563a3-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="563a3-123">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="563a3-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="563a3-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="563a3-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="563a3-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="563a3-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="563a3-126">Mémoire disponible insuffisante pour créer l’objet d’événement demandé.</span><span class="sxs-lookup"><span data-stu-id="563a3-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="563a3-127">Remarques</span><span class="sxs-lookup"><span data-stu-id="563a3-127">Remarks</span></span>  

 <span data-ttu-id="563a3-128">Le CLR appelle la `CreateRWLockWriterEvent` méthode pour obtenir une référence à une `IHostAutoEvent` instance à utiliser dans son implémentation d’un verrou de writer.</span><span class="sxs-lookup"><span data-stu-id="563a3-128">The CLR calls the `CreateRWLockWriterEvent` method to get a reference to an `IHostAutoEvent` instance to use in its implementation of a writer lock.</span></span> <span data-ttu-id="563a3-129">L’hôte peut utiliser le cookie spécifié pour déterminer quelles tâches attendent sur le verrou en appelant les méthodes d’itération de l’interface [ICLRSyncManager](iclrsyncmanager-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="563a3-129">The host can use the specified cookie to determine which tasks are waiting on the lock by calling the iteration methods of the [ICLRSyncManager](iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="563a3-130">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="563a3-130">Requirements</span></span>  

 <span data-ttu-id="563a3-131">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="563a3-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="563a3-132">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="563a3-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="563a3-133">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="563a3-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="563a3-134">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="563a3-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="563a3-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="563a3-135">See also</span></span>

- [<span data-ttu-id="563a3-136">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="563a3-136">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="563a3-137">IHostAutoEvent, interface</span><span class="sxs-lookup"><span data-stu-id="563a3-137">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="563a3-138">IHostManualEvent, interface</span><span class="sxs-lookup"><span data-stu-id="563a3-138">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="563a3-139">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="563a3-139">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
