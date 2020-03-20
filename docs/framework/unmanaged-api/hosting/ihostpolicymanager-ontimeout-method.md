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
ms.openlocfilehash: d5b5fa5198ae2c0bba30ae0f8d6d3834f2891672
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178006"
---
# <a name="ihostpolicymanagerontimeout-method"></a><span data-ttu-id="d82a4-102">IHostPolicyManager::OnTimeout, méthode</span><span class="sxs-lookup"><span data-stu-id="d82a4-102">IHostPolicyManager::OnTimeout Method</span></span>
<span data-ttu-id="d82a4-103">Informe l’hôte que l’heure courante (CLR) est sur le point de prendre l’action spécifiée par un appel à [l’ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) méthode en réponse à un délai d’attente.</span><span class="sxs-lookup"><span data-stu-id="d82a4-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) method in response to a timeout.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d82a4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d82a4-104">Syntax</span></span>  
  
```cpp  
HRESULT OnTimeout (  
    [in] EClrOperation  operation,
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d82a4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d82a4-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="d82a4-106">[dans] L’une des valeurs [EClrOperation,](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) indiquant le type d’opération qui a été chronométrée.</span><span class="sxs-lookup"><span data-stu-id="d82a4-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the kind of operation that timed out.</span></span>  
  
 `action`  
 <span data-ttu-id="d82a4-107">[dans] L’une des valeurs [ePolicyAction,](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) indiquant l’action que prend le CLR en réponse au délai d’attente.</span><span class="sxs-lookup"><span data-stu-id="d82a4-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to the timeout.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d82a4-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d82a4-108">Return Value</span></span>  
  
|<span data-ttu-id="d82a4-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d82a4-109">HRESULT</span></span>|<span data-ttu-id="d82a4-110">Description</span><span class="sxs-lookup"><span data-stu-id="d82a4-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d82a4-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d82a4-111">S_OK</span></span>|<span data-ttu-id="d82a4-112">`OnTimeout`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="d82a4-112">`OnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="d82a4-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d82a4-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d82a4-114">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un état dans lequel il ne peut pas exécuter le code géré ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="d82a4-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d82a4-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d82a4-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d82a4-116">L’appel s’est fait chronométrer.</span><span class="sxs-lookup"><span data-stu-id="d82a4-116">The call timed out.</span></span>|  
|<span data-ttu-id="d82a4-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d82a4-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d82a4-118">L’appelant n’est pas propriétaire de la serrure.</span><span class="sxs-lookup"><span data-stu-id="d82a4-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d82a4-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d82a4-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d82a4-120">Un événement a été annulé alors qu’un fil bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="d82a4-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d82a4-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d82a4-121">E_FAIL</span></span>|<span data-ttu-id="d82a4-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="d82a4-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d82a4-123">Lorsqu’une méthode revient E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="d82a4-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d82a4-124">Les appels ultérieurs aux méthodes d’hébergement reviennent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d82a4-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d82a4-125">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d82a4-125">Requirements</span></span>  
 <span data-ttu-id="d82a4-126">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d82a4-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d82a4-127">**En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor</span><span class="sxs-lookup"><span data-stu-id="d82a4-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d82a4-128">**Bibliothèque:** Inclus comme une ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d82a4-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d82a4-129">**.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d82a4-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d82a4-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d82a4-130">See also</span></span>

- [<span data-ttu-id="d82a4-131">EClrOperation, énumération</span><span class="sxs-lookup"><span data-stu-id="d82a4-131">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="d82a4-132">EPolicyAction, énumération</span><span class="sxs-lookup"><span data-stu-id="d82a4-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="d82a4-133">ICLRPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="d82a4-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="d82a4-134">IHostPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="d82a4-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
