---
title: ICLRPolicyManager::SetActionOnTimeout, méthode
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetActionOnTimeout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetActionOnTimeout
helpviewer_keywords:
- SetActionOnTimeout method [.NET Framework hosting]
- ICLRPolicyManager::SetActionOnTimeout method [.NET Framework hosting]
ms.assetid: 38439fa1-2b99-4fa8-a6ec-08afc0f83b9c
topic_type:
- apiref
ms.openlocfilehash: 9ef906ed5e8a6985c084741bf06b683da79c546e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140786"
---
# <a name="iclrpolicymanagersetactionontimeout-method"></a><span data-ttu-id="5781e-102">ICLRPolicyManager::SetActionOnTimeout, méthode</span><span class="sxs-lookup"><span data-stu-id="5781e-102">ICLRPolicyManager::SetActionOnTimeout Method</span></span>
<span data-ttu-id="5781e-103">Spécifie l’action de stratégie que le common language runtime (CLR) doit prendre lorsque l’opération spécifiée expire.</span><span class="sxs-lookup"><span data-stu-id="5781e-103">Specifies the policy action the common language runtime (CLR) should take when the specified operation times out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5781e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5781e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetActionOnTimeout (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5781e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5781e-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="5781e-106">dans L’une des valeurs [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) , indiquant l’opération pour laquelle spécifier l’action de délai d’attente.</span><span class="sxs-lookup"><span data-stu-id="5781e-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the operation for which to specify the timeout action.</span></span> <span data-ttu-id="5781e-107">Les valeurs suivantes sont prises en charge :</span><span class="sxs-lookup"><span data-stu-id="5781e-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="5781e-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="5781e-108">OPR_AppDomainUnload</span></span>  
  
- <span data-ttu-id="5781e-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="5781e-109">OPR_ProcessExit</span></span>  
  
- <span data-ttu-id="5781e-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="5781e-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
- <span data-ttu-id="5781e-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="5781e-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `action`  
 <span data-ttu-id="5781e-112">dans L’une des valeurs [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) , indiquant l’action de stratégie à prendre lorsque l’opération expire.</span><span class="sxs-lookup"><span data-stu-id="5781e-112">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the policy action to be taken when the operation times out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5781e-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="5781e-113">Return Value</span></span>  
  
|<span data-ttu-id="5781e-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5781e-114">HRESULT</span></span>|<span data-ttu-id="5781e-115">Description</span><span class="sxs-lookup"><span data-stu-id="5781e-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5781e-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="5781e-116">S_OK</span></span>|<span data-ttu-id="5781e-117">`SetActionOnTimeout` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="5781e-117">`SetActionOnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="5781e-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5781e-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5781e-119">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="5781e-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5781e-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5781e-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5781e-121">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="5781e-121">The call timed out.</span></span>|  
|<span data-ttu-id="5781e-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5781e-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5781e-123">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="5781e-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5781e-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5781e-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5781e-125">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="5781e-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5781e-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5781e-126">E_FAIL</span></span>|<span data-ttu-id="5781e-127">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="5781e-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5781e-128">Une fois qu’une méthode a retourné E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="5781e-128">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5781e-129">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5781e-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5781e-130">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="5781e-130">E_INVALIDARG</span></span>|<span data-ttu-id="5781e-131">Un délai d’expiration ne peut pas être défini pour la `operation`spécifiée, ou une valeur non valide a été fournie pour `operation`.</span><span class="sxs-lookup"><span data-stu-id="5781e-131">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5781e-132">Notes</span><span class="sxs-lookup"><span data-stu-id="5781e-132">Remarks</span></span>  
 <span data-ttu-id="5781e-133">La valeur du délai d’attente peut être soit le délai d’attente par défaut défini par le CLR, soit une valeur spécifiée par l’hôte dans un appel à la méthode [ICLRPolicyManager :: setTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5781e-133">The timeout value can be either the default timeout set by the CLR, or a value specified by the host in a call to the [ICLRPolicyManager::SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) method.</span></span>  
  
 <span data-ttu-id="5781e-134">Toutes les valeurs d’action de stratégie ne peuvent pas être spécifiées comme le comportement de délai d’attente pour les opérations CLR.</span><span class="sxs-lookup"><span data-stu-id="5781e-134">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="5781e-135">`SetActionOnTimeout` est généralement utilisé uniquement pour faire remonter le comportement.</span><span class="sxs-lookup"><span data-stu-id="5781e-135">`SetActionOnTimeout` is typically used only to escalate behavior.</span></span> <span data-ttu-id="5781e-136">Par exemple, un hôte peut spécifier que les abandons de thread soient convertis en abandons de thread bruts, mais ne peuvent pas spécifier l’inverse.</span><span class="sxs-lookup"><span data-stu-id="5781e-136">For example, a host can specify that thread aborts be turned into rude thread aborts, but cannot specify the opposite.</span></span> <span data-ttu-id="5781e-137">Le tableau ci-dessous décrit les valeurs de `action` valides pour les valeurs de `operation` valides.</span><span class="sxs-lookup"><span data-stu-id="5781e-137">The table below describes the valid `action` values for valid `operation` values.</span></span>  
  
|<span data-ttu-id="5781e-138">Valeur pour `operation`</span><span class="sxs-lookup"><span data-stu-id="5781e-138">Value for `operation`</span></span>|<span data-ttu-id="5781e-139">Valeurs valides pour `action`</span><span class="sxs-lookup"><span data-stu-id="5781e-139">Valid values for `action`</span></span>|  
|---------------------------|-------------------------------|  
|<span data-ttu-id="5781e-140">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="5781e-140">OPR_ThreadRudeAbortInNonCriticalRegion</span></span><br /><br /> <span data-ttu-id="5781e-141">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="5781e-141">OPR_ThreadRudeAbortInCriticalRegion</span></span>|<span data-ttu-id="5781e-142">- eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="5781e-142">-   eRudeAbortThread</span></span><br /><span data-ttu-id="5781e-143">- eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="5781e-143">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="5781e-144">- eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="5781e-144">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="5781e-145">- eExitProcess</span><span class="sxs-lookup"><span data-stu-id="5781e-145">-   eExitProcess</span></span><br /><span data-ttu-id="5781e-146">- eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="5781e-146">-   eFastExitProcess</span></span><br /><span data-ttu-id="5781e-147">- eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="5781e-147">-   eRudeExitProcess</span></span><br /><span data-ttu-id="5781e-148">- eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="5781e-148">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="5781e-149">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="5781e-149">OPR_AppDomainUnload</span></span>|<span data-ttu-id="5781e-150">- eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="5781e-150">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="5781e-151">- eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="5781e-151">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="5781e-152">- eExitProcess</span><span class="sxs-lookup"><span data-stu-id="5781e-152">-   eExitProcess</span></span><br /><span data-ttu-id="5781e-153">- eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="5781e-153">-   eFastExitProcess</span></span><br /><span data-ttu-id="5781e-154">- eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="5781e-154">-   eRudeExitProcess</span></span><br /><span data-ttu-id="5781e-155">- eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="5781e-155">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="5781e-156">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="5781e-156">OPR_ProcessExit</span></span>|<span data-ttu-id="5781e-157">- eExitProcess</span><span class="sxs-lookup"><span data-stu-id="5781e-157">-   eExitProcess</span></span><br /><span data-ttu-id="5781e-158">- eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="5781e-158">-   eFastExitProcess</span></span><br /><span data-ttu-id="5781e-159">- eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="5781e-159">-   eRudeExitProcess</span></span><br /><span data-ttu-id="5781e-160">- eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="5781e-160">-   eDisableRuntime</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5781e-161">spécifications</span><span class="sxs-lookup"><span data-stu-id="5781e-161">Requirements</span></span>  
 <span data-ttu-id="5781e-162">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5781e-162">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5781e-163">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5781e-163">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5781e-164">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5781e-164">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5781e-165">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5781e-165">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5781e-166">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5781e-166">See also</span></span>

- [<span data-ttu-id="5781e-167">EClrOperation, énumération</span><span class="sxs-lookup"><span data-stu-id="5781e-167">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="5781e-168">EPolicyAction, énumération</span><span class="sxs-lookup"><span data-stu-id="5781e-168">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="5781e-169">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="5781e-169">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="5781e-170">ICLRPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="5781e-170">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
