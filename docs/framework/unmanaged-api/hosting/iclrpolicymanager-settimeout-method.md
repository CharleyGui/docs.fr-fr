---
title: ICLRPolicyManager::SetTimeout, méthode
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetTimeout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetTimeout
helpviewer_keywords:
- SetTimeout method [.NET Framework hosting]
- ICLRPolicyManager::SetTimeout method [.NET Framework hosting]
ms.assetid: 954404fd-d52d-4e68-b582-8692f3a5f608
topic_type:
- apiref
ms.openlocfilehash: 516ba1325404e757af8e38de239864b21b1640f1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140749"
---
# <a name="iclrpolicymanagersettimeout-method"></a><span data-ttu-id="208b8-102">ICLRPolicyManager::SetTimeout, méthode</span><span class="sxs-lookup"><span data-stu-id="208b8-102">ICLRPolicyManager::SetTimeout Method</span></span>
<span data-ttu-id="208b8-103">Définit une valeur de délai d’attente pour l’opération spécifiée.</span><span class="sxs-lookup"><span data-stu-id="208b8-103">Sets a timeout value for the specified operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="208b8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="208b8-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTimeout (  
    [in] EClrOperation operation,  
    [in] DWORD dsMilliseconds  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="208b8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="208b8-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="208b8-106">dans L’une des valeurs [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) , indiquant l’opération de Common Language Runtime (CLR) pour laquelle définir un délai d’attente.</span><span class="sxs-lookup"><span data-stu-id="208b8-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the common language runtime (CLR) operation for which to set a timeout.</span></span> <span data-ttu-id="208b8-107">Les valeurs suivantes sont prises en charge :</span><span class="sxs-lookup"><span data-stu-id="208b8-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="208b8-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="208b8-108">OPR_AppDomainUnload</span></span>  
  
- <span data-ttu-id="208b8-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="208b8-109">OPR_ProcessExit</span></span>  
  
- <span data-ttu-id="208b8-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="208b8-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
- <span data-ttu-id="208b8-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="208b8-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="208b8-112">dans Nouvelle valeur du délai d’attente, en millisecondes.</span><span class="sxs-lookup"><span data-stu-id="208b8-112">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="208b8-113">Si la valeur est Infinite, l’opération n’expire jamais.</span><span class="sxs-lookup"><span data-stu-id="208b8-113">A value of INFINITE causes the operation never to time out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="208b8-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="208b8-114">Return Value</span></span>  
  
|<span data-ttu-id="208b8-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="208b8-115">HRESULT</span></span>|<span data-ttu-id="208b8-116">Description</span><span class="sxs-lookup"><span data-stu-id="208b8-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="208b8-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="208b8-117">S_OK</span></span>|<span data-ttu-id="208b8-118">`SetTimeout` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="208b8-118">`SetTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="208b8-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="208b8-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="208b8-120">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="208b8-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="208b8-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="208b8-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="208b8-122">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="208b8-122">The call timed out.</span></span>|  
|<span data-ttu-id="208b8-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="208b8-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="208b8-124">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="208b8-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="208b8-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="208b8-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="208b8-126">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="208b8-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="208b8-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="208b8-127">E_FAIL</span></span>|<span data-ttu-id="208b8-128">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="208b8-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="208b8-129">Une fois qu’une méthode a retourné E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="208b8-129">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="208b8-130">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="208b8-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="208b8-131">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="208b8-131">E_INVALIDARG</span></span>|<span data-ttu-id="208b8-132">Un délai d’expiration ne peut pas être défini pour la `operation`spécifiée, ou une valeur non valide a été fournie pour `operation`.</span><span class="sxs-lookup"><span data-stu-id="208b8-132">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="208b8-133">spécifications</span><span class="sxs-lookup"><span data-stu-id="208b8-133">Requirements</span></span>  
 <span data-ttu-id="208b8-134">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="208b8-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="208b8-135">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="208b8-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="208b8-136">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="208b8-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="208b8-137">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="208b8-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="208b8-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="208b8-138">See also</span></span>

- [<span data-ttu-id="208b8-139">EClrOperation, énumération</span><span class="sxs-lookup"><span data-stu-id="208b8-139">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="208b8-140">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="208b8-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="208b8-141">ICLRPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="208b8-141">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
