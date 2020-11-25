---
title: ICLRPolicyManager::SetDefaultAction, méthode
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetDefaultAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetDefaultAction
helpviewer_keywords:
- SetDefaultAction method [.NET Framework hosting]
- ICLRPolicyManager::SetDefaultAction method [.NET Framework hosting]
ms.assetid: f9411e7a-27df-451f-9f6c-d643d6a7a7ce
topic_type:
- apiref
ms.openlocfilehash: 93070690ea6b30b22949953f1ed0b8c5b1e92764
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732474"
---
# <a name="iclrpolicymanagersetdefaultaction-method"></a><span data-ttu-id="e8faa-102">ICLRPolicyManager::SetDefaultAction, méthode</span><span class="sxs-lookup"><span data-stu-id="e8faa-102">ICLRPolicyManager::SetDefaultAction Method</span></span>

<span data-ttu-id="e8faa-103">Spécifie l’action de stratégie que le common language runtime (CLR) doit prendre lorsque l’opération spécifiée se produit.</span><span class="sxs-lookup"><span data-stu-id="e8faa-103">Specifies the policy action the common language runtime (CLR) should take when the specified operation occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8faa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8faa-104">Syntax</span></span>  
  
```cpp  
HRESULT SetDefaultAction (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8faa-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e8faa-105">Parameters</span></span>  

 `operation`  
 <span data-ttu-id="e8faa-106">dans L’une des valeurs [EClrOperation](eclroperation-enumeration.md) , indiquant l’action pour laquelle le comportement du CLR doit être personnalisé.</span><span class="sxs-lookup"><span data-stu-id="e8faa-106">[in] One of the [EClrOperation](eclroperation-enumeration.md) values, indicating the action for which CLR behavior should be customized.</span></span>  
  
 `action`  
 <span data-ttu-id="e8faa-107">dans L’une des valeurs [EPolicyAction](epolicyaction-enumeration.md) , indiquant l’action de stratégie que le CLR doit prendre lorsqu’il `operation` se produit.</span><span class="sxs-lookup"><span data-stu-id="e8faa-107">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the policy action the CLR should take when `operation` occurs.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e8faa-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="e8faa-108">Return Value</span></span>  
  
|<span data-ttu-id="e8faa-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e8faa-109">HRESULT</span></span>|<span data-ttu-id="e8faa-110">Description</span><span class="sxs-lookup"><span data-stu-id="e8faa-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e8faa-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e8faa-111">S_OK</span></span>|<span data-ttu-id="e8faa-112">`SetDefaultAction` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="e8faa-112">`SetDefaultAction` returned successfully.</span></span>|  
|<span data-ttu-id="e8faa-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e8faa-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e8faa-114">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="e8faa-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e8faa-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e8faa-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e8faa-116">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="e8faa-116">The call timed out.</span></span>|  
|<span data-ttu-id="e8faa-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e8faa-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e8faa-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="e8faa-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e8faa-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e8faa-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e8faa-120">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="e8faa-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e8faa-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e8faa-121">E_FAIL</span></span>|<span data-ttu-id="e8faa-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="e8faa-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e8faa-123">Une fois que la méthode a retourné E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="e8faa-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e8faa-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e8faa-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e8faa-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="e8faa-125">E_INVALIDARG</span></span>|<span data-ttu-id="e8faa-126">Une valeur non valide `action` a été spécifiée pour le `operation` , ou une valeur non valide a été fournie pour `operation` .</span><span class="sxs-lookup"><span data-stu-id="e8faa-126">An invalid `action` was specified for the `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8faa-127">Remarques</span><span class="sxs-lookup"><span data-stu-id="e8faa-127">Remarks</span></span>  

 <span data-ttu-id="e8faa-128">Toutes les valeurs d’action de stratégie ne peuvent pas être spécifiées comme comportement par défaut pour les opérations CLR.</span><span class="sxs-lookup"><span data-stu-id="e8faa-128">Not all policy action values can be specified as the default behavior for CLR operations.</span></span> <span data-ttu-id="e8faa-129">`SetDefaultAction` peut généralement être utilisé uniquement pour faire remonter le comportement.</span><span class="sxs-lookup"><span data-stu-id="e8faa-129">`SetDefaultAction` can typically be used only to escalate behavior.</span></span> <span data-ttu-id="e8faa-130">Par exemple, un hôte peut spécifier que les abandons de thread soient convertis en abandons de thread bruts, mais ne peuvent pas spécifier l’inverse.</span><span class="sxs-lookup"><span data-stu-id="e8faa-130">For example, a host can specify that thread aborts be turned into rude thread aborts, but cannot specify the opposite.</span></span> <span data-ttu-id="e8faa-131">Le tableau ci-dessous décrit les valeurs valides `action` pour chaque `operation` valeur possible.</span><span class="sxs-lookup"><span data-stu-id="e8faa-131">The table below describes the valid `action` values for each possible `operation` value.</span></span>  
  
|<span data-ttu-id="e8faa-132">Valeur pour `operation`</span><span class="sxs-lookup"><span data-stu-id="e8faa-132">Value for `operation`</span></span>|<span data-ttu-id="e8faa-133">Valeurs valides pour `action`</span><span class="sxs-lookup"><span data-stu-id="e8faa-133">Valid values for `action`</span></span>|  
|---------------------------|-------------------------------|  
|<span data-ttu-id="e8faa-134">OPR_ThreadAbort</span><span class="sxs-lookup"><span data-stu-id="e8faa-134">OPR_ThreadAbort</span></span>|<span data-ttu-id="e8faa-135">- eAbortThread</span><span class="sxs-lookup"><span data-stu-id="e8faa-135">-   eAbortThread</span></span><br /><span data-ttu-id="e8faa-136">- eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="e8faa-136">-   eRudeAbortThread</span></span><br /><span data-ttu-id="e8faa-137">- eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="e8faa-137">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="e8faa-138">- eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="e8faa-138">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="e8faa-139">- eExitProcess</span><span class="sxs-lookup"><span data-stu-id="e8faa-139">-   eExitProcess</span></span><br /><span data-ttu-id="e8faa-140">- eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="e8faa-140">-   eFastExitProcess</span></span><br /><span data-ttu-id="e8faa-141">- eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="e8faa-141">-   eRudeExitProcess</span></span><br /><span data-ttu-id="e8faa-142">- eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="e8faa-142">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="e8faa-143">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="e8faa-143">OPR_ThreadRudeAbortInNonCriticalRegion</span></span><br /><br /> <span data-ttu-id="e8faa-144">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="e8faa-144">OPR_ThreadRudeAbortInCriticalRegion</span></span>|<span data-ttu-id="e8faa-145">- eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="e8faa-145">-   eRudeAbortThread</span></span><br /><span data-ttu-id="e8faa-146">- eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="e8faa-146">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="e8faa-147">- eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="e8faa-147">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="e8faa-148">- eExitProcess</span><span class="sxs-lookup"><span data-stu-id="e8faa-148">-   eExitProcess</span></span><br /><span data-ttu-id="e8faa-149">- eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="e8faa-149">-   eFastExitProcess</span></span><br /><span data-ttu-id="e8faa-150">- eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="e8faa-150">-   eRudeExitProcess</span></span><br /><span data-ttu-id="e8faa-151">- eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="e8faa-151">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="e8faa-152">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="e8faa-152">OPR_AppDomainUnload</span></span>|<span data-ttu-id="e8faa-153">- eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="e8faa-153">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="e8faa-154">- eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="e8faa-154">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="e8faa-155">- eExitProcess</span><span class="sxs-lookup"><span data-stu-id="e8faa-155">-   eExitProcess</span></span><br /><span data-ttu-id="e8faa-156">- eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="e8faa-156">-   eFastExitProcess</span></span><br /><span data-ttu-id="e8faa-157">- eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="e8faa-157">-   eRudeExitProcess</span></span><br /><span data-ttu-id="e8faa-158">- eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="e8faa-158">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="e8faa-159">OPR_AppDomainRudeUnload</span><span class="sxs-lookup"><span data-stu-id="e8faa-159">OPR_AppDomainRudeUnload</span></span>|<span data-ttu-id="e8faa-160">- eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="e8faa-160">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="e8faa-161">- eExitProcess</span><span class="sxs-lookup"><span data-stu-id="e8faa-161">-   eExitProcess</span></span><br /><span data-ttu-id="e8faa-162">- eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="e8faa-162">-   eFastExitProcess</span></span><br /><span data-ttu-id="e8faa-163">- eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="e8faa-163">-   eRudeExitProcess</span></span><br /><span data-ttu-id="e8faa-164">- eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="e8faa-164">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="e8faa-165">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="e8faa-165">OPR_ProcessExit</span></span>|<span data-ttu-id="e8faa-166">- eExitProcess</span><span class="sxs-lookup"><span data-stu-id="e8faa-166">-   eExitProcess</span></span><br /><span data-ttu-id="e8faa-167">- eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="e8faa-167">-   eFastExitProcess</span></span><br /><span data-ttu-id="e8faa-168">- eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="e8faa-168">-   eRudeExitProcess</span></span><br /><span data-ttu-id="e8faa-169">- eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="e8faa-169">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="e8faa-170">OPR_FinalizerRun</span><span class="sxs-lookup"><span data-stu-id="e8faa-170">OPR_FinalizerRun</span></span>|<span data-ttu-id="e8faa-171">- eNoAction</span><span class="sxs-lookup"><span data-stu-id="e8faa-171">-   eNoAction</span></span><br /><span data-ttu-id="e8faa-172">- eAbortThread</span><span class="sxs-lookup"><span data-stu-id="e8faa-172">-   eAbortThread</span></span><br /><span data-ttu-id="e8faa-173">- eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="e8faa-173">-   eRudeAbortThread</span></span><br /><span data-ttu-id="e8faa-174">- eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="e8faa-174">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="e8faa-175">- eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="e8faa-175">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="e8faa-176">- eExitProcess</span><span class="sxs-lookup"><span data-stu-id="e8faa-176">-   eExitProcess</span></span><br /><span data-ttu-id="e8faa-177">- eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="e8faa-177">-   eFastExitProcess</span></span><br /><span data-ttu-id="e8faa-178">- eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="e8faa-178">-   eRudeExitProcess</span></span><br /><span data-ttu-id="e8faa-179">- eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="e8faa-179">-   eDisableRuntime</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e8faa-180">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e8faa-180">Requirements</span></span>  

 <span data-ttu-id="e8faa-181">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8faa-181">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8faa-182">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e8faa-182">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e8faa-183">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e8faa-183">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e8faa-184">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8faa-184">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8faa-185">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8faa-185">See also</span></span>

- [<span data-ttu-id="e8faa-186">EClrOperation, énumération</span><span class="sxs-lookup"><span data-stu-id="e8faa-186">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="e8faa-187">EPolicyAction, énumération</span><span class="sxs-lookup"><span data-stu-id="e8faa-187">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="e8faa-188">ICLRPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="e8faa-188">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
