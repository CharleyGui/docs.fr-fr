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
ms.openlocfilehash: 727cd82226b9a59c4879ffea5e87f93dd5fe38c9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504106"
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a><span data-ttu-id="cbb57-102">ICLRPolicyManager::SetActionOnFailure, méthode</span><span class="sxs-lookup"><span data-stu-id="cbb57-102">ICLRPolicyManager::SetActionOnFailure Method</span></span>
<span data-ttu-id="cbb57-103">Spécifie l’action de stratégie que le common language runtime (CLR) doit prendre lorsque l’échec spécifié se produit.</span><span class="sxs-lookup"><span data-stu-id="cbb57-103">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbb57-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cbb57-104">Syntax</span></span>  
  
```cpp  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cbb57-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cbb57-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="cbb57-106">dans L’une des valeurs [EClrFailure](eclrfailure-enumeration.md) , indiquant le type d’échec pour lequel agir.</span><span class="sxs-lookup"><span data-stu-id="cbb57-106">[in] One of the [EClrFailure](eclrfailure-enumeration.md) values, indicating the type of failure for which to take action.</span></span>  
  
 `action`  
 <span data-ttu-id="cbb57-107">dans L’une des valeurs [EPolicyAction](epolicyaction-enumeration.md) , indiquant l’action à entreprendre en cas d’échec.</span><span class="sxs-lookup"><span data-stu-id="cbb57-107">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the action to be taken when a failure occurs.</span></span> <span data-ttu-id="cbb57-108">Pour obtenir la liste des valeurs prises en charge, consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="cbb57-108">For a list of supported values, see the Remarks section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cbb57-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="cbb57-109">Return Value</span></span>  
  
|<span data-ttu-id="cbb57-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cbb57-110">HRESULT</span></span>|<span data-ttu-id="cbb57-111">Description</span><span class="sxs-lookup"><span data-stu-id="cbb57-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cbb57-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="cbb57-112">S_OK</span></span>|<span data-ttu-id="cbb57-113">`SetActionOnFailure`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="cbb57-113">`SetActionOnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="cbb57-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cbb57-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cbb57-115">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="cbb57-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cbb57-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cbb57-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cbb57-117">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="cbb57-117">The call timed out.</span></span>|  
|<span data-ttu-id="cbb57-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cbb57-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cbb57-119">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="cbb57-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cbb57-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cbb57-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cbb57-121">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="cbb57-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cbb57-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cbb57-122">E_FAIL</span></span>|<span data-ttu-id="cbb57-123">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="cbb57-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cbb57-124">Une fois que la méthode a retourné E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="cbb57-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cbb57-125">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="cbb57-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="cbb57-126">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="cbb57-126">E_INVALIDARG</span></span>|<span data-ttu-id="cbb57-127">Impossible de définir une action de stratégie pour l’opération spécifiée ou une action de stratégie non valide a été spécifiée pour l’opération.</span><span class="sxs-lookup"><span data-stu-id="cbb57-127">A policy action cannot be set for the specified operation, or an invalid policy action was specified for the operation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cbb57-128">Remarques</span><span class="sxs-lookup"><span data-stu-id="cbb57-128">Remarks</span></span>  
 <span data-ttu-id="cbb57-129">Par défaut, le CLR lève une exception lorsqu’il ne parvient pas à allouer une ressource telle que la mémoire.</span><span class="sxs-lookup"><span data-stu-id="cbb57-129">By default, the CLR throws an exception when it fails to allocate a resource such as memory.</span></span> <span data-ttu-id="cbb57-130">`SetActionOnFailure`permet à l’hôte de substituer ce comportement en spécifiant l’action de stratégie à prendre en cas d’échec.</span><span class="sxs-lookup"><span data-stu-id="cbb57-130">`SetActionOnFailure` allows the host to override this behavior by specifying the policy action to take upon failure.</span></span> <span data-ttu-id="cbb57-131">Le tableau suivant présente les combinaisons de valeurs [EClrFailure](eclrfailure-enumeration.md) et [EPolicyAction](epolicyaction-enumeration.md) qui sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="cbb57-131">The following table shows the combinations of [EClrFailure](eclrfailure-enumeration.md) and [EPolicyAction](epolicyaction-enumeration.md) values that are supported.</span></span> <span data-ttu-id="cbb57-132">(Le préfixe FAIL_ est omis des valeurs [EClrFailure](eclrfailure-enumeration.md) .)</span><span class="sxs-lookup"><span data-stu-id="cbb57-132">(The FAIL_ prefix is omitted from [EClrFailure](eclrfailure-enumeration.md) values.)</span></span>  
  
||<span data-ttu-id="cbb57-133">NonCriticalResource</span><span class="sxs-lookup"><span data-stu-id="cbb57-133">NonCriticalResource</span></span>|<span data-ttu-id="cbb57-134">CriticalResource</span><span class="sxs-lookup"><span data-stu-id="cbb57-134">CriticalResource</span></span>|<span data-ttu-id="cbb57-135">FatalRuntime</span><span class="sxs-lookup"><span data-stu-id="cbb57-135">FatalRuntime</span></span>|<span data-ttu-id="cbb57-136">OrphanedLock</span><span class="sxs-lookup"><span data-stu-id="cbb57-136">OrphanedLock</span></span>|<span data-ttu-id="cbb57-137">Stackoverflow</span><span class="sxs-lookup"><span data-stu-id="cbb57-137">StackOverflow</span></span>|<span data-ttu-id="cbb57-138">AccessViolation</span><span class="sxs-lookup"><span data-stu-id="cbb57-138">AccessViolation</span></span>|<span data-ttu-id="cbb57-139">CodeContract</span><span class="sxs-lookup"><span data-stu-id="cbb57-139">CodeContract</span></span>|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|<span data-ttu-id="cbb57-140">X</span><span class="sxs-lookup"><span data-stu-id="cbb57-140">X</span></span>|<span data-ttu-id="cbb57-141">X</span><span class="sxs-lookup"><span data-stu-id="cbb57-141">X</span></span>||||<span data-ttu-id="cbb57-142">N/A</span><span class="sxs-lookup"><span data-stu-id="cbb57-142">N/A</span></span>||  
|<span data-ttu-id="cbb57-143">eThrowException</span><span class="sxs-lookup"><span data-stu-id="cbb57-143">eThrowException</span></span>|<span data-ttu-id="cbb57-144">X</span><span class="sxs-lookup"><span data-stu-id="cbb57-144">X</span></span>|<span data-ttu-id="cbb57-145">X</span><span class="sxs-lookup"><span data-stu-id="cbb57-145">X</span></span>||||<span data-ttu-id="cbb57-146">N/A</span><span class="sxs-lookup"><span data-stu-id="cbb57-146">N/A</span></span>||  
|`eAbortThread`|<span data-ttu-id="cbb57-147">X</span><span class="sxs-lookup"><span data-stu-id="cbb57-147">X</span></span>|<span data-ttu-id="cbb57-148">X</span><span class="sxs-lookup"><span data-stu-id="cbb57-148">X</span></span>||||<span data-ttu-id="cbb57-149">N/A</span><span class="sxs-lookup"><span data-stu-id="cbb57-149">N/A</span></span>|<span data-ttu-id="cbb57-150">X</span><span class="sxs-lookup"><span data-stu-id="cbb57-150">X</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="cbb57-151">X</span><span class="sxs-lookup"><span data-stu-id="cbb57-151">X</span></span>|<span data-ttu-id="cbb57-152">X</span><span class="sxs-lookup"><span data-stu-id="cbb57-152">X</span></span>||||<span data-ttu-id="cbb57-153">N/A</span><span class="sxs-lookup"><span data-stu-id="cbb57-153">N/A</span></span>|<span data-ttu-id="cbb57-154">X</span><span class="sxs-lookup"><span data-stu-id="cbb57-154">X</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="cbb57-155">X</span><span class="sxs-lookup"><span data-stu-id="cbb57-155">X</span></span>|<span data-ttu-id="cbb57-156">X</span><span class="sxs-lookup"><span data-stu-id="cbb57-156">X</span></span>||<span data-ttu-id="cbb57-157">X</span><span class="sxs-lookup"><span data-stu-id="cbb57-157">X</span></span>||<span data-ttu-id="cbb57-158">N/A</span><span class="sxs-lookup"><span data-stu-id="cbb57-158">N/A</span></span>|<span data-ttu-id="cbb57-159">X</span><span class="sxs-lookup"><span data-stu-id="cbb57-159">X</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="cbb57-160">X</span><span class="sxs-lookup"><span data-stu-id="cbb57-160">X</span></span>|<span data-ttu-id="cbb57-161">X</span><span class="sxs-lookup"><span data-stu-id="cbb57-161">X</span></span>||<span data-ttu-id="cbb57-162">X</span><span class="sxs-lookup"><span data-stu-id="cbb57-162">X</span></span>|<span data-ttu-id="cbb57-163">X</span><span class="sxs-lookup"><span data-stu-id="cbb57-163">X</span></span>|<span data-ttu-id="cbb57-164">N/A</span><span class="sxs-lookup"><span data-stu-id="cbb57-164">N/A</span></span>|<span data-ttu-id="cbb57-165">X</span><span class="sxs-lookup"><span data-stu-id="cbb57-165">X</span></span>|  
|`eExitProcess`|<span data-ttu-id="cbb57-166">X</span><span class="sxs-lookup"><span data-stu-id="cbb57-166">X</span></span>|<span data-ttu-id="cbb57-167">X</span><span class="sxs-lookup"><span data-stu-id="cbb57-167">X</span></span>||<span data-ttu-id="cbb57-168">X</span><span class="sxs-lookup"><span data-stu-id="cbb57-168">X</span></span>|<span data-ttu-id="cbb57-169">X</span><span class="sxs-lookup"><span data-stu-id="cbb57-169">X</span></span>|<span data-ttu-id="cbb57-170">N/A</span><span class="sxs-lookup"><span data-stu-id="cbb57-170">N/A</span></span>|<span data-ttu-id="cbb57-171">X</span><span class="sxs-lookup"><span data-stu-id="cbb57-171">X</span></span>|  
|<span data-ttu-id="cbb57-172">eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="cbb57-172">eFastExitProcess</span></span>|<span data-ttu-id="cbb57-173">X</span><span class="sxs-lookup"><span data-stu-id="cbb57-173">X</span></span>|<span data-ttu-id="cbb57-174">X</span><span class="sxs-lookup"><span data-stu-id="cbb57-174">X</span></span>||<span data-ttu-id="cbb57-175">X</span><span class="sxs-lookup"><span data-stu-id="cbb57-175">X</span></span>|<span data-ttu-id="cbb57-176">X</span><span class="sxs-lookup"><span data-stu-id="cbb57-176">X</span></span>|<span data-ttu-id="cbb57-177">N/A</span><span class="sxs-lookup"><span data-stu-id="cbb57-177">N/A</span></span>||  
|`eRudeExitProcess`|<span data-ttu-id="cbb57-178">X</span><span class="sxs-lookup"><span data-stu-id="cbb57-178">X</span></span>|<span data-ttu-id="cbb57-179">X</span><span class="sxs-lookup"><span data-stu-id="cbb57-179">X</span></span>|<span data-ttu-id="cbb57-180">X</span><span class="sxs-lookup"><span data-stu-id="cbb57-180">X</span></span>|<span data-ttu-id="cbb57-181">X</span><span class="sxs-lookup"><span data-stu-id="cbb57-181">X</span></span>|<span data-ttu-id="cbb57-182">X</span><span class="sxs-lookup"><span data-stu-id="cbb57-182">X</span></span>|<span data-ttu-id="cbb57-183">N/A</span><span class="sxs-lookup"><span data-stu-id="cbb57-183">N/A</span></span>||  
|`eDisableRuntime`|<span data-ttu-id="cbb57-184">X</span><span class="sxs-lookup"><span data-stu-id="cbb57-184">X</span></span>|<span data-ttu-id="cbb57-185">X</span><span class="sxs-lookup"><span data-stu-id="cbb57-185">X</span></span>|<span data-ttu-id="cbb57-186">X</span><span class="sxs-lookup"><span data-stu-id="cbb57-186">X</span></span>|<span data-ttu-id="cbb57-187">X</span><span class="sxs-lookup"><span data-stu-id="cbb57-187">X</span></span>|<span data-ttu-id="cbb57-188">X</span><span class="sxs-lookup"><span data-stu-id="cbb57-188">X</span></span>|<span data-ttu-id="cbb57-189">N/A</span><span class="sxs-lookup"><span data-stu-id="cbb57-189">N/A</span></span>||  
  
## <a name="requirements"></a><span data-ttu-id="cbb57-190">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="cbb57-190">Requirements</span></span>  
 <span data-ttu-id="cbb57-191">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cbb57-191">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbb57-192">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cbb57-192">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cbb57-193">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="cbb57-193">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cbb57-194">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbb57-194">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbb57-195">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cbb57-195">See also</span></span>

- [<span data-ttu-id="cbb57-196">EClrFailure, énumération</span><span class="sxs-lookup"><span data-stu-id="cbb57-196">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="cbb57-197">EPolicyAction, énumération</span><span class="sxs-lookup"><span data-stu-id="cbb57-197">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="cbb57-198">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="cbb57-198">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="cbb57-199">ICLRPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="cbb57-199">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
