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
ms.openlocfilehash: 3ddd78ea35d5709abb30af085b2212a09b28c2ef
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725558"
---
# <a name="iclrpolicymanagersetactionontimeout-method"></a><span data-ttu-id="e721c-102">ICLRPolicyManager::SetActionOnTimeout, méthode</span><span class="sxs-lookup"><span data-stu-id="e721c-102">ICLRPolicyManager::SetActionOnTimeout Method</span></span>

<span data-ttu-id="e721c-103">Spécifie l’action de stratégie que le common language runtime (CLR) doit prendre lorsque l’opération spécifiée expire.</span><span class="sxs-lookup"><span data-stu-id="e721c-103">Specifies the policy action the common language runtime (CLR) should take when the specified operation times out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e721c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e721c-104">Syntax</span></span>  
  
```cpp  
HRESULT SetActionOnTimeout (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e721c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e721c-105">Parameters</span></span>  

 `operation`  
 <span data-ttu-id="e721c-106">dans L’une des valeurs [EClrOperation](eclroperation-enumeration.md) , indiquant l’opération pour laquelle spécifier l’action de délai d’attente.</span><span class="sxs-lookup"><span data-stu-id="e721c-106">[in] One of the [EClrOperation](eclroperation-enumeration.md) values, indicating the operation for which to specify the timeout action.</span></span> <span data-ttu-id="e721c-107">Les valeurs suivantes sont admises :</span><span class="sxs-lookup"><span data-stu-id="e721c-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="e721c-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="e721c-108">OPR_AppDomainUnload</span></span>  
  
- <span data-ttu-id="e721c-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="e721c-109">OPR_ProcessExit</span></span>  
  
- <span data-ttu-id="e721c-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="e721c-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
- <span data-ttu-id="e721c-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="e721c-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `action`  
 <span data-ttu-id="e721c-112">dans L’une des valeurs [EPolicyAction](epolicyaction-enumeration.md) , indiquant l’action de stratégie à prendre lorsque l’opération expire.</span><span class="sxs-lookup"><span data-stu-id="e721c-112">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the policy action to be taken when the operation times out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e721c-113">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="e721c-113">Return Value</span></span>  
  
|<span data-ttu-id="e721c-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e721c-114">HRESULT</span></span>|<span data-ttu-id="e721c-115">Description</span><span class="sxs-lookup"><span data-stu-id="e721c-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e721c-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="e721c-116">S_OK</span></span>|<span data-ttu-id="e721c-117">`SetActionOnTimeout` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="e721c-117">`SetActionOnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="e721c-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e721c-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e721c-119">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="e721c-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e721c-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e721c-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e721c-121">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="e721c-121">The call timed out.</span></span>|  
|<span data-ttu-id="e721c-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e721c-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e721c-123">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="e721c-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e721c-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e721c-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e721c-125">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="e721c-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e721c-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e721c-126">E_FAIL</span></span>|<span data-ttu-id="e721c-127">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="e721c-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e721c-128">Une fois que la méthode a retourné E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="e721c-128">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e721c-129">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e721c-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e721c-130">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="e721c-130">E_INVALIDARG</span></span>|<span data-ttu-id="e721c-131">Un délai d’expiration ne peut pas être défini pour le spécifié `operation` , ou une valeur non valide a été fournie pour `operation` .</span><span class="sxs-lookup"><span data-stu-id="e721c-131">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e721c-132">Remarques</span><span class="sxs-lookup"><span data-stu-id="e721c-132">Remarks</span></span>  

 <span data-ttu-id="e721c-133">La valeur du délai d’attente peut être soit le délai d’attente par défaut défini par le CLR, soit une valeur spécifiée par l’hôte dans un appel à la méthode [ICLRPolicyManager :: setTimeout](iclrpolicymanager-settimeout-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e721c-133">The timeout value can be either the default timeout set by the CLR, or a value specified by the host in a call to the [ICLRPolicyManager::SetTimeout](iclrpolicymanager-settimeout-method.md) method.</span></span>  
  
 <span data-ttu-id="e721c-134">Toutes les valeurs d’action de stratégie ne peuvent pas être spécifiées comme le comportement de délai d’attente pour les opérations CLR.</span><span class="sxs-lookup"><span data-stu-id="e721c-134">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="e721c-135">`SetActionOnTimeout` est généralement utilisé uniquement pour faire remonter le comportement.</span><span class="sxs-lookup"><span data-stu-id="e721c-135">`SetActionOnTimeout` is typically used only to escalate behavior.</span></span> <span data-ttu-id="e721c-136">Par exemple, un hôte peut spécifier que les abandons de thread soient convertis en abandons de thread bruts, mais ne peuvent pas spécifier l’inverse.</span><span class="sxs-lookup"><span data-stu-id="e721c-136">For example, a host can specify that thread aborts be turned into rude thread aborts, but cannot specify the opposite.</span></span> <span data-ttu-id="e721c-137">Le tableau ci-dessous décrit les valeurs valides `action` pour les valeurs valides `operation` .</span><span class="sxs-lookup"><span data-stu-id="e721c-137">The table below describes the valid `action` values for valid `operation` values.</span></span>  
  
|<span data-ttu-id="e721c-138">Valeur pour `operation`</span><span class="sxs-lookup"><span data-stu-id="e721c-138">Value for `operation`</span></span>|<span data-ttu-id="e721c-139">Valeurs valides pour `action`</span><span class="sxs-lookup"><span data-stu-id="e721c-139">Valid values for `action`</span></span>|  
|---------------------------|-------------------------------|  
|<span data-ttu-id="e721c-140">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="e721c-140">OPR_ThreadRudeAbortInNonCriticalRegion</span></span><br /><br /> <span data-ttu-id="e721c-141">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="e721c-141">OPR_ThreadRudeAbortInCriticalRegion</span></span>|<span data-ttu-id="e721c-142">- eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="e721c-142">-   eRudeAbortThread</span></span><br /><span data-ttu-id="e721c-143">- eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="e721c-143">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="e721c-144">- eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="e721c-144">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="e721c-145">- eExitProcess</span><span class="sxs-lookup"><span data-stu-id="e721c-145">-   eExitProcess</span></span><br /><span data-ttu-id="e721c-146">- eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="e721c-146">-   eFastExitProcess</span></span><br /><span data-ttu-id="e721c-147">- eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="e721c-147">-   eRudeExitProcess</span></span><br /><span data-ttu-id="e721c-148">- eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="e721c-148">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="e721c-149">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="e721c-149">OPR_AppDomainUnload</span></span>|<span data-ttu-id="e721c-150">- eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="e721c-150">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="e721c-151">- eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="e721c-151">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="e721c-152">- eExitProcess</span><span class="sxs-lookup"><span data-stu-id="e721c-152">-   eExitProcess</span></span><br /><span data-ttu-id="e721c-153">- eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="e721c-153">-   eFastExitProcess</span></span><br /><span data-ttu-id="e721c-154">- eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="e721c-154">-   eRudeExitProcess</span></span><br /><span data-ttu-id="e721c-155">- eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="e721c-155">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="e721c-156">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="e721c-156">OPR_ProcessExit</span></span>|<span data-ttu-id="e721c-157">- eExitProcess</span><span class="sxs-lookup"><span data-stu-id="e721c-157">-   eExitProcess</span></span><br /><span data-ttu-id="e721c-158">- eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="e721c-158">-   eFastExitProcess</span></span><br /><span data-ttu-id="e721c-159">- eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="e721c-159">-   eRudeExitProcess</span></span><br /><span data-ttu-id="e721c-160">- eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="e721c-160">-   eDisableRuntime</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e721c-161">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e721c-161">Requirements</span></span>  

 <span data-ttu-id="e721c-162">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e721c-162">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e721c-163">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e721c-163">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e721c-164">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e721c-164">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e721c-165">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e721c-165">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e721c-166">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e721c-166">See also</span></span>

- [<span data-ttu-id="e721c-167">EClrOperation, énumération</span><span class="sxs-lookup"><span data-stu-id="e721c-167">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="e721c-168">EPolicyAction, énumération</span><span class="sxs-lookup"><span data-stu-id="e721c-168">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="e721c-169">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="e721c-169">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="e721c-170">ICLRPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="e721c-170">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
