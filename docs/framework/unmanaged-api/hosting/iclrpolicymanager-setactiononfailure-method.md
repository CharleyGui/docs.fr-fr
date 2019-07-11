---
title: ICLRPolicyManager::SetActionOnFailure, méthode
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetActionOnFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetActionOnFailure
helpviewer_keywords:
- SetActionOnFailure method [.NET Framework hosting]
- ICLRPolicyManager::SetActionOnFailure method [.NET Framework hosting]
ms.assetid: 4664033f-db97-4388-b988-2ec470796e58
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 76f064d1683615ef8f665cf1facaa31d61b294a5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759596"
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a><span data-ttu-id="6cf13-102">ICLRPolicyManager::SetActionOnFailure, méthode</span><span class="sxs-lookup"><span data-stu-id="6cf13-102">ICLRPolicyManager::SetActionOnFailure Method</span></span>
<span data-ttu-id="6cf13-103">Spécifie l’action de stratégie que le common language runtime (CLR) doit prendre en cas d’échec spécifié.</span><span class="sxs-lookup"><span data-stu-id="6cf13-103">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cf13-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6cf13-104">Syntax</span></span>  
  
```cpp  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6cf13-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6cf13-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="6cf13-106">[in] Parmi les [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) valeurs indiquant le type d’échec pour lequel effectuer l’action.</span><span class="sxs-lookup"><span data-stu-id="6cf13-106">[in] One of the [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values, indicating the type of failure for which to take action.</span></span>  
  
 `action`  
 <span data-ttu-id="6cf13-107">[in] Parmi les [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) valeurs indiquant l’action à entreprendre lorsqu’une défaillance se produit.</span><span class="sxs-lookup"><span data-stu-id="6cf13-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action to be taken when a failure occurs.</span></span> <span data-ttu-id="6cf13-108">Pour obtenir la liste de valeurs prises en charge, consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="6cf13-108">For a list of supported values, see the Remarks section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6cf13-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="6cf13-109">Return Value</span></span>  
  
|<span data-ttu-id="6cf13-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6cf13-110">HRESULT</span></span>|<span data-ttu-id="6cf13-111">Description</span><span class="sxs-lookup"><span data-stu-id="6cf13-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6cf13-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="6cf13-112">S_OK</span></span>|<span data-ttu-id="6cf13-113">`SetActionOnFailure` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="6cf13-113">`SetActionOnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="6cf13-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6cf13-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6cf13-115">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="6cf13-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6cf13-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6cf13-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6cf13-117">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="6cf13-117">The call timed out.</span></span>|  
|<span data-ttu-id="6cf13-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6cf13-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6cf13-119">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="6cf13-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6cf13-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6cf13-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6cf13-121">Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="6cf13-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6cf13-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6cf13-122">E_FAIL</span></span>|<span data-ttu-id="6cf13-123">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="6cf13-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6cf13-124">Une fois une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus.</span><span class="sxs-lookup"><span data-stu-id="6cf13-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6cf13-125">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6cf13-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6cf13-126">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="6cf13-126">E_INVALIDARG</span></span>|<span data-ttu-id="6cf13-127">Impossible de définir une action de la stratégie pour l’opération spécifiée, ou une action de stratégie non valide a été spécifiée pour l’opération.</span><span class="sxs-lookup"><span data-stu-id="6cf13-127">A policy action cannot be set for the specified operation, or an invalid policy action was specified for the operation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6cf13-128">Notes</span><span class="sxs-lookup"><span data-stu-id="6cf13-128">Remarks</span></span>  
 <span data-ttu-id="6cf13-129">Par défaut, le CLR lève une exception lorsqu’il ne peut pas allouer une ressource, telles que la mémoire.</span><span class="sxs-lookup"><span data-stu-id="6cf13-129">By default, the CLR throws an exception when it fails to allocate a resource such as memory.</span></span> <span data-ttu-id="6cf13-130">`SetActionOnFailure` permet à l’hôte de substituer ce comportement en spécifiant l’action de la stratégie à appliquer en cas d’échec.</span><span class="sxs-lookup"><span data-stu-id="6cf13-130">`SetActionOnFailure` allows the host to override this behavior by specifying the policy action to take upon failure.</span></span> <span data-ttu-id="6cf13-131">Le tableau suivant montre les combinaisons de [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) et [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) valeurs qui sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="6cf13-131">The following table shows the combinations of [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) and [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values that are supported.</span></span> <span data-ttu-id="6cf13-132">(Le préfixe FAIL_ est omis du [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) valeurs.)</span><span class="sxs-lookup"><span data-stu-id="6cf13-132">(The FAIL_ prefix is omitted from [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values.)</span></span>  
  
||<span data-ttu-id="6cf13-133">NonCriticalResource</span><span class="sxs-lookup"><span data-stu-id="6cf13-133">NonCriticalResource</span></span>|<span data-ttu-id="6cf13-134">CriticalResource</span><span class="sxs-lookup"><span data-stu-id="6cf13-134">CriticalResource</span></span>|<span data-ttu-id="6cf13-135">FatalRuntime</span><span class="sxs-lookup"><span data-stu-id="6cf13-135">FatalRuntime</span></span>|<span data-ttu-id="6cf13-136">OrphanedLock</span><span class="sxs-lookup"><span data-stu-id="6cf13-136">OrphanedLock</span></span>|<span data-ttu-id="6cf13-137">StackOverflow</span><span class="sxs-lookup"><span data-stu-id="6cf13-137">StackOverflow</span></span>|<span data-ttu-id="6cf13-138">AccessViolation</span><span class="sxs-lookup"><span data-stu-id="6cf13-138">AccessViolation</span></span>|<span data-ttu-id="6cf13-139">CodeContract</span><span class="sxs-lookup"><span data-stu-id="6cf13-139">CodeContract</span></span>|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|<span data-ttu-id="6cf13-140">X</span><span class="sxs-lookup"><span data-stu-id="6cf13-140">X</span></span>|<span data-ttu-id="6cf13-141">X</span><span class="sxs-lookup"><span data-stu-id="6cf13-141">X</span></span>||||<span data-ttu-id="6cf13-142">N/A</span><span class="sxs-lookup"><span data-stu-id="6cf13-142">N/A</span></span>||  
|<span data-ttu-id="6cf13-143">eThrowException</span><span class="sxs-lookup"><span data-stu-id="6cf13-143">eThrowException</span></span>|<span data-ttu-id="6cf13-144">X</span><span class="sxs-lookup"><span data-stu-id="6cf13-144">X</span></span>|<span data-ttu-id="6cf13-145">X</span><span class="sxs-lookup"><span data-stu-id="6cf13-145">X</span></span>||||<span data-ttu-id="6cf13-146">N/A</span><span class="sxs-lookup"><span data-stu-id="6cf13-146">N/A</span></span>||  
|`eAbortThread`|<span data-ttu-id="6cf13-147">X</span><span class="sxs-lookup"><span data-stu-id="6cf13-147">X</span></span>|<span data-ttu-id="6cf13-148">X</span><span class="sxs-lookup"><span data-stu-id="6cf13-148">X</span></span>||||<span data-ttu-id="6cf13-149">N/A</span><span class="sxs-lookup"><span data-stu-id="6cf13-149">N/A</span></span>|<span data-ttu-id="6cf13-150">X</span><span class="sxs-lookup"><span data-stu-id="6cf13-150">X</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="6cf13-151">X</span><span class="sxs-lookup"><span data-stu-id="6cf13-151">X</span></span>|<span data-ttu-id="6cf13-152">X</span><span class="sxs-lookup"><span data-stu-id="6cf13-152">X</span></span>||||<span data-ttu-id="6cf13-153">N/A</span><span class="sxs-lookup"><span data-stu-id="6cf13-153">N/A</span></span>|<span data-ttu-id="6cf13-154">X</span><span class="sxs-lookup"><span data-stu-id="6cf13-154">X</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="6cf13-155">X</span><span class="sxs-lookup"><span data-stu-id="6cf13-155">X</span></span>|<span data-ttu-id="6cf13-156">X</span><span class="sxs-lookup"><span data-stu-id="6cf13-156">X</span></span>||<span data-ttu-id="6cf13-157">X</span><span class="sxs-lookup"><span data-stu-id="6cf13-157">X</span></span>||<span data-ttu-id="6cf13-158">N/A</span><span class="sxs-lookup"><span data-stu-id="6cf13-158">N/A</span></span>|<span data-ttu-id="6cf13-159">X</span><span class="sxs-lookup"><span data-stu-id="6cf13-159">X</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="6cf13-160">X</span><span class="sxs-lookup"><span data-stu-id="6cf13-160">X</span></span>|<span data-ttu-id="6cf13-161">X</span><span class="sxs-lookup"><span data-stu-id="6cf13-161">X</span></span>||<span data-ttu-id="6cf13-162">X</span><span class="sxs-lookup"><span data-stu-id="6cf13-162">X</span></span>|<span data-ttu-id="6cf13-163">X</span><span class="sxs-lookup"><span data-stu-id="6cf13-163">X</span></span>|<span data-ttu-id="6cf13-164">N/A</span><span class="sxs-lookup"><span data-stu-id="6cf13-164">N/A</span></span>|<span data-ttu-id="6cf13-165">X</span><span class="sxs-lookup"><span data-stu-id="6cf13-165">X</span></span>|  
|`eExitProcess`|<span data-ttu-id="6cf13-166">X</span><span class="sxs-lookup"><span data-stu-id="6cf13-166">X</span></span>|<span data-ttu-id="6cf13-167">X</span><span class="sxs-lookup"><span data-stu-id="6cf13-167">X</span></span>||<span data-ttu-id="6cf13-168">X</span><span class="sxs-lookup"><span data-stu-id="6cf13-168">X</span></span>|<span data-ttu-id="6cf13-169">X</span><span class="sxs-lookup"><span data-stu-id="6cf13-169">X</span></span>|<span data-ttu-id="6cf13-170">N/A</span><span class="sxs-lookup"><span data-stu-id="6cf13-170">N/A</span></span>|<span data-ttu-id="6cf13-171">X</span><span class="sxs-lookup"><span data-stu-id="6cf13-171">X</span></span>|  
|<span data-ttu-id="6cf13-172">eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="6cf13-172">eFastExitProcess</span></span>|<span data-ttu-id="6cf13-173">X</span><span class="sxs-lookup"><span data-stu-id="6cf13-173">X</span></span>|<span data-ttu-id="6cf13-174">X</span><span class="sxs-lookup"><span data-stu-id="6cf13-174">X</span></span>||<span data-ttu-id="6cf13-175">X</span><span class="sxs-lookup"><span data-stu-id="6cf13-175">X</span></span>|<span data-ttu-id="6cf13-176">X</span><span class="sxs-lookup"><span data-stu-id="6cf13-176">X</span></span>|<span data-ttu-id="6cf13-177">N/A</span><span class="sxs-lookup"><span data-stu-id="6cf13-177">N/A</span></span>||  
|`eRudeExitProcess`|<span data-ttu-id="6cf13-178">X</span><span class="sxs-lookup"><span data-stu-id="6cf13-178">X</span></span>|<span data-ttu-id="6cf13-179">X</span><span class="sxs-lookup"><span data-stu-id="6cf13-179">X</span></span>|<span data-ttu-id="6cf13-180">X</span><span class="sxs-lookup"><span data-stu-id="6cf13-180">X</span></span>|<span data-ttu-id="6cf13-181">X</span><span class="sxs-lookup"><span data-stu-id="6cf13-181">X</span></span>|<span data-ttu-id="6cf13-182">X</span><span class="sxs-lookup"><span data-stu-id="6cf13-182">X</span></span>|<span data-ttu-id="6cf13-183">N/A</span><span class="sxs-lookup"><span data-stu-id="6cf13-183">N/A</span></span>||  
|`eDisableRuntime`|<span data-ttu-id="6cf13-184">X</span><span class="sxs-lookup"><span data-stu-id="6cf13-184">X</span></span>|<span data-ttu-id="6cf13-185">X</span><span class="sxs-lookup"><span data-stu-id="6cf13-185">X</span></span>|<span data-ttu-id="6cf13-186">X</span><span class="sxs-lookup"><span data-stu-id="6cf13-186">X</span></span>|<span data-ttu-id="6cf13-187">X</span><span class="sxs-lookup"><span data-stu-id="6cf13-187">X</span></span>|<span data-ttu-id="6cf13-188">X</span><span class="sxs-lookup"><span data-stu-id="6cf13-188">X</span></span>|<span data-ttu-id="6cf13-189">N/A</span><span class="sxs-lookup"><span data-stu-id="6cf13-189">N/A</span></span>||  
  
## <a name="requirements"></a><span data-ttu-id="6cf13-190">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6cf13-190">Requirements</span></span>  
 <span data-ttu-id="6cf13-191">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6cf13-191">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cf13-192">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6cf13-192">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6cf13-193">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6cf13-193">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6cf13-194">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cf13-194">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cf13-195">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6cf13-195">See also</span></span>

- [<span data-ttu-id="6cf13-196">EClrFailure, énumération</span><span class="sxs-lookup"><span data-stu-id="6cf13-196">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="6cf13-197">EPolicyAction, énumération</span><span class="sxs-lookup"><span data-stu-id="6cf13-197">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="6cf13-198">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="6cf13-198">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="6cf13-199">ICLRPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="6cf13-199">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
