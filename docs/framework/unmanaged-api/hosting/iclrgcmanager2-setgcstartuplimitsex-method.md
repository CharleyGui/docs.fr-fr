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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 356678afb537ab5e5e1653c4f71140ce704e55ef
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779687"
---
# <a name="iclrgcmanager2setgcstartuplimitsex-method"></a><span data-ttu-id="0c78e-102">ICLRGCManager2::SetGCStartupLimitsEx, méthode</span><span class="sxs-lookup"><span data-stu-id="0c78e-102">ICLRGCManager2::SetGCStartupLimitsEx Method</span></span>
<span data-ttu-id="0c78e-103">Définit la taille d’un segment de garbage collection et la taille maximale de la génération du système de nettoyage 0.</span><span class="sxs-lookup"><span data-stu-id="0c78e-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c78e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0c78e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,   
    [in] SIZE_T MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c78e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0c78e-105">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="0c78e-106">[in] La taille spécifiée d’un segment de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="0c78e-106">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="0c78e-107">La taille de segment minimale est de 4 Mo.</span><span class="sxs-lookup"><span data-stu-id="0c78e-107">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="0c78e-108">Segments peuvent être accrue en incréments de 1 Mo ou plus.</span><span class="sxs-lookup"><span data-stu-id="0c78e-108">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="0c78e-109">[in] La taille maximale spécifiée pour la génération 0.</span><span class="sxs-lookup"><span data-stu-id="0c78e-109">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="0c78e-110">La taille minimum de la génération 0 est de 64 Ko.</span><span class="sxs-lookup"><span data-stu-id="0c78e-110">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0c78e-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="0c78e-111">Return Value</span></span>  
  
|<span data-ttu-id="0c78e-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0c78e-112">HRESULT</span></span>|<span data-ttu-id="0c78e-113">Description</span><span class="sxs-lookup"><span data-stu-id="0c78e-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0c78e-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="0c78e-114">S_OK</span></span>|<span data-ttu-id="0c78e-115">`SetGCStartupLimitsEx` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="0c78e-115">`SetGCStartupLimitsEx` returned successfully.</span></span>|  
|<span data-ttu-id="0c78e-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0c78e-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0c78e-117">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="0c78e-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0c78e-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0c78e-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0c78e-119">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="0c78e-119">The call timed out.</span></span>|  
|<span data-ttu-id="0c78e-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0c78e-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0c78e-121">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="0c78e-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0c78e-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0c78e-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0c78e-123">Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="0c78e-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0c78e-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0c78e-124">E_FAIL</span></span>|<span data-ttu-id="0c78e-125">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="0c78e-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0c78e-126">Une fois une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus.</span><span class="sxs-lookup"><span data-stu-id="0c78e-126">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0c78e-127">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0c78e-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c78e-128">Notes</span><span class="sxs-lookup"><span data-stu-id="0c78e-128">Remarks</span></span>  
 <span data-ttu-id="0c78e-129">Les valeurs qui `SetGCStartupLimitsEx` jeux peuvent être spécifiés uniquement avant le démarrage de l’ordinateur hôte.</span><span class="sxs-lookup"><span data-stu-id="0c78e-129">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="0c78e-130">Appels ultérieurs à `SetGCStartupLimitsEx` sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="0c78e-130">Later calls to `SetGCStartupLimitsEx` are ignored.</span></span>  
  
 <span data-ttu-id="0c78e-131">Pour définir un paramètre sans affecter l’autre, spécifiez 0 (zéro) pour le paramètre que vous ne souhaitez pas modifier.</span><span class="sxs-lookup"><span data-stu-id="0c78e-131">To set either parameter without affecting the other, specify 0 (zero) for the parameter you don't want to change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c78e-132">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0c78e-132">Requirements</span></span>  
 <span data-ttu-id="0c78e-133">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c78e-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c78e-134">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0c78e-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0c78e-135">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0c78e-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0c78e-136">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c78e-136">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c78e-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0c78e-137">See also</span></span>

- [<span data-ttu-id="0c78e-138">Gestion automatique de la mémoire</span><span class="sxs-lookup"><span data-stu-id="0c78e-138">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)
- [<span data-ttu-id="0c78e-139">Nettoyage de la mémoire</span><span class="sxs-lookup"><span data-stu-id="0c78e-139">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)
- [<span data-ttu-id="0c78e-140">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="0c78e-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="0c78e-141">ICLRGCManager2, interface</span><span class="sxs-lookup"><span data-stu-id="0c78e-141">ICLRGCManager2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)
