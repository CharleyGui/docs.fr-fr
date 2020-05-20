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
ms.openlocfilehash: a216a2925382016adeb100554bdceefdf3ee902b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616058"
---
# <a name="iactiononclreventonevent-method"></a><span data-ttu-id="d44e2-102">IActionOnCLREvent::OnEvent, méthode</span><span class="sxs-lookup"><span data-stu-id="d44e2-102">IActionOnCLREvent::OnEvent Method</span></span>
<span data-ttu-id="d44e2-103">Exécute des rappels sur les événements qui ont été inscrits à l’aide d’un appel à la méthode [ICLROnEventManager :: RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d44e2-103">Performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d44e2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d44e2-104">Syntax</span></span>  
  
```cpp  
HRESULT OnEvent (  
    [in] EClrEvent event,  
    [in] PVOID     data  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d44e2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d44e2-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="d44e2-106">dans L’une des valeurs [EClrEvent](eclrevent-enumeration.md) , qui indique le type d’événement.</span><span class="sxs-lookup"><span data-stu-id="d44e2-106">[in] One of the [EClrEvent](eclrevent-enumeration.md) values, which indicates the type of event.</span></span>  
  
 `data`  
 <span data-ttu-id="d44e2-107">dans Pointeur vers un objet qui contient des détails sur `event` .</span><span class="sxs-lookup"><span data-stu-id="d44e2-107">[in] A pointer to an object that contains details about `event`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d44e2-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d44e2-108">Return Value</span></span>  
  
|<span data-ttu-id="d44e2-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d44e2-109">HRESULT</span></span>|<span data-ttu-id="d44e2-110">Description</span><span class="sxs-lookup"><span data-stu-id="d44e2-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d44e2-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d44e2-111">S_OK</span></span>|<span data-ttu-id="d44e2-112">`OnEvent`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="d44e2-112">`OnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="d44e2-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d44e2-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d44e2-114">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="d44e2-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d44e2-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d44e2-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d44e2-116">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="d44e2-116">The call timed out.</span></span>|  
|<span data-ttu-id="d44e2-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d44e2-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d44e2-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="d44e2-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d44e2-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d44e2-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d44e2-120">Un événement a été annulé alors qu’un thread ou une fibre bloqué attendait dessus.</span><span class="sxs-lookup"><span data-stu-id="d44e2-120">An event was cancelled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d44e2-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d44e2-121">E_FAIL</span></span>|<span data-ttu-id="d44e2-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="d44e2-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d44e2-123">Si une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="d44e2-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d44e2-124">Les appels suivants à toute méthode d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d44e2-124">Subsequent calls to any hosting method return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d44e2-125">Notes</span><span class="sxs-lookup"><span data-stu-id="d44e2-125">Remarks</span></span>  
 <span data-ttu-id="d44e2-126">Le `data` paramètre est un pointeur vers un objet de type non spécifié.</span><span class="sxs-lookup"><span data-stu-id="d44e2-126">The `data` parameter is a pointer to an object of unspecified type.</span></span> <span data-ttu-id="d44e2-127">Si le `event` paramètre a la valeur `Event_DomainUnload` , `data` est l’identificateur numérique pour le <xref:System.AppDomain> qui a été déchargé.</span><span class="sxs-lookup"><span data-stu-id="d44e2-127">If the `event` parameter is `Event_DomainUnload`, `data` is the numeric identifier for the <xref:System.AppDomain> that was unloaded.</span></span> <span data-ttu-id="d44e2-128">L’hôte peut prendre les mesures appropriées à l’aide de cet identificateur comme clé.</span><span class="sxs-lookup"><span data-stu-id="d44e2-128">The host can take appropriate action using this identifier as a key.</span></span>  
  
 <span data-ttu-id="d44e2-129">Si `event` est `Event_MDAFired` , `data` est un pointeur vers une instance [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) qui contient la sortie de message d’un Assistant Débogage managé (MDA).</span><span class="sxs-lookup"><span data-stu-id="d44e2-129">If `event` is `Event_MDAFired`, `data` is a pointer to an [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) instance that contains the message output from a Managed Debugging Assistant (MDA).</span></span> <span data-ttu-id="d44e2-130">Les MDA sont une fonctionnalité du CLR qui permet aux développeurs de déboguer, en générant des messages XML sur les événements qui, sinon, sont difficiles à intercepter.</span><span class="sxs-lookup"><span data-stu-id="d44e2-130">MDAs are a feature of the CLR that help developers with debugging, by generating XML messages about events that are otherwise difficult to trap.</span></span> <span data-ttu-id="d44e2-131">Ces messages peuvent être particulièrement utiles lors du débogage de transitions entre du code managé et du code non managé.</span><span class="sxs-lookup"><span data-stu-id="d44e2-131">Such messages can be especially useful in debugging transitions between managed and unmanaged code.</span></span> <span data-ttu-id="d44e2-132">Pour plus d’informations, consultez [diagnostic des erreurs avec les Assistants Débogage managé](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="d44e2-132">For more information, see [Diagnosing Errors with Managed Debugging Assistants](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d44e2-133">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="d44e2-133">Requirements</span></span>  
 <span data-ttu-id="d44e2-134">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d44e2-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d44e2-135">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d44e2-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d44e2-136">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d44e2-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d44e2-137">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d44e2-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d44e2-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d44e2-138">See also</span></span>

- [<span data-ttu-id="d44e2-139">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="d44e2-139">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="d44e2-140">EClrEvent, énumération</span><span class="sxs-lookup"><span data-stu-id="d44e2-140">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="d44e2-141">IActionOnCLREvent, interface</span><span class="sxs-lookup"><span data-stu-id="d44e2-141">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)
- [<span data-ttu-id="d44e2-142">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="d44e2-142">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="d44e2-143">ICLROnEventManager, interface</span><span class="sxs-lookup"><span data-stu-id="d44e2-143">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
- [<span data-ttu-id="d44e2-144">MDAInfo, structure</span><span class="sxs-lookup"><span data-stu-id="d44e2-144">MDAInfo Structure</span></span>](mdainfo-structure.md)
