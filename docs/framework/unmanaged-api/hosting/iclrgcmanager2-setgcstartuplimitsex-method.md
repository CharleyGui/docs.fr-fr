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
ms.openlocfilehash: 77de550cd3fb614e03f8028707c3cbf914734910
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141088"
---
# <a name="iclrgcmanager2setgcstartuplimitsex-method"></a><span data-ttu-id="fdaec-102">ICLRGCManager2::SetGCStartupLimitsEx, méthode</span><span class="sxs-lookup"><span data-stu-id="fdaec-102">ICLRGCManager2::SetGCStartupLimitsEx Method</span></span>
<span data-ttu-id="fdaec-103">Définit la taille d’un segment de garbage collection et la taille maximale de la génération 0 du système garbage collection.</span><span class="sxs-lookup"><span data-stu-id="fdaec-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdaec-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fdaec-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,   
    [in] SIZE_T MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fdaec-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fdaec-105">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="fdaec-106">dans Taille spécifiée d’un segment de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="fdaec-106">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="fdaec-107">La taille minimale du segment est de 4 Mo.</span><span class="sxs-lookup"><span data-stu-id="fdaec-107">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="fdaec-108">Les segments peuvent être augmentés par incréments de 1 Mo ou plus.</span><span class="sxs-lookup"><span data-stu-id="fdaec-108">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="fdaec-109">dans Taille maximale spécifiée pour la génération 0.</span><span class="sxs-lookup"><span data-stu-id="fdaec-109">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="fdaec-110">La taille minimale de la génération 0 est de 64 Ko.</span><span class="sxs-lookup"><span data-stu-id="fdaec-110">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fdaec-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="fdaec-111">Return Value</span></span>  
  
|<span data-ttu-id="fdaec-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fdaec-112">HRESULT</span></span>|<span data-ttu-id="fdaec-113">Description</span><span class="sxs-lookup"><span data-stu-id="fdaec-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fdaec-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="fdaec-114">S_OK</span></span>|<span data-ttu-id="fdaec-115">`SetGCStartupLimitsEx` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="fdaec-115">`SetGCStartupLimitsEx` returned successfully.</span></span>|  
|<span data-ttu-id="fdaec-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fdaec-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fdaec-117">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="fdaec-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fdaec-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fdaec-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fdaec-119">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="fdaec-119">The call timed out.</span></span>|  
|<span data-ttu-id="fdaec-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fdaec-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fdaec-121">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="fdaec-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fdaec-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fdaec-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fdaec-123">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="fdaec-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fdaec-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fdaec-124">E_FAIL</span></span>|<span data-ttu-id="fdaec-125">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="fdaec-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fdaec-126">Une fois qu’une méthode a retourné E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="fdaec-126">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fdaec-127">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fdaec-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fdaec-128">Notes</span><span class="sxs-lookup"><span data-stu-id="fdaec-128">Remarks</span></span>  
 <span data-ttu-id="fdaec-129">Les valeurs que `SetGCStartupLimitsEx` définit peuvent être spécifiées uniquement avant le démarrage de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="fdaec-129">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="fdaec-130">Les appels ultérieurs à `SetGCStartupLimitsEx` sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="fdaec-130">Later calls to `SetGCStartupLimitsEx` are ignored.</span></span>  
  
 <span data-ttu-id="fdaec-131">Pour définir l’un ou l’autre paramètre sans affecter l’autre, spécifiez 0 (zéro) pour le paramètre que vous ne souhaitez pas modifier.</span><span class="sxs-lookup"><span data-stu-id="fdaec-131">To set either parameter without affecting the other, specify 0 (zero) for the parameter you don't want to change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fdaec-132">spécifications</span><span class="sxs-lookup"><span data-stu-id="fdaec-132">Requirements</span></span>  
 <span data-ttu-id="fdaec-133">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fdaec-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fdaec-134">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fdaec-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fdaec-135">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="fdaec-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fdaec-136">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fdaec-136">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdaec-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fdaec-137">See also</span></span>

- [<span data-ttu-id="fdaec-138">Gestion automatique de la mémoire</span><span class="sxs-lookup"><span data-stu-id="fdaec-138">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="fdaec-139">Nettoyage de la mémoire</span><span class="sxs-lookup"><span data-stu-id="fdaec-139">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="fdaec-140">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="fdaec-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="fdaec-141">ICLRGCManager2, interface</span><span class="sxs-lookup"><span data-stu-id="fdaec-141">ICLRGCManager2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)
