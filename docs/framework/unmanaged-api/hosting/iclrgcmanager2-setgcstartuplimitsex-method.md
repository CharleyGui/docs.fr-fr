---
title: ICLRGCManager2::SetGCStartupLimitsEx, méthode
ms.date: 03/30/2017
api_name:
- ICLRGCManager2.SetGCStartupLimitsEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager2::SetCLRGCStartupLimitsEx
helpviewer_keywords:
- ICLRGCManager2::SetGCStartupLimitsEx method [.NET Framework hosting]
- SetGCStartupLimitsEx method, ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 6c3a08a9-5d65-48d4-8bbf-2a86ed7d356a
topic_type:
- apiref
ms.openlocfilehash: 9885149a71147db6eef13958b8ef825caa1d6ec6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176381"
---
# <a name="iclrgcmanager2setgcstartuplimitsex-method"></a><span data-ttu-id="e4d3d-102">ICLRGCManager2::SetGCStartupLimitsEx, méthode</span><span class="sxs-lookup"><span data-stu-id="e4d3d-102">ICLRGCManager2::SetGCStartupLimitsEx Method</span></span>
<span data-ttu-id="e4d3d-103">Définit la taille d’un segment de collecte des ordures et la taille maximale de la génération 0 du système de collecte des ordures.</span><span class="sxs-lookup"><span data-stu-id="e4d3d-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4d3d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4d3d-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,
    [in] SIZE_T MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4d3d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e4d3d-105">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="e4d3d-106">[dans] La taille spécifiée d’un segment de collecte des ordures.</span><span class="sxs-lookup"><span data-stu-id="e4d3d-106">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="e4d3d-107">La taille minimale du segment est de 4 Mo.</span><span class="sxs-lookup"><span data-stu-id="e4d3d-107">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="e4d3d-108">Les segments peuvent être augmentés par incréments de 1 Mo ou plus.</span><span class="sxs-lookup"><span data-stu-id="e4d3d-108">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="e4d3d-109">[dans] La taille maximale spécifiée pour la génération 0.</span><span class="sxs-lookup"><span data-stu-id="e4d3d-109">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="e4d3d-110">La taille minimale de la génération 0 est de 64 KB.</span><span class="sxs-lookup"><span data-stu-id="e4d3d-110">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e4d3d-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e4d3d-111">Return Value</span></span>  
  
|<span data-ttu-id="e4d3d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e4d3d-112">HRESULT</span></span>|<span data-ttu-id="e4d3d-113">Description</span><span class="sxs-lookup"><span data-stu-id="e4d3d-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e4d3d-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="e4d3d-114">S_OK</span></span>|<span data-ttu-id="e4d3d-115">`SetGCStartupLimitsEx`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="e4d3d-115">`SetGCStartupLimitsEx` returned successfully.</span></span>|  
|<span data-ttu-id="e4d3d-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e4d3d-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e4d3d-117">L’heure courante de l’exécution de la langue (CLR) n’a pas été chargée dans un processus, ou le CLR est dans un état où il ne peut pas exécuter le code géré ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="e4d3d-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e4d3d-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e4d3d-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e4d3d-119">L’appel s’est fait chronométrer.</span><span class="sxs-lookup"><span data-stu-id="e4d3d-119">The call timed out.</span></span>|  
|<span data-ttu-id="e4d3d-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e4d3d-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e4d3d-121">L’appelant n’est pas propriétaire de la serrure.</span><span class="sxs-lookup"><span data-stu-id="e4d3d-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e4d3d-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e4d3d-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e4d3d-123">Un événement a été annulé alors qu’un fil bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="e4d3d-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e4d3d-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e4d3d-124">E_FAIL</span></span>|<span data-ttu-id="e4d3d-125">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="e4d3d-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e4d3d-126">Une fois qu’une méthode revient E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="e4d3d-126">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e4d3d-127">Les appels ultérieurs aux méthodes d’hébergement reviennent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e4d3d-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4d3d-128">Notes </span><span class="sxs-lookup"><span data-stu-id="e4d3d-128">Remarks</span></span>  
 <span data-ttu-id="e4d3d-129">Les valeurs `SetGCStartupLimitsEx` qui se fixent ne peuvent être spécifiées qu’avant le démarrage de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="e4d3d-129">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="e4d3d-130">Les appels `SetGCStartupLimitsEx` ultérieurs sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="e4d3d-130">Later calls to `SetGCStartupLimitsEx` are ignored.</span></span>  
  
 <span data-ttu-id="e4d3d-131">Pour définir l’un ou l’autre paramètre sans affecter l’autre, spécifiez 0 (zéro) pour le paramètre que vous ne souhaitez pas modifier.</span><span class="sxs-lookup"><span data-stu-id="e4d3d-131">To set either parameter without affecting the other, specify 0 (zero) for the parameter you don't want to change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4d3d-132">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e4d3d-132">Requirements</span></span>  
 <span data-ttu-id="e4d3d-133">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4d3d-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4d3d-134">**En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor</span><span class="sxs-lookup"><span data-stu-id="e4d3d-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e4d3d-135">**Bibliothèque:** Inclus comme une ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e4d3d-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e4d3d-136">**.NET Versions-cadre:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4d3d-136">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4d3d-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e4d3d-137">See also</span></span>

- [<span data-ttu-id="e4d3d-138">Gestion automatique de la mémoire</span><span class="sxs-lookup"><span data-stu-id="e4d3d-138">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="e4d3d-139">Garbage collection</span><span class="sxs-lookup"><span data-stu-id="e4d3d-139">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="e4d3d-140">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="e4d3d-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="e4d3d-141">ICLRGCManager2, interface</span><span class="sxs-lookup"><span data-stu-id="e4d3d-141">ICLRGCManager2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)
