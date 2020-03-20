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
ms.openlocfilehash: 645b64c8b536029663c350bdcde9a716a715aab3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178081"
---
# <a name="iclrgcmanagersetgcstartuplimits-method"></a><span data-ttu-id="143ca-102">ICLRGCManager::SetGCStartupLimits, méthode</span><span class="sxs-lookup"><span data-stu-id="143ca-102">ICLRGCManager::SetGCStartupLimits Method</span></span>
<span data-ttu-id="143ca-103">Définit la taille d’un segment de collecte des ordures et la taille maximale de la génération 0 du système de collecte des ordures.</span><span class="sxs-lookup"><span data-stu-id="143ca-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="143ca-104">En commençant par le cadre .NET 4.5, vous pouvez définir la `DWORD` taille du segment et la taille maximale de génération 0 à des valeurs supérieures à en utilisant la méthode [ICLRGCManager2::SetGCStartupLimitsEx.](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)</span><span class="sxs-lookup"><span data-stu-id="143ca-104">Starting with the .NET Framework 4.5, you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="143ca-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="143ca-105">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="143ca-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="143ca-106">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="143ca-107">[dans] La taille spécifiée d’un segment de collecte des ordures.</span><span class="sxs-lookup"><span data-stu-id="143ca-107">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="143ca-108">La taille minimale du segment est de 4 Mo.</span><span class="sxs-lookup"><span data-stu-id="143ca-108">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="143ca-109">Les segments peuvent être augmentés par incréments de 1 Mo ou plus.</span><span class="sxs-lookup"><span data-stu-id="143ca-109">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="143ca-110">[dans] La taille maximale spécifiée pour la génération 0.</span><span class="sxs-lookup"><span data-stu-id="143ca-110">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="143ca-111">La taille minimale de la génération 0 est de 64 KB.</span><span class="sxs-lookup"><span data-stu-id="143ca-111">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="143ca-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="143ca-112">Return Value</span></span>  
  
|<span data-ttu-id="143ca-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="143ca-113">HRESULT</span></span>|<span data-ttu-id="143ca-114">Description</span><span class="sxs-lookup"><span data-stu-id="143ca-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="143ca-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="143ca-115">S_OK</span></span>|<span data-ttu-id="143ca-116">`SetGCStartupLimits`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="143ca-116">`SetGCStartupLimits` returned successfully.</span></span>|  
|<span data-ttu-id="143ca-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="143ca-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="143ca-118">L’heure courante de l’exécution de la langue (CLR) n’a pas été chargée dans un processus, ou le CLR est dans un état où il ne peut pas exécuter le code géré ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="143ca-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="143ca-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="143ca-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="143ca-120">L’appel s’est fait chronométrer.</span><span class="sxs-lookup"><span data-stu-id="143ca-120">The call timed out.</span></span>|  
|<span data-ttu-id="143ca-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="143ca-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="143ca-122">L’appelant n’est pas propriétaire de la serrure.</span><span class="sxs-lookup"><span data-stu-id="143ca-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="143ca-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="143ca-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="143ca-124">Un événement a été annulé alors qu’un fil bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="143ca-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="143ca-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="143ca-125">E_FAIL</span></span>|<span data-ttu-id="143ca-126">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="143ca-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="143ca-127">Une fois qu’une méthode revient E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="143ca-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="143ca-128">Les appels ultérieurs aux méthodes d’hébergement reviennent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="143ca-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="143ca-129">Notes </span><span class="sxs-lookup"><span data-stu-id="143ca-129">Remarks</span></span>  
 <span data-ttu-id="143ca-130">Les valeurs `SetGCStartupLimits` qui se fixent ne peuvent être spécifiées qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="143ca-130">The values that `SetGCStartupLimits` sets can be specified only once.</span></span> <span data-ttu-id="143ca-131">Les appels `SetGCStartupLimits` ultérieurs sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="143ca-131">Later calls to `SetGCStartupLimits` are ignored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="143ca-132">Spécifications</span><span class="sxs-lookup"><span data-stu-id="143ca-132">Requirements</span></span>  
 <span data-ttu-id="143ca-133">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="143ca-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="143ca-134">**En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor</span><span class="sxs-lookup"><span data-stu-id="143ca-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="143ca-135">**Bibliothèque:** Inclus comme une ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="143ca-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="143ca-136">**.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="143ca-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="143ca-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="143ca-137">See also</span></span>

- [<span data-ttu-id="143ca-138">Gestion automatique de la mémoire</span><span class="sxs-lookup"><span data-stu-id="143ca-138">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="143ca-139">Garbage collection</span><span class="sxs-lookup"><span data-stu-id="143ca-139">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="143ca-140">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="143ca-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="143ca-141">ICLRGCManager, interface</span><span class="sxs-lookup"><span data-stu-id="143ca-141">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
