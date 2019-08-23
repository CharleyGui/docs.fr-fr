---
title: ICLRMemoryNotificationCallback::OnMemoryNotification, méthode
ms.date: 03/30/2017
api_name:
- ICLRMemoryNotificationCallback.OnMemoryNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMemoryNotificationCallback::OnMemoryNotification
helpviewer_keywords:
- ICLRMemoryNotificationCallback::OnMemoryNotification method [.NET Framework hosting]
- OnMemoryNotification method [.NET Framework hosting]
ms.assetid: 5612a44d-56cc-4f34-af31-8c9809ba9431
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 899d0cf6a0475846b749bd0b7cbda41b1b88253d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949703"
---
# <a name="iclrmemorynotificationcallbackonmemorynotification-method"></a><span data-ttu-id="83382-102">ICLRMemoryNotificationCallback::OnMemoryNotification, méthode</span><span class="sxs-lookup"><span data-stu-id="83382-102">ICLRMemoryNotificationCallback::OnMemoryNotification Method</span></span>
<span data-ttu-id="83382-103">Notifie le common language runtime (CLR) de la charge de mémoire sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="83382-103">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83382-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83382-104">Syntax</span></span>  
  
```cpp  
HRESULT OnMemoryNotification (  
    [in] EMemoryAvailable eMemoryAvailable  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83382-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="83382-105">Parameters</span></span>  
 `eMemoryAvailable`  
 <span data-ttu-id="83382-106">dans L’une des valeurs [EMemoryAvailable,](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md) , indiquant la sollicitation de la mémoire que l’ordinateur rencontre actuellement.</span><span class="sxs-lookup"><span data-stu-id="83382-106">[in] One of the [EMemoryAvailable](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md) values, indicating the memory pressure the computer is currently experiencing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="83382-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="83382-107">Return Value</span></span>  
  
|<span data-ttu-id="83382-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="83382-108">HRESULT</span></span>|<span data-ttu-id="83382-109">Description</span><span class="sxs-lookup"><span data-stu-id="83382-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="83382-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="83382-110">S_OK</span></span>|<span data-ttu-id="83382-111">`OnMemoryNotification`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="83382-111">`OnMemoryNotification` returned successfully.</span></span>|  
|<span data-ttu-id="83382-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="83382-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="83382-113">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="83382-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="83382-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="83382-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="83382-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="83382-115">The call timed out.</span></span>|  
|<span data-ttu-id="83382-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="83382-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="83382-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="83382-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="83382-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="83382-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="83382-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="83382-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="83382-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="83382-120">E_FAIL</span></span>|<span data-ttu-id="83382-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="83382-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="83382-122">Une fois qu’une méthode a retourné E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="83382-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="83382-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="83382-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83382-124">Notes</span><span class="sxs-lookup"><span data-stu-id="83382-124">Remarks</span></span>  
 <span data-ttu-id="83382-125">Le CLR inscrit un rappel à `OnMemoryNotification` en utilisant un appel à la méthode [IHostMemoryManager:: RegisterMemoryNotificationCallback,](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md) .</span><span class="sxs-lookup"><span data-stu-id="83382-125">The CLR registers a callback to `OnMemoryNotification` by using a call to the [IHostMemoryManager::RegisterMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md) method.</span></span> <span data-ttu-id="83382-126">Le runtime utilise les informations retournées dans le rappel pour libérer de la mémoire supplémentaire lorsque l’hôte signale que les ressources mémoire sont insuffisantes.</span><span class="sxs-lookup"><span data-stu-id="83382-126">The runtime uses the information returned in the callback to free additional memory when the host reports that memory resources are running low.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="83382-127">Appels à `OnMemoryNotification` ne jamais bloquer.</span><span class="sxs-lookup"><span data-stu-id="83382-127">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="83382-128">Ils retournent toujours immédiatement.</span><span class="sxs-lookup"><span data-stu-id="83382-128">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83382-129">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="83382-129">Requirements</span></span>  
 <span data-ttu-id="83382-130">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83382-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83382-131">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="83382-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="83382-132">**Bibliothèque** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="83382-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="83382-133">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83382-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83382-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="83382-134">See also</span></span>

- [<span data-ttu-id="83382-135">IHostMemoryManager, interface</span><span class="sxs-lookup"><span data-stu-id="83382-135">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="83382-136">RegisterMemoryNotificationCallback, méthode</span><span class="sxs-lookup"><span data-stu-id="83382-136">RegisterMemoryNotificationCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)
- [<span data-ttu-id="83382-137">ICLRMemoryNotificationCallback, interface</span><span class="sxs-lookup"><span data-stu-id="83382-137">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
