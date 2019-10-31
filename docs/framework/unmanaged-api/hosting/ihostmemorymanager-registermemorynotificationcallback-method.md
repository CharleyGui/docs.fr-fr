---
title: IHostMemoryManager::RegisterMemoryNotificationCallback, méthode
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.RegisterMemoryNotificationCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::RegisterMemoryNotificationCallback
helpviewer_keywords:
- IHostMemoryManager::RegisterMemoryNotificationCallback method [.NET Framework hosting]
- RegisterMemoryNotificationCallback method [.NET Framework hosting]
ms.assetid: 65d301f6-4dbb-4b5f-8eff-82540e2b6465
topic_type:
- apiref
ms.openlocfilehash: 4400fab27ed82e540230ce4196844285e8e37d16
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128633"
---
# <a name="ihostmemorymanagerregistermemorynotificationcallback-method"></a><span data-ttu-id="84c54-102">IHostMemoryManager::RegisterMemoryNotificationCallback, méthode</span><span class="sxs-lookup"><span data-stu-id="84c54-102">IHostMemoryManager::RegisterMemoryNotificationCallback Method</span></span>
<span data-ttu-id="84c54-103">Inscrit un pointeur vers une fonction de rappel que l’hôte appelle pour notifier le common language runtime (CLR) de la charge de mémoire actuelle sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="84c54-103">Registers a pointer to a callback function that the host invokes to notify the common language runtime (CLR) of the current memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84c54-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="84c54-104">Syntax</span></span>  
  
```cpp  
HRESULT RegisterMemoryNotificationCallback (  
    [in] ICLRMemoryNotificationCallback* pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84c54-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="84c54-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="84c54-106">dans Pointeur d’interface vers une instance [ICLRMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md) qui est implémentée par le CLR.</span><span class="sxs-lookup"><span data-stu-id="84c54-106">[in] An interface pointer to an [ICLRMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md) instance that is implemented by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="84c54-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="84c54-107">Return Value</span></span>  
  
|<span data-ttu-id="84c54-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="84c54-108">HRESULT</span></span>|<span data-ttu-id="84c54-109">Description</span><span class="sxs-lookup"><span data-stu-id="84c54-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="84c54-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="84c54-110">S_OK</span></span>|<span data-ttu-id="84c54-111">`RegisterMemoryNotificationCallback` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="84c54-111">`RegisterMemoryNotificationCallback` returned successfully.</span></span>|  
|<span data-ttu-id="84c54-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="84c54-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="84c54-113">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="84c54-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="84c54-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="84c54-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="84c54-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="84c54-115">The call timed out.</span></span>|  
|<span data-ttu-id="84c54-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="84c54-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="84c54-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="84c54-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="84c54-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="84c54-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="84c54-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="84c54-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="84c54-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="84c54-120">E_FAIL</span></span>|<span data-ttu-id="84c54-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="84c54-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="84c54-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="84c54-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="84c54-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="84c54-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84c54-124">Notes</span><span class="sxs-lookup"><span data-stu-id="84c54-124">Remarks</span></span>  
 <span data-ttu-id="84c54-125">Étant donné que l’interface `ICLRMemoryNotificationCallback` définit une seule méthode ([ICLRMemoryNotificationCallback :: OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)) et que `pCallback` est un pointeur vers une instance `ICLRMemoryNotificationCallback` fournie par le CLR, l’inscription est efficace pour le rappel. fonction elle-même.</span><span class="sxs-lookup"><span data-stu-id="84c54-125">Because the `ICLRMemoryNotificationCallback` interface defines only one method ([ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)), and because `pCallback` is a pointer to an `ICLRMemoryNotificationCallback` instance provided by the CLR, the registration is effectively for the callback function itself.</span></span> <span data-ttu-id="84c54-126">L’hôte appelle `OnMemoryNotification` pour signaler les conditions de sollicitation de la mémoire, au lieu d’utiliser la fonction de `CreateMemoryResourceNotification` Win32 standard.</span><span class="sxs-lookup"><span data-stu-id="84c54-126">The host invokes `OnMemoryNotification` to report memory pressure conditions, rather than using the standard Win32 `CreateMemoryResourceNotification` function.</span></span> <span data-ttu-id="84c54-127">Pour plus d’informations, consultez la documentation de la plateforme Windows.</span><span class="sxs-lookup"><span data-stu-id="84c54-127">For more information, see the Windows Platform documentation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="84c54-128">Les appels à `OnMemoryNotification` jamais bloqués.</span><span class="sxs-lookup"><span data-stu-id="84c54-128">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="84c54-129">Ils retournent toujours immédiatement.</span><span class="sxs-lookup"><span data-stu-id="84c54-129">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84c54-130">spécifications</span><span class="sxs-lookup"><span data-stu-id="84c54-130">Requirements</span></span>  
 <span data-ttu-id="84c54-131">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84c54-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84c54-132">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="84c54-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="84c54-133">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="84c54-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="84c54-134">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84c54-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84c54-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="84c54-135">See also</span></span>

- [<span data-ttu-id="84c54-136">ICLRMemoryNotificationCallback, interface</span><span class="sxs-lookup"><span data-stu-id="84c54-136">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
- [<span data-ttu-id="84c54-137">IHostMemoryManager, interface</span><span class="sxs-lookup"><span data-stu-id="84c54-137">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
