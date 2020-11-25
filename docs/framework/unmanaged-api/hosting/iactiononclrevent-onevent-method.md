---
title: IActionOnCLREvent::OnEvent, méthode
ms.date: 03/30/2017
api_name:
- IActionOnCLREvent.OnEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IActionOnCLREvent::OnEvent
helpviewer_keywords:
- OnEvent method [.NET Framework hosting]
- IActionOnCLREvent::OnEvent method [.NET Framework hosting]
ms.assetid: 0970f10c-4304-4c12-91c0-83e51455afb4
topic_type:
- apiref
ms.openlocfilehash: 3bfcb01e30b4cb33ec9276f1d3c6ac2f3bde4b58
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721762"
---
# <a name="iactiononclreventonevent-method"></a><span data-ttu-id="0fb6b-102">IActionOnCLREvent::OnEvent, méthode</span><span class="sxs-lookup"><span data-stu-id="0fb6b-102">IActionOnCLREvent::OnEvent Method</span></span>

<span data-ttu-id="0fb6b-103">Exécute des rappels sur les événements qui ont été inscrits à l’aide d’un appel à la méthode [ICLROnEventManager :: RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) .</span><span class="sxs-lookup"><span data-stu-id="0fb6b-103">Performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fb6b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0fb6b-104">Syntax</span></span>  
  
```cpp  
HRESULT OnEvent (  
    [in] EClrEvent event,  
    [in] PVOID     data  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0fb6b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0fb6b-105">Parameters</span></span>  

 `event`  
 <span data-ttu-id="0fb6b-106">dans L’une des valeurs [EClrEvent](eclrevent-enumeration.md) , qui indique le type d’événement.</span><span class="sxs-lookup"><span data-stu-id="0fb6b-106">[in] One of the [EClrEvent](eclrevent-enumeration.md) values, which indicates the type of event.</span></span>  
  
 `data`  
 <span data-ttu-id="0fb6b-107">dans Pointeur vers un objet qui contient des détails sur `event` .</span><span class="sxs-lookup"><span data-stu-id="0fb6b-107">[in] A pointer to an object that contains details about `event`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0fb6b-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="0fb6b-108">Return Value</span></span>  
  
|<span data-ttu-id="0fb6b-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0fb6b-109">HRESULT</span></span>|<span data-ttu-id="0fb6b-110">Description</span><span class="sxs-lookup"><span data-stu-id="0fb6b-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0fb6b-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="0fb6b-111">S_OK</span></span>|<span data-ttu-id="0fb6b-112">`OnEvent` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="0fb6b-112">`OnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="0fb6b-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0fb6b-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0fb6b-114">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="0fb6b-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0fb6b-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0fb6b-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0fb6b-116">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="0fb6b-116">The call timed out.</span></span>|  
|<span data-ttu-id="0fb6b-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0fb6b-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0fb6b-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="0fb6b-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0fb6b-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0fb6b-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0fb6b-120">Un événement a été annulé alors qu’un thread ou une fibre bloqué attendait dessus.</span><span class="sxs-lookup"><span data-stu-id="0fb6b-120">An event was cancelled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0fb6b-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0fb6b-121">E_FAIL</span></span>|<span data-ttu-id="0fb6b-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="0fb6b-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0fb6b-123">Si une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="0fb6b-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0fb6b-124">Les appels suivants à toute méthode d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0fb6b-124">Subsequent calls to any hosting method return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0fb6b-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="0fb6b-125">Remarks</span></span>  

 <span data-ttu-id="0fb6b-126">Le `data` paramètre est un pointeur vers un objet de type non spécifié.</span><span class="sxs-lookup"><span data-stu-id="0fb6b-126">The `data` parameter is a pointer to an object of unspecified type.</span></span> <span data-ttu-id="0fb6b-127">Si le `event` paramètre a la valeur `Event_DomainUnload` , `data` est l’identificateur numérique pour le <xref:System.AppDomain> qui a été déchargé.</span><span class="sxs-lookup"><span data-stu-id="0fb6b-127">If the `event` parameter is `Event_DomainUnload`, `data` is the numeric identifier for the <xref:System.AppDomain> that was unloaded.</span></span> <span data-ttu-id="0fb6b-128">L’hôte peut prendre les mesures appropriées à l’aide de cet identificateur comme clé.</span><span class="sxs-lookup"><span data-stu-id="0fb6b-128">The host can take appropriate action using this identifier as a key.</span></span>  
  
 <span data-ttu-id="0fb6b-129">Si `event` est `Event_MDAFired` , `data` est un pointeur vers une instance [MDAInfo](mdainfo-structure.md) qui contient la sortie de message d’un Assistant Débogage managé (MDA).</span><span class="sxs-lookup"><span data-stu-id="0fb6b-129">If `event` is `Event_MDAFired`, `data` is a pointer to an [MDAInfo](mdainfo-structure.md) instance that contains the message output from a Managed Debugging Assistant (MDA).</span></span> <span data-ttu-id="0fb6b-130">Les MDA sont une fonctionnalité du CLR qui permet aux développeurs de déboguer, en générant des messages XML sur les événements qui, sinon, sont difficiles à intercepter.</span><span class="sxs-lookup"><span data-stu-id="0fb6b-130">MDAs are a feature of the CLR that help developers with debugging, by generating XML messages about events that are otherwise difficult to trap.</span></span> <span data-ttu-id="0fb6b-131">Ces messages peuvent être particulièrement utiles lors du débogage de transitions entre du code managé et du code non managé.</span><span class="sxs-lookup"><span data-stu-id="0fb6b-131">Such messages can be especially useful in debugging transitions between managed and unmanaged code.</span></span> <span data-ttu-id="0fb6b-132">Pour plus d’informations, consultez [diagnostic des erreurs avec les Assistants Débogage managé](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="0fb6b-132">For more information, see [Diagnosing Errors with Managed Debugging Assistants](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0fb6b-133">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0fb6b-133">Requirements</span></span>  

 <span data-ttu-id="0fb6b-134">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0fb6b-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0fb6b-135">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0fb6b-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0fb6b-136">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0fb6b-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0fb6b-137">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0fb6b-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fb6b-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0fb6b-138">See also</span></span>

- [<span data-ttu-id="0fb6b-139">Diagnostic d'erreurs avec les Assistants de débogage managés</span><span class="sxs-lookup"><span data-stu-id="0fb6b-139">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="0fb6b-140">EClrEvent, énumération</span><span class="sxs-lookup"><span data-stu-id="0fb6b-140">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="0fb6b-141">IActionOnCLREvent, interface</span><span class="sxs-lookup"><span data-stu-id="0fb6b-141">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)
- [<span data-ttu-id="0fb6b-142">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="0fb6b-142">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="0fb6b-143">ICLROnEventManager, interface</span><span class="sxs-lookup"><span data-stu-id="0fb6b-143">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
- [<span data-ttu-id="0fb6b-144">MDAInfo, structure</span><span class="sxs-lookup"><span data-stu-id="0fb6b-144">MDAInfo Structure</span></span>](mdainfo-structure.md)
