---
title: ICLRTaskManager::SetLocale, méthode
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.SetLocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::SetLocale
helpviewer_keywords:
- SetLocale method, ICLRTaskManager interface [.NET Framework hosting]
- ICLRTaskManager::SetLocale method [.NET Framework hosting]
ms.assetid: ed16bb7f-4206-43a8-b9e9-c5737b69e3af
topic_type:
- apiref
ms.openlocfilehash: 5f799c140705a5279c996b6bec90ab1f29bd42ef
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732432"
---
# <a name="iclrtaskmanagersetlocale-method"></a><span data-ttu-id="df33d-102">ICLRTaskManager::SetLocale, méthode</span><span class="sxs-lookup"><span data-stu-id="df33d-102">ICLRTaskManager::SetLocale Method</span></span>

<span data-ttu-id="df33d-103">Avertit le common language runtime (CLR) que l’hôte a modifié la valeur de l’identificateur de paramètres régionaux (qui correspond à la culture géographique et à la langue) sur la tâche en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="df33d-103">Notifies the common language runtime (CLR) that the host has modified the value of the locale identifier (which maps to the geographical culture and language) on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df33d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="df33d-104">Syntax</span></span>  
  
```cpp  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="df33d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="df33d-105">Parameters</span></span>  

 `lcid`  
 <span data-ttu-id="df33d-106">dans Valeur de l’identificateur de paramètres régionaux qui correspond à la culture géographique et à la langue qui viennent d’être attribuées.</span><span class="sxs-lookup"><span data-stu-id="df33d-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="df33d-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="df33d-107">Return Value</span></span>  
  
|<span data-ttu-id="df33d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="df33d-108">HRESULT</span></span>|<span data-ttu-id="df33d-109">Description</span><span class="sxs-lookup"><span data-stu-id="df33d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="df33d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="df33d-110">S_OK</span></span>|<span data-ttu-id="df33d-111">Retour réussi de la méthode.</span><span class="sxs-lookup"><span data-stu-id="df33d-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="df33d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="df33d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="df33d-113">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="df33d-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="df33d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="df33d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="df33d-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="df33d-115">The call timed out.</span></span>|  
|<span data-ttu-id="df33d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="df33d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="df33d-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="df33d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="df33d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="df33d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="df33d-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="df33d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="df33d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="df33d-120">E_FAIL</span></span>|<span data-ttu-id="df33d-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="df33d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="df33d-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="df33d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="df33d-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="df33d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df33d-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="df33d-124">Remarks</span></span>  

 <span data-ttu-id="df33d-125">`SetLocale` donne à l’hôte la possibilité d’exécuter tous les mécanismes dont il peut disposer pour la synchronisation des paramètres régionaux.</span><span class="sxs-lookup"><span data-stu-id="df33d-125">`SetLocale` gives the host an opportunity to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df33d-126">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="df33d-126">Requirements</span></span>  

 <span data-ttu-id="df33d-127">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df33d-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df33d-128">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="df33d-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="df33d-129">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="df33d-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="df33d-130">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df33d-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df33d-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="df33d-131">See also</span></span>

- [<span data-ttu-id="df33d-132">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="df33d-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="df33d-133">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="df33d-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="df33d-134">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="df33d-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="df33d-135">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="df33d-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
