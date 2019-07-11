---
title: IHostSyncManager::CreateMonitorEvent, méthode
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateMonitorEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateMonitorEvent
helpviewer_keywords:
- CreateMonitorEvent method [.NET Framework hosting]
- IHostSyncManager::CreateMonitorEvent method [.NET Framework hosting]
ms.assetid: 524c7fd3-9b5c-46e7-99ba-555fd2fe33f0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3e5a66a87424c2ff8367aaf9ad4da27595880912
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753428"
---
# <a name="ihostsyncmanagercreatemonitorevent-method"></a><span data-ttu-id="db249-102">IHostSyncManager::CreateMonitorEvent, méthode</span><span class="sxs-lookup"><span data-stu-id="db249-102">IHostSyncManager::CreateMonitorEvent Method</span></span>
<span data-ttu-id="db249-103">Crée un objet d’événement d’auto-réinitialisation surveillé.</span><span class="sxs-lookup"><span data-stu-id="db249-103">Creates a monitored auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db249-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db249-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateMonitorEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db249-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="db249-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="db249-106">[in] Un cookie à associer à l’objet d’événement.</span><span class="sxs-lookup"><span data-stu-id="db249-106">[in] A cookie to associate with the event object.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="db249-107">[out] Un pointeur vers l’adresse d’un [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) d’instance, ou null si l’objet d’événement n’a pas pu être créé.</span><span class="sxs-lookup"><span data-stu-id="db249-107">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="db249-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="db249-108">Return Value</span></span>  
  
|<span data-ttu-id="db249-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="db249-109">HRESULT</span></span>|<span data-ttu-id="db249-110">Description</span><span class="sxs-lookup"><span data-stu-id="db249-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="db249-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="db249-111">S_OK</span></span>|<span data-ttu-id="db249-112">`CreateMonitorEvent` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="db249-112">`CreateMonitorEvent` returned successfully.</span></span>|  
|<span data-ttu-id="db249-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="db249-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="db249-114">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="db249-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="db249-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="db249-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="db249-116">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="db249-116">The call timed out.</span></span>|  
|<span data-ttu-id="db249-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="db249-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="db249-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="db249-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="db249-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="db249-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="db249-120">Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="db249-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="db249-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="db249-121">E_FAIL</span></span>|<span data-ttu-id="db249-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="db249-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="db249-123">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus.</span><span class="sxs-lookup"><span data-stu-id="db249-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="db249-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="db249-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="db249-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="db249-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="db249-126">Pas assez de mémoire n’était disponible pour créer l’objet événement demandé.</span><span class="sxs-lookup"><span data-stu-id="db249-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db249-127">Notes</span><span class="sxs-lookup"><span data-stu-id="db249-127">Remarks</span></span>  
 <span data-ttu-id="db249-128">`CreateMonitorEvent` Retourne un `IHostAutoEvent` que le CLR utilise dans son implémentation de managé <xref:System.Threading.Monitor?displayProperty=nameWithType> type.</span><span class="sxs-lookup"><span data-stu-id="db249-128">`CreateMonitorEvent` returns an `IHostAutoEvent` that the CLR uses in its implementation of the managed <xref:System.Threading.Monitor?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="db249-129">Cette méthode reflète Win32 `CreateEvent` (fonction), avec la valeur `false` spécifié pour le `bManualReset` paramètre.</span><span class="sxs-lookup"><span data-stu-id="db249-129">This method mirrors the Win32 `CreateEvent` function, with a value of `false` specified for the `bManualReset` parameter.</span></span>  
  
 <span data-ttu-id="db249-130">L’hôte peut utiliser le cookie pour déterminer quelle tâche attend le moniteur en appelant le [ICLRSyncManager::GetMonitorOwner](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="db249-130">The host can use the cookie to determine which task is waiting on the monitor by calling the [ICLRSyncManager::GetMonitorOwner](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db249-131">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="db249-131">Requirements</span></span>  
 <span data-ttu-id="db249-132">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db249-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db249-133">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="db249-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="db249-134">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="db249-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="db249-135">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db249-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db249-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="db249-136">See also</span></span>

- [<span data-ttu-id="db249-137">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="db249-137">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="db249-138">IHostAutoEvent, interface</span><span class="sxs-lookup"><span data-stu-id="db249-138">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="db249-139">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="db249-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- <xref:System.Threading.Monitor>
