---
title: IHostSyncManager::CreateManualEvent, méthode
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateManualEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateManualEvent
helpviewer_keywords:
- CreateManualEvent method [.NET Framework hosting]
- IHostSyncManager::CreateManualEvent method [.NET Framework hosting]
ms.assetid: 68661fbd-09cf-46dc-890b-e694f8a3880a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1cfb57ba6f07437abfc8576ca4d5ff9cd0131d8b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753436"
---
# <a name="ihostsyncmanagercreatemanualevent-method"></a><span data-ttu-id="c8f4f-102">IHostSyncManager::CreateManualEvent, méthode</span><span class="sxs-lookup"><span data-stu-id="c8f4f-102">IHostSyncManager::CreateManualEvent Method</span></span>
<span data-ttu-id="c8f4f-103">Crée un objet d’événement de réinitialisation manuelle.</span><span class="sxs-lookup"><span data-stu-id="c8f4f-103">Creates a manual-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8f4f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c8f4f-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateManualEvent (  
    [in]  BOOL bInitialState,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8f4f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c8f4f-105">Parameters</span></span>  
 `bInitialState`  
 <span data-ttu-id="c8f4f-106">[in] `true`, si l’objet est signalé ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="c8f4f-106">[in] `true`, if the object is signaled; otherwise, `false`.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="c8f4f-107">[out] Un pointeur vers l’adresse d’un [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) d’instance, ou null si l’événement n’a pas pu être créé.</span><span class="sxs-lookup"><span data-stu-id="c8f4f-107">[out] A pointer to the address of an [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance, or null if the event could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c8f4f-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c8f4f-108">Return Value</span></span>  
  
|<span data-ttu-id="c8f4f-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c8f4f-109">HRESULT</span></span>|<span data-ttu-id="c8f4f-110">Description</span><span class="sxs-lookup"><span data-stu-id="c8f4f-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c8f4f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c8f4f-111">S_OK</span></span>|<span data-ttu-id="c8f4f-112">`CreateManualEvent` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="c8f4f-112">`CreateManualEvent` returned successfully.</span></span>|  
|<span data-ttu-id="c8f4f-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c8f4f-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c8f4f-114">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="c8f4f-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c8f4f-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c8f4f-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c8f4f-116">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="c8f4f-116">The call timed out.</span></span>|  
|<span data-ttu-id="c8f4f-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c8f4f-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c8f4f-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="c8f4f-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c8f4f-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c8f4f-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c8f4f-120">Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="c8f4f-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c8f4f-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c8f4f-121">E_FAIL</span></span>|<span data-ttu-id="c8f4f-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="c8f4f-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c8f4f-123">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus.</span><span class="sxs-lookup"><span data-stu-id="c8f4f-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c8f4f-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c8f4f-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c8f4f-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="c8f4f-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="c8f4f-126">Pas assez de mémoire n’était disponible pour créer l’objet événement demandé.</span><span class="sxs-lookup"><span data-stu-id="c8f4f-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c8f4f-127">Notes</span><span class="sxs-lookup"><span data-stu-id="c8f4f-127">Remarks</span></span>  
 <span data-ttu-id="c8f4f-128">`CreateManualEvent` Crée un `IHostManualEvent`, un objet d’événement de réinitialisation manuelle qui nécessite un appel à la [IHostManualEvent::Reset](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md) méthode pour définir un état non signalé.</span><span class="sxs-lookup"><span data-stu-id="c8f4f-128">`CreateManualEvent` creates an `IHostManualEvent`, a manual-reset event object that requires a call to the [IHostManualEvent::Reset](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md) method to set it to a non-signaled state.</span></span> <span data-ttu-id="c8f4f-129">`CreateManualEvent` reflète Win32 `CreateEvent` fonction avec la valeur `true` spécifié pour le `bManualReset` paramètre.</span><span class="sxs-lookup"><span data-stu-id="c8f4f-129">`CreateManualEvent` mirrors the Win32 `CreateEvent` function with a value of `true` specified for the `bManualReset` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8f4f-130">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c8f4f-130">Requirements</span></span>  
 <span data-ttu-id="c8f4f-131">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8f4f-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8f4f-132">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c8f4f-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c8f4f-133">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c8f4f-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c8f4f-134">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8f4f-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8f4f-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c8f4f-135">See also</span></span>

- [<span data-ttu-id="c8f4f-136">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="c8f4f-136">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="c8f4f-137">IHostManualEvent, interface</span><span class="sxs-lookup"><span data-stu-id="c8f4f-137">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="c8f4f-138">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="c8f4f-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
