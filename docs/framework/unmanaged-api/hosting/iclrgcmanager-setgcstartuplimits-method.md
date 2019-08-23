---
title: ICLRGCManager::SetGCStartupLimits, méthode
ms.date: 03/30/2017
api_name:
- ICLRGCManager.SetGCStartupLimits
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager::SetGCStartupLimits
helpviewer_keywords:
- SetGCStartupLimits method, ICLRGCManager interface [.NET Framework hosting]
- ICLRGCManager::SetGCStartupLimits method [.NET Framework hosting]
ms.assetid: 1c8d9959-95b5-4131-be4a-556d97774014
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 29311f00f5ac4b61380b57cdd9fda07ec7de1b23
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966198"
---
# <a name="iclrgcmanagersetgcstartuplimits-method"></a><span data-ttu-id="d7534-102">ICLRGCManager::SetGCStartupLimits, méthode</span><span class="sxs-lookup"><span data-stu-id="d7534-102">ICLRGCManager::SetGCStartupLimits Method</span></span>
<span data-ttu-id="d7534-103">Définit la taille d’un segment de garbage collection et la taille maximale de la génération 0 du système garbage collection.</span><span class="sxs-lookup"><span data-stu-id="d7534-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d7534-104">À partir de la .NET Framework 4,5, vous pouvez définir la taille du segment et la taille maximale de la `DWORD` génération 0 sur des valeurs supérieures à à l’aide de la méthode [ICLRGCManager2:: setgcstartuplimitsex,](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d7534-104">Starting with the .NET Framework 4.5, you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7534-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d7534-105">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,   
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7534-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d7534-106">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="d7534-107">dans Taille spécifiée d’un segment de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="d7534-107">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="d7534-108">La taille minimale du segment est de 4 Mo.</span><span class="sxs-lookup"><span data-stu-id="d7534-108">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="d7534-109">Les segments peuvent être augmentés par incréments de 1 Mo ou plus.</span><span class="sxs-lookup"><span data-stu-id="d7534-109">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="d7534-110">dans Taille maximale spécifiée pour la génération 0.</span><span class="sxs-lookup"><span data-stu-id="d7534-110">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="d7534-111">La taille minimale de la génération 0 est de 64 Ko.</span><span class="sxs-lookup"><span data-stu-id="d7534-111">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d7534-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d7534-112">Return Value</span></span>  
  
|<span data-ttu-id="d7534-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d7534-113">HRESULT</span></span>|<span data-ttu-id="d7534-114">Description</span><span class="sxs-lookup"><span data-stu-id="d7534-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d7534-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="d7534-115">S_OK</span></span>|<span data-ttu-id="d7534-116">`SetGCStartupLimits`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="d7534-116">`SetGCStartupLimits` returned successfully.</span></span>|  
|<span data-ttu-id="d7534-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d7534-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d7534-118">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="d7534-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d7534-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d7534-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d7534-120">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="d7534-120">The call timed out.</span></span>|  
|<span data-ttu-id="d7534-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d7534-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d7534-122">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="d7534-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d7534-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d7534-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d7534-124">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="d7534-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d7534-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d7534-125">E_FAIL</span></span>|<span data-ttu-id="d7534-126">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="d7534-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d7534-127">Une fois qu’une méthode a retourné E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="d7534-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d7534-128">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d7534-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7534-129">Notes</span><span class="sxs-lookup"><span data-stu-id="d7534-129">Remarks</span></span>  
 <span data-ttu-id="d7534-130">Les valeurs définies `SetGCStartupLimits` par ne peuvent être spécifiées qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="d7534-130">The values that `SetGCStartupLimits` sets can be specified only once.</span></span> <span data-ttu-id="d7534-131">Les appels ultérieurs à `SetGCStartupLimits` sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="d7534-131">Later calls to `SetGCStartupLimits` are ignored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7534-132">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d7534-132">Requirements</span></span>  
 <span data-ttu-id="d7534-133">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7534-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7534-134">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d7534-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d7534-135">**Bibliothèque** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d7534-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d7534-136">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7534-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7534-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d7534-137">See also</span></span>

- [<span data-ttu-id="d7534-138">Gestion automatique de la mémoire</span><span class="sxs-lookup"><span data-stu-id="d7534-138">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="d7534-139">Nettoyage de la mémoire</span><span class="sxs-lookup"><span data-stu-id="d7534-139">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="d7534-140">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="d7534-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="d7534-141">ICLRGCManager, interface</span><span class="sxs-lookup"><span data-stu-id="d7534-141">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
