---
title: ICLRRuntimeHost::UnloadAppDomain, méthode
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.UnloadAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::UnloadAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::UnloadAppDomain method [.NET Framework hosting]
- UnloadAppDomain method [.NET Framework hosting]
ms.assetid: 571912bc-3429-4ff8-8eb2-ea993ffbd901
topic_type:
- apiref
ms.openlocfilehash: cc5d0d65d213d952c0897a72d8ec38ea6b8b22db
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700663"
---
# <a name="iclrruntimehostunloadappdomain-method"></a><span data-ttu-id="ce6cc-102">ICLRRuntimeHost::UnloadAppDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="ce6cc-102">ICLRRuntimeHost::UnloadAppDomain Method</span></span>

<span data-ttu-id="ce6cc-103">Décharge le managé <xref:System.AppDomain> qui correspond à l’identificateur numérique spécifié.</span><span class="sxs-lookup"><span data-stu-id="ce6cc-103">Unloads the managed <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce6cc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ce6cc-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadAppDomain(  
    [in] DWORD dwAppDomainId  
    [in] BOOL  fWaitUntilDone  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce6cc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ce6cc-105">Parameters</span></span>  

 `dwAppDomainId`  
 <span data-ttu-id="ce6cc-106">dans Identificateur numérique du domaine d’application à décharger.</span><span class="sxs-lookup"><span data-stu-id="ce6cc-106">[in] The numeric identifier of the application domain to unload.</span></span>  
  
 `fWaitUntilDone`  
 <span data-ttu-id="ce6cc-107">[in] `true` pour indiquer que le common language runtime (CLR) doit attendre la fin de l’exécution du thread actuel de l’application avant de tenter de décharger le domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="ce6cc-107">[in] `true` to indicate that the common language runtime( CLR) must wait until it has finished executing the application's current thread before attempting to unload the application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ce6cc-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="ce6cc-108">Return Value</span></span>  
  
|<span data-ttu-id="ce6cc-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ce6cc-109">HRESULT</span></span>|<span data-ttu-id="ce6cc-110">Description</span><span class="sxs-lookup"><span data-stu-id="ce6cc-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ce6cc-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ce6cc-111">S_OK</span></span>|<span data-ttu-id="ce6cc-112">`UnloadAppDomain` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="ce6cc-112">`UnloadAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="ce6cc-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ce6cc-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ce6cc-114">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="ce6cc-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ce6cc-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ce6cc-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ce6cc-116">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="ce6cc-116">The call timed out.</span></span>|  
|<span data-ttu-id="ce6cc-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ce6cc-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ce6cc-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="ce6cc-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ce6cc-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ce6cc-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ce6cc-120">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="ce6cc-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ce6cc-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ce6cc-121">E_FAIL</span></span>|<span data-ttu-id="ce6cc-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="ce6cc-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ce6cc-123">Si une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="ce6cc-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ce6cc-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ce6cc-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce6cc-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="ce6cc-125">Remarks</span></span>  

 <span data-ttu-id="ce6cc-126">Vous pouvez récupérer l’identificateur numérique du domaine d’application dans lequel le thread actuel s’exécute en appelant [GetCurrentAppDomainId,](iclrruntimehost-getcurrentappdomainid-method.md).</span><span class="sxs-lookup"><span data-stu-id="ce6cc-126">You can get the numeric identifier of the application domain in which the current thread is executing by calling [GetCurrentAppDomainId](iclrruntimehost-getcurrentappdomainid-method.md).</span></span> <span data-ttu-id="ce6cc-127">Cet identificateur correspond à la <xref:System.AppDomain.Id%2A> propriété du <xref:System.AppDomain> type managé.</span><span class="sxs-lookup"><span data-stu-id="ce6cc-127">This identifier corresponds to the <xref:System.AppDomain.Id%2A> property of the managed <xref:System.AppDomain> type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce6cc-128">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ce6cc-128">Requirements</span></span>  

 <span data-ttu-id="ce6cc-129">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce6cc-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce6cc-130">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ce6cc-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ce6cc-131">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ce6cc-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ce6cc-132">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce6cc-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce6cc-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce6cc-133">See also</span></span>

- [<span data-ttu-id="ce6cc-134">ICLRRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="ce6cc-134">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
