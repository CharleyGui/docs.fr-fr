---
title: ICLRPolicyManager::SetTimeoutAndAction, méthode
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetTimeoutAndAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetTimeoutAndAction
helpviewer_keywords:
- ICLRPolicyManager::SetTimeoutAndAction method [.NET Framework hosting]
- SetTimeoutAndAction method [.NET Framework hosting]
ms.assetid: 60454f91-d855-4ddf-bb6d-60a02f5eabab
topic_type:
- apiref
ms.openlocfilehash: efd30ef04c148d5e098110efcb37e50f143884e4
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703425"
---
# <a name="iclrpolicymanagersettimeoutandaction-method"></a><span data-ttu-id="c5d7c-102">ICLRPolicyManager::SetTimeoutAndAction, méthode</span><span class="sxs-lookup"><span data-stu-id="c5d7c-102">ICLRPolicyManager::SetTimeoutAndAction Method</span></span>
<span data-ttu-id="c5d7c-103">Définit une valeur de délai d’attente pour l’opération spécifiée et spécifie l’action de stratégie que le common language runtime (CLR) doit prendre lorsque l’opération se produit.</span><span class="sxs-lookup"><span data-stu-id="c5d7c-103">Sets a timeout value for the specified operation, and specifies the policy action the common language runtime (CLR) should take when the operation occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5d7c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c5d7c-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTimeoutAndAction (  
    [in] EClrOperation operation,  
    [in] DWORD dwMilliseconds,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5d7c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c5d7c-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="c5d7c-106">dans L’une des valeurs [EClrOperation](eclroperation-enumeration.md) , indiquant l’opération pour laquelle définir le délai d’attente et la stratégie `action` .</span><span class="sxs-lookup"><span data-stu-id="c5d7c-106">[in] One of the [EClrOperation](eclroperation-enumeration.md) values, indicating the operation for which to set the timeout and policy `action`.</span></span> <span data-ttu-id="c5d7c-107">Les valeurs suivantes sont admises :</span><span class="sxs-lookup"><span data-stu-id="c5d7c-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="c5d7c-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="c5d7c-108">OPR_AppDomainUnload</span></span>  
  
- <span data-ttu-id="c5d7c-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="c5d7c-109">OPR_ProcessExit</span></span>  
  
- <span data-ttu-id="c5d7c-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="c5d7c-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
- <span data-ttu-id="c5d7c-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="c5d7c-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="c5d7c-112">dans Nouvelle valeur du délai d’attente, en millisecondes.</span><span class="sxs-lookup"><span data-stu-id="c5d7c-112">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="c5d7c-113">Si la valeur est Infinite, le `operation` délai d’attente n’est jamais dépassé.</span><span class="sxs-lookup"><span data-stu-id="c5d7c-113">A value of INFINITE causes `operation` never to time out.</span></span>  
  
 `action`  
 <span data-ttu-id="c5d7c-114">dans L’une des valeurs [EPolicyAction](epolicyaction-enumeration.md) , indiquant l’action de stratégie que le CLR doit prendre lorsqu’il `operation` se produit.</span><span class="sxs-lookup"><span data-stu-id="c5d7c-114">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the policy action that the CLR should take when `operation` occurs.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c5d7c-115">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c5d7c-115">Return Value</span></span>  
  
|<span data-ttu-id="c5d7c-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c5d7c-116">HRESULT</span></span>|<span data-ttu-id="c5d7c-117">Description</span><span class="sxs-lookup"><span data-stu-id="c5d7c-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c5d7c-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="c5d7c-118">S_OK</span></span>|<span data-ttu-id="c5d7c-119">`SetTimeoutAndAction`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="c5d7c-119">`SetTimeoutAndAction` returned successfully.</span></span>|  
|<span data-ttu-id="c5d7c-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c5d7c-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c5d7c-121">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="c5d7c-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c5d7c-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c5d7c-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c5d7c-123">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="c5d7c-123">The call timed out.</span></span>|  
|<span data-ttu-id="c5d7c-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c5d7c-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c5d7c-125">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="c5d7c-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c5d7c-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c5d7c-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c5d7c-127">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="c5d7c-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c5d7c-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c5d7c-128">E_FAIL</span></span>|<span data-ttu-id="c5d7c-129">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="c5d7c-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c5d7c-130">Une fois que la méthode a retourné E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="c5d7c-130">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c5d7c-131">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c5d7c-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c5d7c-132">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c5d7c-132">E_INVALIDARG</span></span>|<span data-ttu-id="c5d7c-133">Un délai d’expiration ne peut pas être défini pour le spécifié `operation` , ou une valeur non valide a été fournie pour `action` .</span><span class="sxs-lookup"><span data-stu-id="c5d7c-133">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `action`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5d7c-134">Notes</span><span class="sxs-lookup"><span data-stu-id="c5d7c-134">Remarks</span></span>  
 <span data-ttu-id="c5d7c-135">`SetTimeoutAndAction`encapsule les fonctionnalités des méthodes [ICLRPolicyManager :: setTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) et [ICLRPolicyManager :: SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) , et peut être appelée à la place des appels séquentiels à ces deux méthodes.</span><span class="sxs-lookup"><span data-stu-id="c5d7c-135">`SetTimeoutAndAction` encapsulates the capabilities of the [ICLRPolicyManager::SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) and [ICLRPolicyManager::SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) methods, and can be called in place of sequential calls to these two methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c5d7c-136">Toutes les valeurs d’action de stratégie ne peuvent pas être spécifiées comme le comportement de délai d’attente pour les opérations CLR.</span><span class="sxs-lookup"><span data-stu-id="c5d7c-136">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="c5d7c-137">Consultez les sections notes des rubriques relatives à ces deux méthodes pour connaître les valeurs valides.</span><span class="sxs-lookup"><span data-stu-id="c5d7c-137">See the Remarks sections of the topics for these two methods for valid values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5d7c-138">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="c5d7c-138">Requirements</span></span>  
 <span data-ttu-id="c5d7c-139">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5d7c-139">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5d7c-140">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c5d7c-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c5d7c-141">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c5d7c-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c5d7c-142">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5d7c-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5d7c-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c5d7c-143">See also</span></span>

- [<span data-ttu-id="c5d7c-144">EClrOperation, énumération</span><span class="sxs-lookup"><span data-stu-id="c5d7c-144">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="c5d7c-145">EPolicyAction, énumération</span><span class="sxs-lookup"><span data-stu-id="c5d7c-145">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="c5d7c-146">ICLRPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="c5d7c-146">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="c5d7c-147">SetActionOnTimeout, méthode</span><span class="sxs-lookup"><span data-stu-id="c5d7c-147">SetActionOnTimeout Method</span></span>](iclrpolicymanager-setactionontimeout-method.md)
- [<span data-ttu-id="c5d7c-148">ICLRPolicyManager :: SetTimeoutAndAction,</span><span class="sxs-lookup"><span data-stu-id="c5d7c-148">ICLRPolicyManager::SetTimeoutAndAction</span></span>](iclrpolicymanager-settimeoutandaction-method.md)
