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
ms.openlocfilehash: 505c16cb7ead7950b6d2d6d401730cc3368fb6aa
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703297"
---
# <a name="iclrruntimehostexecuteinappdomain-method"></a><span data-ttu-id="79015-102">ICLRRuntimeHost::ExecuteInAppDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="79015-102">ICLRRuntimeHost::ExecuteInAppDomain Method</span></span>
<span data-ttu-id="79015-103">Spécifie le <xref:System.AppDomain> dans lequel exécuter le code managé spécifié.</span><span class="sxs-lookup"><span data-stu-id="79015-103">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79015-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="79015-104">Syntax</span></span>  
  
```cpp  
HRESULT ExecuteInAppDomain(  
    [in] DWORD AppDomainId,
    [in] FExecuteInDomainCallback pCallback,
    [in] void* cookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79015-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="79015-105">Parameters</span></span>  
 `AppDomainId`  
 <span data-ttu-id="79015-106">dans ID numérique du <xref:System.AppDomain> dans lequel exécuter la méthode spécifiée.</span><span class="sxs-lookup"><span data-stu-id="79015-106">[in] The numeric ID of the <xref:System.AppDomain> in which to execute the specified method.</span></span>  
  
 `pCallback`  
 <span data-ttu-id="79015-107">dans Pointeur vers la fonction à exécuter dans le spécifié <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="79015-107">[in] A pointer to the function to execute within the specified <xref:System.AppDomain>.</span></span>  
  
 `cookie`  
 <span data-ttu-id="79015-108">dans Pointeur vers la mémoire opaque allouée par l’appelant.</span><span class="sxs-lookup"><span data-stu-id="79015-108">[in] A pointer to opaque caller-allocated memory.</span></span> <span data-ttu-id="79015-109">Ce paramètre est passé par le common language runtime (CLR) au rappel de domaine.</span><span class="sxs-lookup"><span data-stu-id="79015-109">This parameter is passed by the common language runtime (CLR) to the domain callback.</span></span> <span data-ttu-id="79015-110">Il ne s’agit pas d’une mémoire de tas managée par le Runtime ; l’allocation et la durée de vie de cette mémoire sont contrôlées par l’appelant.</span><span class="sxs-lookup"><span data-stu-id="79015-110">It is not runtime-managed heap memory; both the allocation and lifetime of this memory are controlled by the caller.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="79015-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="79015-111">Return Value</span></span>  
  
|<span data-ttu-id="79015-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="79015-112">HRESULT</span></span>|<span data-ttu-id="79015-113">Description</span><span class="sxs-lookup"><span data-stu-id="79015-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="79015-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="79015-114">S_OK</span></span>|<span data-ttu-id="79015-115">`ExecuteInAppDomain`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="79015-115">`ExecuteInAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="79015-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="79015-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="79015-117">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="79015-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="79015-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="79015-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="79015-119">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="79015-119">The call timed out.</span></span>|  
|<span data-ttu-id="79015-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="79015-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="79015-121">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="79015-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="79015-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="79015-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="79015-123">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="79015-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="79015-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="79015-124">E_FAIL</span></span>|<span data-ttu-id="79015-125">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="79015-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="79015-126">Si une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="79015-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="79015-127">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="79015-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="79015-128">Notes</span><span class="sxs-lookup"><span data-stu-id="79015-128">Remarks</span></span>  
 <span data-ttu-id="79015-129">`ExecuteInAppDomain`permet à l’hôte d’exercer le contrôle sur <xref:System.AppDomain> le managé dans lequel la méthode managée spécifiée doit être exécutée.</span><span class="sxs-lookup"><span data-stu-id="79015-129">`ExecuteInAppDomain` allows the host to exercise control over which managed <xref:System.AppDomain> the specified managed method should be executed in.</span></span> <span data-ttu-id="79015-130">Vous pouvez récupérer la valeur de l’identificateur d’un domaine d’application, qui correspond à la valeur de la <xref:System.AppDomain.Id%2A> propriété, en appelant la [méthode GetCurrentAppDomainId,](iclrruntimehost-getcurrentappdomainid-method.md).</span><span class="sxs-lookup"><span data-stu-id="79015-130">You can get the value of an application domain's identifier, which corresponds to the value of the <xref:System.AppDomain.Id%2A> property, by calling [GetCurrentAppDomainId Method](iclrruntimehost-getcurrentappdomainid-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79015-131">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="79015-131">Requirements</span></span>  
 <span data-ttu-id="79015-132">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79015-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79015-133">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="79015-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="79015-134">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="79015-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="79015-135">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79015-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79015-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="79015-136">See also</span></span>

- [<span data-ttu-id="79015-137">ICLRRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="79015-137">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
