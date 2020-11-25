---
title: ICLRTaskManager::SetUILocale, méthode
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.SetUILocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::SetUILocale
helpviewer_keywords:
- ICLRTaskManager::SetUILocale method [.NET Framework hosting]
- SetUILocale method, ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: 03adaa9a-2beb-49b3-b2c4-6b4fc3f10715
topic_type:
- apiref
ms.openlocfilehash: a426fca1b7ca4bfb9cbb30a221859f7c114db682
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732422"
---
# <a name="iclrtaskmanagersetuilocale-method"></a><span data-ttu-id="7459f-102">ICLRTaskManager::SetUILocale, méthode</span><span class="sxs-lookup"><span data-stu-id="7459f-102">ICLRTaskManager::SetUILocale Method</span></span>

<span data-ttu-id="7459f-103">Avertit le common language runtime (CLR) que l’hôte a modifié les paramètres régionaux de l’interface utilisateur (IU), ou culture, sur la tâche en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="7459f-103">Notifies the common language runtime (CLR) that the host has modified the user interface (UI) locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7459f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7459f-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7459f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7459f-105">Parameters</span></span>  

 `lcid`  
 <span data-ttu-id="7459f-106">dans Valeur de l’identificateur de paramètres régionaux qui correspond à la culture géographique et à la langue de l’interface utilisateur nouvellement assignées.</span><span class="sxs-lookup"><span data-stu-id="7459f-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language for the user interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7459f-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="7459f-107">Return Value</span></span>  
  
|<span data-ttu-id="7459f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7459f-108">HRESULT</span></span>|<span data-ttu-id="7459f-109">Description</span><span class="sxs-lookup"><span data-stu-id="7459f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7459f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7459f-110">S_OK</span></span>|<span data-ttu-id="7459f-111">`SetUILocale` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="7459f-111">`SetUILocale` returned successfully.</span></span>|  
|<span data-ttu-id="7459f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7459f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7459f-113">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="7459f-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7459f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7459f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7459f-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="7459f-115">The call timed out.</span></span>|  
|<span data-ttu-id="7459f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7459f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7459f-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="7459f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7459f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7459f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7459f-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="7459f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7459f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7459f-120">E_FAIL</span></span>|<span data-ttu-id="7459f-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="7459f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7459f-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="7459f-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7459f-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7459f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7459f-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="7459f-124">Remarks</span></span>  

 <span data-ttu-id="7459f-125">`SetUILocale` permet à l’hôte d’exécuter tout mécanisme qu’il peut avoir pour la synchronisation des paramètres régionaux.</span><span class="sxs-lookup"><span data-stu-id="7459f-125">`SetUILocale` provides an opportunity for the host to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7459f-126">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7459f-126">Requirements</span></span>  

 <span data-ttu-id="7459f-127">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7459f-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7459f-128">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7459f-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7459f-129">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7459f-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7459f-130">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7459f-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7459f-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7459f-131">See also</span></span>

- [<span data-ttu-id="7459f-132">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="7459f-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="7459f-133">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="7459f-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="7459f-134">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="7459f-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="7459f-135">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="7459f-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
