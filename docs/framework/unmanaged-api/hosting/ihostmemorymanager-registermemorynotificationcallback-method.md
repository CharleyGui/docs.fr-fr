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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 48580f5ac71b906c302ee7ce1b98e7d4334f2482
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767737"
---
# <a name="ihostmemorymanagerregistermemorynotificationcallback-method"></a><span data-ttu-id="8ccb5-102">IHostMemoryManager::RegisterMemoryNotificationCallback, méthode</span><span class="sxs-lookup"><span data-stu-id="8ccb5-102">IHostMemoryManager::RegisterMemoryNotificationCallback Method</span></span>
<span data-ttu-id="8ccb5-103">Enregistre un pointeur vers une fonction de rappel que l’hôte appelle pour avertir le common language runtime (CLR) de la charge actuelle de la mémoire sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8ccb5-103">Registers a pointer to a callback function that the host invokes to notify the common language runtime (CLR) of the current memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ccb5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ccb5-104">Syntax</span></span>  
  
```cpp  
HRESULT RegisterMemoryNotificationCallback (  
    [in] ICLRMemoryNotificationCallback* pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ccb5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8ccb5-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="8ccb5-106">[in] Un pointeur d’interface vers un [ICLRMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md) instance qui est implémentée par le CLR.</span><span class="sxs-lookup"><span data-stu-id="8ccb5-106">[in] An interface pointer to an [ICLRMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md) instance that is implemented by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8ccb5-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="8ccb5-107">Return Value</span></span>  
  
|<span data-ttu-id="8ccb5-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8ccb5-108">HRESULT</span></span>|<span data-ttu-id="8ccb5-109">Description</span><span class="sxs-lookup"><span data-stu-id="8ccb5-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8ccb5-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="8ccb5-110">S_OK</span></span>|<span data-ttu-id="8ccb5-111">`RegisterMemoryNotificationCallback` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="8ccb5-111">`RegisterMemoryNotificationCallback` returned successfully.</span></span>|  
|<span data-ttu-id="8ccb5-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8ccb5-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8ccb5-113">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="8ccb5-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8ccb5-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8ccb5-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8ccb5-115">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="8ccb5-115">The call timed out.</span></span>|  
|<span data-ttu-id="8ccb5-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8ccb5-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8ccb5-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="8ccb5-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8ccb5-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8ccb5-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8ccb5-119">Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="8ccb5-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8ccb5-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8ccb5-120">E_FAIL</span></span>|<span data-ttu-id="8ccb5-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="8ccb5-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8ccb5-122">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus.</span><span class="sxs-lookup"><span data-stu-id="8ccb5-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8ccb5-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8ccb5-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ccb5-124">Notes</span><span class="sxs-lookup"><span data-stu-id="8ccb5-124">Remarks</span></span>  
 <span data-ttu-id="8ccb5-125">Étant donné que le `ICLRMemoryNotificationCallback` interface ne définit qu’une seule méthode ([ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)) et parce que `pCallback` est un pointeur vers un `ICLRMemoryNotificationCallback` instance fournie par le CLR, le l’inscription est efficace pour la fonction de rappel elle-même.</span><span class="sxs-lookup"><span data-stu-id="8ccb5-125">Because the `ICLRMemoryNotificationCallback` interface defines only one method ([ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)), and because `pCallback` is a pointer to an `ICLRMemoryNotificationCallback` instance provided by the CLR, the registration is effectively for the callback function itself.</span></span> <span data-ttu-id="8ccb5-126">L’hôte appelle `OnMemoryNotification` à signaler des conditions de sollicitation de la mémoire, plutôt qu’à l’aide de Win32 standard `CreateMemoryResourceNotification` (fonction).</span><span class="sxs-lookup"><span data-stu-id="8ccb5-126">The host invokes `OnMemoryNotification` to report memory pressure conditions, rather than using the standard Win32 `CreateMemoryResourceNotification` function.</span></span> <span data-ttu-id="8ccb5-127">Pour plus d’informations, consultez la documentation de la plateforme de Windows.</span><span class="sxs-lookup"><span data-stu-id="8ccb5-127">For more information, see the Windows Platform documentation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ccb5-128">Les appels à `OnMemoryNotification` ne jamais se bloquer.</span><span class="sxs-lookup"><span data-stu-id="8ccb5-128">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="8ccb5-129">Elles retournent toujours immédiatement.</span><span class="sxs-lookup"><span data-stu-id="8ccb5-129">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ccb5-130">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8ccb5-130">Requirements</span></span>  
 <span data-ttu-id="8ccb5-131">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ccb5-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ccb5-132">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8ccb5-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8ccb5-133">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8ccb5-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8ccb5-134">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ccb5-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ccb5-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ccb5-135">See also</span></span>

- [<span data-ttu-id="8ccb5-136">ICLRMemoryNotificationCallback, interface</span><span class="sxs-lookup"><span data-stu-id="8ccb5-136">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
- [<span data-ttu-id="8ccb5-137">IHostMemoryManager, interface</span><span class="sxs-lookup"><span data-stu-id="8ccb5-137">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
