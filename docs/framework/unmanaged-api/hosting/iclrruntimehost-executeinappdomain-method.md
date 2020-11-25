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
ms.openlocfilehash: 4c28c4a5cc64b20c9ac9c57e1aef5e7b90a20e01
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728886"
---
# <a name="iclrruntimehostexecuteinappdomain-method"></a><span data-ttu-id="1b80d-102">ICLRRuntimeHost::ExecuteInAppDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="1b80d-102">ICLRRuntimeHost::ExecuteInAppDomain Method</span></span>

<span data-ttu-id="1b80d-103">Spécifie le <xref:System.AppDomain> dans lequel exécuter le code managé spécifié.</span><span class="sxs-lookup"><span data-stu-id="1b80d-103">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b80d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1b80d-104">Syntax</span></span>  
  
```cpp  
HRESULT ExecuteInAppDomain(  
    [in] DWORD AppDomainId,
    [in] FExecuteInDomainCallback pCallback,
    [in] void* cookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b80d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1b80d-105">Parameters</span></span>  

 `AppDomainId`  
 <span data-ttu-id="1b80d-106">dans ID numérique du <xref:System.AppDomain> dans lequel exécuter la méthode spécifiée.</span><span class="sxs-lookup"><span data-stu-id="1b80d-106">[in] The numeric ID of the <xref:System.AppDomain> in which to execute the specified method.</span></span>  
  
 `pCallback`  
 <span data-ttu-id="1b80d-107">dans Pointeur vers la fonction à exécuter dans le spécifié <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="1b80d-107">[in] A pointer to the function to execute within the specified <xref:System.AppDomain>.</span></span>  
  
 `cookie`  
 <span data-ttu-id="1b80d-108">dans Pointeur vers la mémoire opaque allouée par l’appelant.</span><span class="sxs-lookup"><span data-stu-id="1b80d-108">[in] A pointer to opaque caller-allocated memory.</span></span> <span data-ttu-id="1b80d-109">Ce paramètre est passé par le common language runtime (CLR) au rappel de domaine.</span><span class="sxs-lookup"><span data-stu-id="1b80d-109">This parameter is passed by the common language runtime (CLR) to the domain callback.</span></span> <span data-ttu-id="1b80d-110">Il ne s’agit pas d’une mémoire de tas managée par le Runtime ; l’allocation et la durée de vie de cette mémoire sont contrôlées par l’appelant.</span><span class="sxs-lookup"><span data-stu-id="1b80d-110">It is not runtime-managed heap memory; both the allocation and lifetime of this memory are controlled by the caller.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1b80d-111">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="1b80d-111">Return Value</span></span>  
  
|<span data-ttu-id="1b80d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1b80d-112">HRESULT</span></span>|<span data-ttu-id="1b80d-113">Description</span><span class="sxs-lookup"><span data-stu-id="1b80d-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1b80d-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="1b80d-114">S_OK</span></span>|<span data-ttu-id="1b80d-115">`ExecuteInAppDomain` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="1b80d-115">`ExecuteInAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="1b80d-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1b80d-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1b80d-117">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="1b80d-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1b80d-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1b80d-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1b80d-119">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="1b80d-119">The call timed out.</span></span>|  
|<span data-ttu-id="1b80d-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1b80d-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1b80d-121">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="1b80d-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1b80d-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1b80d-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1b80d-123">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="1b80d-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1b80d-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1b80d-124">E_FAIL</span></span>|<span data-ttu-id="1b80d-125">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="1b80d-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1b80d-126">Si une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="1b80d-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1b80d-127">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1b80d-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b80d-128">Remarques</span><span class="sxs-lookup"><span data-stu-id="1b80d-128">Remarks</span></span>  

 <span data-ttu-id="1b80d-129">`ExecuteInAppDomain` permet à l’hôte d’exercer le contrôle sur <xref:System.AppDomain> le managé dans lequel la méthode managée spécifiée doit être exécutée.</span><span class="sxs-lookup"><span data-stu-id="1b80d-129">`ExecuteInAppDomain` allows the host to exercise control over which managed <xref:System.AppDomain> the specified managed method should be executed in.</span></span> <span data-ttu-id="1b80d-130">Vous pouvez récupérer la valeur de l’identificateur d’un domaine d’application, qui correspond à la valeur de la <xref:System.AppDomain.Id%2A> propriété, en appelant la [méthode GetCurrentAppDomainId,](iclrruntimehost-getcurrentappdomainid-method.md).</span><span class="sxs-lookup"><span data-stu-id="1b80d-130">You can get the value of an application domain's identifier, which corresponds to the value of the <xref:System.AppDomain.Id%2A> property, by calling [GetCurrentAppDomainId Method](iclrruntimehost-getcurrentappdomainid-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b80d-131">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1b80d-131">Requirements</span></span>  

 <span data-ttu-id="1b80d-132">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b80d-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b80d-133">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1b80d-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1b80d-134">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1b80d-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1b80d-135">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b80d-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b80d-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1b80d-136">See also</span></span>

- [<span data-ttu-id="1b80d-137">ICLRRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="1b80d-137">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
