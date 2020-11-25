---
title: IHostTaskManager::SetUILocale, méthode
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetUILocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetUILocale
helpviewer_keywords:
- SetUILocale method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::SetUILocale method [.NET Framework hosting]
ms.assetid: d0c87a9c-ea81-4237-a16b-c22b36ec9dc8
topic_type:
- apiref
ms.openlocfilehash: bd1a1d7d2f7f945f345e8af802b881392d6d93e5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724219"
---
# <a name="ihosttaskmanagersetuilocale-method"></a><span data-ttu-id="91755-102">IHostTaskManager::SetUILocale, méthode</span><span class="sxs-lookup"><span data-stu-id="91755-102">IHostTaskManager::SetUILocale Method</span></span>

<span data-ttu-id="91755-103">Avertit l’hôte que le common language runtime (CLR) a modifié les paramètres régionaux de l’interface utilisateur (IU), ou culture, sur la tâche en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="91755-103">Notifies the host that the common language runtime (CLR) has changed the user interface (UI) locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91755-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="91755-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91755-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="91755-105">Parameters</span></span>  

 `lcid`  
 <span data-ttu-id="91755-106">dans Valeur de l’identificateur de paramètres régionaux qui correspond à la culture géographique et à la langue qui viennent d’être attribuées.</span><span class="sxs-lookup"><span data-stu-id="91755-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="91755-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="91755-107">Return Value</span></span>  
  
|<span data-ttu-id="91755-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="91755-108">HRESULT</span></span>|<span data-ttu-id="91755-109">Description</span><span class="sxs-lookup"><span data-stu-id="91755-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="91755-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="91755-110">S_OK</span></span>|<span data-ttu-id="91755-111">`SetUILocale` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="91755-111">`SetUILocale` returned successfully.</span></span>|  
|<span data-ttu-id="91755-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="91755-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="91755-113">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="91755-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="91755-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="91755-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="91755-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="91755-115">The call timed out.</span></span>|  
|<span data-ttu-id="91755-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="91755-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="91755-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="91755-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="91755-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="91755-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="91755-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="91755-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="91755-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="91755-120">E_FAIL</span></span>|<span data-ttu-id="91755-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="91755-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="91755-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="91755-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="91755-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="91755-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="91755-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="91755-124">E_NOTIMPL</span></span>|<span data-ttu-id="91755-125">L’hôte n’autorise pas le code utilisateur managé à modifier la culture de l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="91755-125">The host does not allow managed user code to change the UI culture.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91755-126">Remarques</span><span class="sxs-lookup"><span data-stu-id="91755-126">Remarks</span></span>  

 <span data-ttu-id="91755-127">Le runtime appelle `SetUILocale` lorsque la valeur de la <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> propriété est modifiée par le code managé.</span><span class="sxs-lookup"><span data-stu-id="91755-127">The runtime calls `SetUILocale` when the value of the <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> property is changed by managed code.</span></span> <span data-ttu-id="91755-128">Cette méthode permet à l’hôte d’exécuter tous les mécanismes qu’il peut avoir pour la synchronisation des paramètres régionaux.</span><span class="sxs-lookup"><span data-stu-id="91755-128">This method provides an opportunity for the host to execute any mechanisms it might have for synchronization of locales.</span></span> <span data-ttu-id="91755-129">Si un hôte n’autorise pas la modification des paramètres régionaux de l’interface utilisateur à partir du code managé, ou n’implémente pas de mécanisme pour synchroniser les paramètres régionaux, il doit retourner E_NOTIMPL à partir de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="91755-129">If a host does not allow the UI locale to be changed from managed code, or does not implement a mechanism to synchronize locales, it should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91755-130">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="91755-130">Requirements</span></span>  

 <span data-ttu-id="91755-131">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91755-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91755-132">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="91755-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="91755-133">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="91755-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="91755-134">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91755-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91755-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="91755-135">See also</span></span>

- [<span data-ttu-id="91755-136">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="91755-136">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="91755-137">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="91755-137">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="91755-138">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="91755-138">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="91755-139">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="91755-139">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="91755-140">SetLocale, méthode</span><span class="sxs-lookup"><span data-stu-id="91755-140">SetLocale Method</span></span>](ihosttaskmanager-setlocale-method.md)
