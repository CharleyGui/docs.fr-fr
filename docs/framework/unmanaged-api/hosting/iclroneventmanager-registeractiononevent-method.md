---
title: ICLROnEventManager::RegisterActionOnEvent, méthode
ms.date: 03/30/2017
api_name:
- ICLROnEventManager.RegisterActionOnEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLROnEventManager::RegisterActionOnEvent
helpviewer_keywords:
- ICLROnEventManager::RegisterActionOnEvent method [.NET Framework hosting]
- RegisterActionOnEvent method [.NET Framework hosting]
ms.assetid: b944cf49-918d-4c4e-993b-77d097a52550
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36d4b0692b112a66fea3dd878c7054a083fb68ff
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951145"
---
# <a name="iclroneventmanagerregisteractiononevent-method"></a><span data-ttu-id="ceca1-102">ICLROnEventManager::RegisterActionOnEvent, méthode</span><span class="sxs-lookup"><span data-stu-id="ceca1-102">ICLROnEventManager::RegisterActionOnEvent Method</span></span>
<span data-ttu-id="ceca1-103">Inscrit un pointeur de rappel pour l’événement spécifié.</span><span class="sxs-lookup"><span data-stu-id="ceca1-103">Registers a callback pointer for the specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ceca1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ceca1-104">Syntax</span></span>  
  
```cpp  
HRESULT RegisterActionOnEvent (  
    [in] EClrEvent event,  
    [in] IActionOnCLREvent *pAction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ceca1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ceca1-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="ceca1-106">dans L’une des valeurs [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) , indiquant l’événement pour lequel enregistrer le pointeur de rappel décrit par `pAction`.</span><span class="sxs-lookup"><span data-stu-id="ceca1-106">[in] One of the [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) values, indicating the event for which to register the callback pointer described by `pAction`.</span></span>  
  
 `pAction`  
 <span data-ttu-id="ceca1-107">dans Pointeur vers un objet [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) qui est appelé lorsque l’événement inscrit se déclenche.</span><span class="sxs-lookup"><span data-stu-id="ceca1-107">[in] A pointer to an [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) object that is called when the registered event fires.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ceca1-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ceca1-108">Return Value</span></span>  
  
|<span data-ttu-id="ceca1-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ceca1-109">HRESULT</span></span>|<span data-ttu-id="ceca1-110">Description</span><span class="sxs-lookup"><span data-stu-id="ceca1-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ceca1-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ceca1-111">S_OK</span></span>|<span data-ttu-id="ceca1-112">`RegisterActionOnEvent`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="ceca1-112">`RegisterActionOnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="ceca1-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ceca1-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ceca1-114">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="ceca1-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ceca1-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ceca1-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ceca1-116">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="ceca1-116">The call timed out.</span></span>|  
|<span data-ttu-id="ceca1-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ceca1-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ceca1-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="ceca1-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ceca1-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ceca1-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ceca1-120">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="ceca1-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ceca1-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ceca1-121">E_FAIL</span></span>|<span data-ttu-id="ceca1-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="ceca1-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ceca1-123">Une fois qu’une méthode a retourné E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="ceca1-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ceca1-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ceca1-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ceca1-125">Notes</span><span class="sxs-lookup"><span data-stu-id="ceca1-125">Remarks</span></span>  
 <span data-ttu-id="ceca1-126">L’hôte peut inscrire des rappels pour l’un des deux types d’événements, ou `EClrEvent`les deux, décrits par.</span><span class="sxs-lookup"><span data-stu-id="ceca1-126">The host can register callbacks for either or both of the two event types described by `EClrEvent`.</span></span> <span data-ttu-id="ceca1-127">L’hôte obtient l' `ICLROnEventManager` interface en appelant la méthode [ICLRControl:: GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ceca1-127">The host gets the `ICLROnEventManager` interface by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ceca1-128">Les événements `RegisterActionOnEvent` enregistrés peuvent être déclenchés plusieurs fois et à partir de différents threads pour signaler un déchargement ou la désactivation du CLR.</span><span class="sxs-lookup"><span data-stu-id="ceca1-128">The events that `RegisterActionOnEvent` registers can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ceca1-129">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ceca1-129">Requirements</span></span>  
 <span data-ttu-id="ceca1-130">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ceca1-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ceca1-131">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ceca1-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ceca1-132">**Bibliothèque** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ceca1-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ceca1-133">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ceca1-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ceca1-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ceca1-134">See also</span></span>

- [<span data-ttu-id="ceca1-135">EClrEvent, énumération</span><span class="sxs-lookup"><span data-stu-id="ceca1-135">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="ceca1-136">IActionOnCLREvent, interface</span><span class="sxs-lookup"><span data-stu-id="ceca1-136">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [<span data-ttu-id="ceca1-137">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="ceca1-137">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="ceca1-138">ICLROnEventManager, interface</span><span class="sxs-lookup"><span data-stu-id="ceca1-138">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
