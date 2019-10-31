---
title: IHostTaskManager::SetLocale, méthode
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetLocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetLocale
helpviewer_keywords:
- SetLocale method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::SetLocale method [.NET Framework hosting]
ms.assetid: 747ee407-ee8c-484d-9583-25089236d2d1
topic_type:
- apiref
ms.openlocfilehash: e560d08d3e10db1b5978d1bd7be53dfed9ca3268
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132981"
---
# <a name="ihosttaskmanagersetlocale-method"></a><span data-ttu-id="f8188-102">IHostTaskManager::SetLocale, méthode</span><span class="sxs-lookup"><span data-stu-id="f8188-102">IHostTaskManager::SetLocale Method</span></span>
<span data-ttu-id="f8188-103">Avertit l’hôte que le common language runtime (CLR) a modifié les paramètres régionaux, ou la culture, sur la tâche en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="f8188-103">Notifies the host that the common language runtime (CLR) has changed the locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8188-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8188-104">Syntax</span></span>  
  
```cpp  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f8188-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f8188-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="f8188-106">dans Valeur de l’identificateur de paramètres régionaux qui correspond à la culture géographique et à la langue qui viennent d’être attribuées.</span><span class="sxs-lookup"><span data-stu-id="f8188-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f8188-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f8188-107">Return Value</span></span>  
  
|<span data-ttu-id="f8188-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f8188-108">HRESULT</span></span>|<span data-ttu-id="f8188-109">Description</span><span class="sxs-lookup"><span data-stu-id="f8188-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f8188-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f8188-110">S_OK</span></span>|<span data-ttu-id="f8188-111">`SetLocale` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="f8188-111">`SetLocale` returned successfully.</span></span>|  
|<span data-ttu-id="f8188-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f8188-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f8188-113">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="f8188-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f8188-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f8188-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f8188-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="f8188-115">The call timed out.</span></span>|  
|<span data-ttu-id="f8188-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f8188-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f8188-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="f8188-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f8188-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f8188-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f8188-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="f8188-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f8188-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f8188-120">E_FAIL</span></span>|<span data-ttu-id="f8188-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="f8188-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f8188-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="f8188-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f8188-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f8188-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f8188-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="f8188-124">E_NOTIMPL</span></span>|<span data-ttu-id="f8188-125">L’hôte n’autorise pas le code utilisateur managé à modifier les paramètres régionaux.</span><span class="sxs-lookup"><span data-stu-id="f8188-125">The host does not allow managed user code to modify the locale.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8188-126">Notes</span><span class="sxs-lookup"><span data-stu-id="f8188-126">Remarks</span></span>  
 <span data-ttu-id="f8188-127">Le runtime appelle `SetLocale` lorsque la valeur de la propriété <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> est modifiée par le code managé.</span><span class="sxs-lookup"><span data-stu-id="f8188-127">The runtime calls `SetLocale` when the value of the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property is changed by managed code.</span></span> <span data-ttu-id="f8188-128">Cette méthode permet à l’hôte d’exécuter tous les mécanismes qu’il peut avoir pour la synchronisation des paramètres régionaux.</span><span class="sxs-lookup"><span data-stu-id="f8188-128">This method provides an opportunity for the host to execute any mechanisms it might have for synchronization of locales.</span></span> <span data-ttu-id="f8188-129">Si un hôte n’autorise pas la modification des paramètres régionaux à partir du code managé, ou n’implémente pas de mécanisme pour synchroniser des paramètres régionaux, il doit retourner E_NOTIMPL à partir de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="f8188-129">If a host does not allow the locale to be changed from managed code, or does not implement a mechanism to synchronize locales, it should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8188-130">spécifications</span><span class="sxs-lookup"><span data-stu-id="f8188-130">Requirements</span></span>  
 <span data-ttu-id="f8188-131">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8188-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8188-132">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f8188-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f8188-133">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f8188-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f8188-134">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8188-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8188-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8188-135">See also</span></span>

- [<span data-ttu-id="f8188-136">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="f8188-136">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="f8188-137">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="f8188-137">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="f8188-138">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="f8188-138">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="f8188-139">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="f8188-139">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="f8188-140">SetUILocale, méthode</span><span class="sxs-lookup"><span data-stu-id="f8188-140">SetUILocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setuilocale-method.md)
