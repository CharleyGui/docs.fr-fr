---
title: ICLROnEventManager::UnregisterActionOnEvent, méthode
ms.date: 03/30/2017
api_name:
- ICLROnEventManager.UnregisterActionOnEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLROnEventManager::UnregisterActionOnEvent
helpviewer_keywords:
- UnRegisterActionOnEvent method [.NET Framework hosting]
- ICLROnEventManager::UnRegisterActionOnEvent method [.NET Framework hosting]
ms.assetid: 4c02ec37-cdf0-46b2-890e-235092741236
topic_type:
- apiref
ms.openlocfilehash: ca3c7fe813f22d3beab3087414100b3d8e5814ac
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725597"
---
# <a name="iclroneventmanagerunregisteractiononevent-method"></a><span data-ttu-id="1411e-102">ICLROnEventManager::UnregisterActionOnEvent, méthode</span><span class="sxs-lookup"><span data-stu-id="1411e-102">ICLROnEventManager::UnregisterActionOnEvent Method</span></span>

<span data-ttu-id="1411e-103">Annule l’inscription d’un pointeur de rappel précédemment inscrit pour l’événement spécifié.</span><span class="sxs-lookup"><span data-stu-id="1411e-103">Unregisters a previously registered callback pointer for the specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1411e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1411e-104">Syntax</span></span>  
  
```cpp  
HRESULT UnregisterActionOnEvent (  
    [in] EClrEvent event,  
    [in] IActionOnCLREvent *pAction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1411e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1411e-105">Parameters</span></span>  

 `event`  
 <span data-ttu-id="1411e-106">dans L’une des valeurs [EClrEvent](eclrevent-enumeration.md) , indiquant l’événement pour lequel annuler l’inscription du pointeur de rappel décrit par `pAction` .</span><span class="sxs-lookup"><span data-stu-id="1411e-106">[in] One of the [EClrEvent](eclrevent-enumeration.md) values, indicating the event for which to unregister the callback pointer described by `pAction`.</span></span>  
  
 `pAction`  
 <span data-ttu-id="1411e-107">dans Pointeur vers un objet [IActionOnCLREvent](iactiononclrevent-interface.md) qui a été passé en tant que paramètre à la méthode [RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) .</span><span class="sxs-lookup"><span data-stu-id="1411e-107">[in] A pointer to an [IActionOnCLREvent](iactiononclrevent-interface.md) object that was passed as a parameter to the [RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1411e-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="1411e-108">Return Value</span></span>  
  
|<span data-ttu-id="1411e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1411e-109">HRESULT</span></span>|<span data-ttu-id="1411e-110">Description</span><span class="sxs-lookup"><span data-stu-id="1411e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1411e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="1411e-111">S_OK</span></span>|<span data-ttu-id="1411e-112">`UnregisterActionOnEvent` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="1411e-112">`UnregisterActionOnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="1411e-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1411e-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1411e-114">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="1411e-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1411e-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1411e-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1411e-116">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="1411e-116">The call timed out.</span></span>|  
|<span data-ttu-id="1411e-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1411e-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1411e-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="1411e-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1411e-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1411e-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1411e-120">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="1411e-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1411e-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1411e-121">E_FAIL</span></span>|<span data-ttu-id="1411e-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="1411e-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1411e-123">Une fois que la méthode a retourné E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="1411e-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1411e-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1411e-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1411e-125">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1411e-125">Requirements</span></span>  

 <span data-ttu-id="1411e-126">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1411e-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1411e-127">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1411e-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1411e-128">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1411e-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1411e-129">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1411e-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1411e-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1411e-130">See also</span></span>

- [<span data-ttu-id="1411e-131">EClrEvent, énumération</span><span class="sxs-lookup"><span data-stu-id="1411e-131">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="1411e-132">IActionOnCLREvent, interface</span><span class="sxs-lookup"><span data-stu-id="1411e-132">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)
- [<span data-ttu-id="1411e-133">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="1411e-133">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="1411e-134">ICLROnEventManager, interface</span><span class="sxs-lookup"><span data-stu-id="1411e-134">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
