---
title: IHostSemaphore::ReleaseSemaphore, méthode
ms.date: 03/30/2017
api_name:
- IHostSemaphore.ReleaseSemaphore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSemaphore::ReleaseSemaphore
helpviewer_keywords:
- ReleaseSemaphore method [.NET Framework hosting]
- IHostSemaphore::ReleaseSemaphore method [.NET Framework hosting]
ms.assetid: a343d197-979a-4ac6-ab8c-cb8a05f3120e
topic_type:
- apiref
ms.openlocfilehash: aa67aabbe8a7a47a9b3036f508e2f8bb6082c3e0
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803559"
---
# <a name="ihostsemaphorereleasesemaphore-method"></a><span data-ttu-id="a50d7-102">IHostSemaphore::ReleaseSemaphore, méthode</span><span class="sxs-lookup"><span data-stu-id="a50d7-102">IHostSemaphore::ReleaseSemaphore Method</span></span>
<span data-ttu-id="a50d7-103">Augmente le nombre de l’instance [IHostSemaphore](ihostsemaphore-interface.md) actuelle de la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="a50d7-103">Increases the count of the current [IHostSemaphore](ihostsemaphore-interface.md) instance by the specified amount.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a50d7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a50d7-104">Syntax</span></span>  
  
```cpp  
HRESULT ReleaseSemaphore (  
    [in]  LONG  lReleaseCount,  
    [out] LONG  *lpPreviousCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a50d7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a50d7-105">Parameters</span></span>  
 `lReleaseCount`  
 <span data-ttu-id="a50d7-106">dans Valeur d’augmentation du nombre de l' `IHostSemaphore` instance actuelle.</span><span class="sxs-lookup"><span data-stu-id="a50d7-106">[in] The amount by which to increase the count of the current `IHostSemaphore` instance.</span></span> <span data-ttu-id="a50d7-107">Cette valeur doit être supérieure à zéro.</span><span class="sxs-lookup"><span data-stu-id="a50d7-107">This amount must be greater than zero.</span></span>  
  
 `lpPreviousCount`  
 <span data-ttu-id="a50d7-108">à Pointeur vers le nombre précédent, ou null si l’appelant n’a pas besoin du nombre précédent.</span><span class="sxs-lookup"><span data-stu-id="a50d7-108">[out] A pointer to the previous count, or null if the caller does not require the previous count.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a50d7-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="a50d7-109">Return Value</span></span>  
  
|<span data-ttu-id="a50d7-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a50d7-110">HRESULT</span></span>|<span data-ttu-id="a50d7-111">Description</span><span class="sxs-lookup"><span data-stu-id="a50d7-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a50d7-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="a50d7-112">S_OK</span></span>|<span data-ttu-id="a50d7-113">`ReleaseSemaphore`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="a50d7-113">`ReleaseSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="a50d7-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a50d7-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a50d7-115">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="a50d7-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a50d7-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a50d7-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a50d7-117">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="a50d7-117">The call timed out.</span></span>|  
|<span data-ttu-id="a50d7-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a50d7-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a50d7-119">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="a50d7-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a50d7-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a50d7-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a50d7-121">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="a50d7-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a50d7-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a50d7-122">E_FAIL</span></span>|<span data-ttu-id="a50d7-123">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="a50d7-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a50d7-124">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="a50d7-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a50d7-125">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a50d7-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a50d7-126">Notes</span><span class="sxs-lookup"><span data-stu-id="a50d7-126">Remarks</span></span>  
 <span data-ttu-id="a50d7-127">Le CLR appelle généralement `ReleaseSemaphore` pour notifier l’hôte qu’il a fini d’utiliser une ressource, en passant la valeur 1 pour le `lReleaseCount` paramètre.</span><span class="sxs-lookup"><span data-stu-id="a50d7-127">The CLR typically calls `ReleaseSemaphore` to notify the host that it has finished using a resource, passing a value of 1 for the `lReleaseCount` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a50d7-128">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a50d7-128">Requirements</span></span>  
 <span data-ttu-id="a50d7-129">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a50d7-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a50d7-130">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a50d7-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a50d7-131">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a50d7-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a50d7-132">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a50d7-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a50d7-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a50d7-133">See also</span></span>

- [<span data-ttu-id="a50d7-134">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="a50d7-134">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="a50d7-135">IHostAutoEvent, interface</span><span class="sxs-lookup"><span data-stu-id="a50d7-135">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="a50d7-136">IHostManualEvent, interface</span><span class="sxs-lookup"><span data-stu-id="a50d7-136">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="a50d7-137">IHostSemaphore, interface</span><span class="sxs-lookup"><span data-stu-id="a50d7-137">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="a50d7-138">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="a50d7-138">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
