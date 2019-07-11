---
title: IHostPolicyManager::OnTimeout, méthode
ms.date: 03/30/2017
api_name:
- IHostPolicyManager.OnTimeout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager::OnTimeout
helpviewer_keywords:
- IHostPolicyManager::OnTimeout method [.NET Framework hosting]
- OnTimeout method [.NET Framework hosting]
ms.assetid: 0a313b51-5e4d-4714-a86b-af75cf3902e6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 75e6ff3b2b7c8f4b8611630092203aace0ce3136
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781020"
---
# <a name="ihostpolicymanagerontimeout-method"></a><span data-ttu-id="f0583-102">IHostPolicyManager::OnTimeout, méthode</span><span class="sxs-lookup"><span data-stu-id="f0583-102">IHostPolicyManager::OnTimeout Method</span></span>
<span data-ttu-id="f0583-103">Avertit l’hôte que le common language runtime (CLR) est sur le point d’effectuer l’action spécifiée par un appel à la [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) méthode en réponse à un délai d’expiration.</span><span class="sxs-lookup"><span data-stu-id="f0583-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) method in response to a timeout.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0583-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f0583-104">Syntax</span></span>  
  
```cpp  
HRESULT OnTimeout (  
    [in] EClrOperation  operation,   
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0583-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f0583-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="f0583-106">[in] Parmi les [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) valeurs indiquant le genre d’opération qui a expiré.</span><span class="sxs-lookup"><span data-stu-id="f0583-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the kind of operation that timed out.</span></span>  
  
 `action`  
 <span data-ttu-id="f0583-107">[in] Parmi les [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) valeurs, indiquant l’action, le CLR effectue en réponse au délai d’attente.</span><span class="sxs-lookup"><span data-stu-id="f0583-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to the timeout.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f0583-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f0583-108">Return Value</span></span>  
  
|<span data-ttu-id="f0583-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f0583-109">HRESULT</span></span>|<span data-ttu-id="f0583-110">Description</span><span class="sxs-lookup"><span data-stu-id="f0583-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f0583-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f0583-111">S_OK</span></span>|<span data-ttu-id="f0583-112">`OnTimeout` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="f0583-112">`OnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="f0583-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f0583-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f0583-114">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="f0583-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f0583-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f0583-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f0583-116">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="f0583-116">The call timed out.</span></span>|  
|<span data-ttu-id="f0583-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f0583-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f0583-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="f0583-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f0583-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f0583-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f0583-120">Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="f0583-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f0583-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f0583-121">E_FAIL</span></span>|<span data-ttu-id="f0583-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="f0583-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f0583-123">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus.</span><span class="sxs-lookup"><span data-stu-id="f0583-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f0583-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f0583-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f0583-125">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f0583-125">Requirements</span></span>  
 <span data-ttu-id="f0583-126">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0583-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0583-127">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f0583-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f0583-128">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f0583-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f0583-129">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0583-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0583-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f0583-130">See also</span></span>

- [<span data-ttu-id="f0583-131">EClrOperation, énumération</span><span class="sxs-lookup"><span data-stu-id="f0583-131">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="f0583-132">EPolicyAction, énumération</span><span class="sxs-lookup"><span data-stu-id="f0583-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="f0583-133">ICLRPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="f0583-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="f0583-134">IHostPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="f0583-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
