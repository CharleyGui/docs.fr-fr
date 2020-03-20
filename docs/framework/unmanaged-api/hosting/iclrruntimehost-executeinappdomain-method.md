---
title: ICLRRuntimeHost::ExecuteInAppDomain, méthode
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteInAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteInAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInAppDomain method [.NET Framework hosting]
- ExecuteInAppDomain method [.NET Framework hosting]
ms.assetid: e2b0e2db-3fae-4b56-844e-d30a125a660c
topic_type:
- apiref
ms.openlocfilehash: c012e4e2b5e41737f7bbe6a0fb887693b0ba22c8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176420"
---
# <a name="iclrruntimehostexecuteinappdomain-method"></a><span data-ttu-id="b9170-102">ICLRRuntimeHost::ExecuteInAppDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="b9170-102">ICLRRuntimeHost::ExecuteInAppDomain Method</span></span>
<span data-ttu-id="b9170-103">Spécifie le <xref:System.AppDomain> code géré spécifié.</span><span class="sxs-lookup"><span data-stu-id="b9170-103">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9170-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b9170-104">Syntax</span></span>  
  
```cpp  
HRESULT ExecuteInAppDomain(  
    [in] DWORD AppDomainId,
    [in] FExecuteInDomainCallback pCallback,
    [in] void* cookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9170-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b9170-105">Parameters</span></span>  
 `AppDomainId`  
 <span data-ttu-id="b9170-106">[dans] L’ID numérique <xref:System.AppDomain> de la méthode spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b9170-106">[in] The numeric ID of the <xref:System.AppDomain> in which to execute the specified method.</span></span>  
  
 `pCallback`  
 <span data-ttu-id="b9170-107">[dans] Un pointeur à la fonction <xref:System.AppDomain>à exécuter dans le spécifié .</span><span class="sxs-lookup"><span data-stu-id="b9170-107">[in] A pointer to the function to execute within the specified <xref:System.AppDomain>.</span></span>  
  
 `cookie`  
 <span data-ttu-id="b9170-108">[dans] Un pointeur à la mémoire opaque d’appelant-attribué.</span><span class="sxs-lookup"><span data-stu-id="b9170-108">[in] A pointer to opaque caller-allocated memory.</span></span> <span data-ttu-id="b9170-109">Ce paramètre est transmis par l’heure de l’exécution de la langue commune (CLR) au rappel de domaine.</span><span class="sxs-lookup"><span data-stu-id="b9170-109">This parameter is passed by the common language runtime (CLR) to the domain callback.</span></span> <span data-ttu-id="b9170-110">Ce n’est pas la mémoire de tas gérée par le temps d’exécution; l’allocation et la durée de vie de cette mémoire sont contrôlées par l’appelant.</span><span class="sxs-lookup"><span data-stu-id="b9170-110">It is not runtime-managed heap memory; both the allocation and lifetime of this memory are controlled by the caller.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b9170-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="b9170-111">Return Value</span></span>  
  
|<span data-ttu-id="b9170-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b9170-112">HRESULT</span></span>|<span data-ttu-id="b9170-113">Description</span><span class="sxs-lookup"><span data-stu-id="b9170-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b9170-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="b9170-114">S_OK</span></span>|<span data-ttu-id="b9170-115">`ExecuteInAppDomain`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="b9170-115">`ExecuteInAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="b9170-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b9170-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b9170-117">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un état dans lequel il ne peut pas exécuter le code géré ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="b9170-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b9170-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b9170-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b9170-119">L’appel s’est fait chronométrer.</span><span class="sxs-lookup"><span data-stu-id="b9170-119">The call timed out.</span></span>|  
|<span data-ttu-id="b9170-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b9170-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b9170-121">L’appelant n’est pas propriétaire de la serrure.</span><span class="sxs-lookup"><span data-stu-id="b9170-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b9170-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b9170-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b9170-123">Un événement a été annulé alors qu’un fil bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="b9170-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b9170-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b9170-124">E_FAIL</span></span>|<span data-ttu-id="b9170-125">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="b9170-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b9170-126">Si une méthode revient E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="b9170-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b9170-127">Les appels ultérieurs aux méthodes d’hébergement reviennent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b9170-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9170-128">Notes </span><span class="sxs-lookup"><span data-stu-id="b9170-128">Remarks</span></span>  
 <span data-ttu-id="b9170-129">`ExecuteInAppDomain`permet à l’hôte d’exercer un contrôle sur <xref:System.AppDomain> la méthode gérée spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b9170-129">`ExecuteInAppDomain` allows the host to exercise control over which managed <xref:System.AppDomain> the specified managed method should be executed in.</span></span> <span data-ttu-id="b9170-130">Vous pouvez obtenir la valeur de l’identifiant d’un domaine <xref:System.AppDomain.Id%2A> d’application, qui correspond à la valeur de la propriété, en appelant [GetCurrentAppDomainId Méthode](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span><span class="sxs-lookup"><span data-stu-id="b9170-130">You can get the value of an application domain's identifier, which corresponds to the value of the <xref:System.AppDomain.Id%2A> property, by calling [GetCurrentAppDomainId Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9170-131">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b9170-131">Requirements</span></span>  
 <span data-ttu-id="b9170-132">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9170-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9170-133">**En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor</span><span class="sxs-lookup"><span data-stu-id="b9170-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b9170-134">**Bibliothèque:** Inclus comme une ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b9170-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b9170-135">**.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9170-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9170-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b9170-136">See also</span></span>

- [<span data-ttu-id="b9170-137">ICLRRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="b9170-137">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
