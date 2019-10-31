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
ms.openlocfilehash: f7426585045c7ae81377ec9bfca9d397d6f734cb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192020"
---
# <a name="ihostsyncmanagercreatemonitorevent-method"></a><span data-ttu-id="9d6f2-102">IHostSyncManager::CreateMonitorEvent, méthode</span><span class="sxs-lookup"><span data-stu-id="9d6f2-102">IHostSyncManager::CreateMonitorEvent Method</span></span>
<span data-ttu-id="9d6f2-103">Crée un objet d’événement de réinitialisation automatique surveillé.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-103">Creates a monitored auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d6f2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d6f2-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateMonitorEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d6f2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9d6f2-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="9d6f2-106">dans Cookie à associer à l’objet d’événement.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-106">[in] A cookie to associate with the event object.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="9d6f2-107">à Pointeur vers l’adresse d’une instance [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) , ou null si l’objet d’événement n’a pas pu être créé.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-107">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9d6f2-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="9d6f2-108">Return Value</span></span>  
  
|<span data-ttu-id="9d6f2-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9d6f2-109">HRESULT</span></span>|<span data-ttu-id="9d6f2-110">Description</span><span class="sxs-lookup"><span data-stu-id="9d6f2-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9d6f2-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="9d6f2-111">S_OK</span></span>|<span data-ttu-id="9d6f2-112">`CreateMonitorEvent` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-112">`CreateMonitorEvent` returned successfully.</span></span>|  
|<span data-ttu-id="9d6f2-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9d6f2-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9d6f2-114">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9d6f2-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9d6f2-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9d6f2-116">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-116">The call timed out.</span></span>|  
|<span data-ttu-id="9d6f2-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9d6f2-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9d6f2-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9d6f2-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9d6f2-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9d6f2-120">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9d6f2-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9d6f2-121">E_FAIL</span></span>|<span data-ttu-id="9d6f2-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9d6f2-123">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9d6f2-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9d6f2-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="9d6f2-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="9d6f2-126">Mémoire disponible insuffisante pour créer l’objet d’événement demandé.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d6f2-127">Notes</span><span class="sxs-lookup"><span data-stu-id="9d6f2-127">Remarks</span></span>  
 <span data-ttu-id="9d6f2-128">`CreateMonitorEvent` retourne un `IHostAutoEvent` que le CLR utilise dans son implémentation du type de <xref:System.Threading.Monitor?displayProperty=nameWithType> managé.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-128">`CreateMonitorEvent` returns an `IHostAutoEvent` that the CLR uses in its implementation of the managed <xref:System.Threading.Monitor?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="9d6f2-129">Cette méthode reflète la fonction Win32 `CreateEvent`, avec une valeur de `false` spécifiée pour le paramètre `bManualReset`.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-129">This method mirrors the Win32 `CreateEvent` function, with a value of `false` specified for the `bManualReset` parameter.</span></span>  
  
 <span data-ttu-id="9d6f2-130">L’hôte peut utiliser le cookie pour déterminer quelle tâche est en attente sur l’analyse en appelant la méthode [ICLRSyncManager :: GetMonitorOwner,](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md) .</span><span class="sxs-lookup"><span data-stu-id="9d6f2-130">The host can use the cookie to determine which task is waiting on the monitor by calling the [ICLRSyncManager::GetMonitorOwner](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d6f2-131">spécifications</span><span class="sxs-lookup"><span data-stu-id="9d6f2-131">Requirements</span></span>  
 <span data-ttu-id="9d6f2-132">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d6f2-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d6f2-133">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9d6f2-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9d6f2-134">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9d6f2-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9d6f2-135">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d6f2-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d6f2-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d6f2-136">See also</span></span>

- [<span data-ttu-id="9d6f2-137">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="9d6f2-137">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="9d6f2-138">IHostAutoEvent, interface</span><span class="sxs-lookup"><span data-stu-id="9d6f2-138">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="9d6f2-139">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="9d6f2-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- <xref:System.Threading.Monitor>
