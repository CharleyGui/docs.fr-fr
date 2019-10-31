---
title: IHostPolicyManager::OnDefaultAction, méthode
ms.date: 03/30/2017
api_name:
- IHostPolicyManager.OnDefaultAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager::OnDefaultAction
helpviewer_keywords:
- OnDefaultAction method [.NET Framework hosting]
- IHostPolicyManager::OnDefaultAction method [.NET Framework hosting]
ms.assetid: 071e73bd-4795-470f-9373-cfaef553b7f2
topic_type:
- apiref
ms.openlocfilehash: cdf0a720ac440d156b5b8bdc8dc2c78d3bb5ba86
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128561"
---
# <a name="ihostpolicymanagerondefaultaction-method"></a><span data-ttu-id="6288f-102">IHostPolicyManager::OnDefaultAction, méthode</span><span class="sxs-lookup"><span data-stu-id="6288f-102">IHostPolicyManager::OnDefaultAction Method</span></span>
<span data-ttu-id="6288f-103">Avertit l’hôte que le common language runtime (CLR) est sur le point d’exécuter l’action par défaut qui a été définie par un appel à la méthode [ICLRPolicyManager :: SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) en réponse à une interruption de thread ou à un déchargement de <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="6288f-103">Notifies the host that the common language runtime (CLR) is about to take the default action that was set by a call to the [ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) method in response to a thread abort or <xref:System.AppDomain> unload.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6288f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6288f-104">Syntax</span></span>  
  
```cpp  
HRESULT OnDefaultAction (  
    [in] EClrOperation  operation,   
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6288f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6288f-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="6288f-106">dans L’une des valeurs [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) , indiquant le type d’événement auquel le CLR répond.</span><span class="sxs-lookup"><span data-stu-id="6288f-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the kind of event to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="6288f-107">dans L’une des valeurs [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) , indiquant l’action que le CLR prend en réponse à l’événement.</span><span class="sxs-lookup"><span data-stu-id="6288f-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action that the CLR is taking in response to the event.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6288f-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="6288f-108">Return Value</span></span>  
  
|<span data-ttu-id="6288f-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6288f-109">HRESULT</span></span>|<span data-ttu-id="6288f-110">Description</span><span class="sxs-lookup"><span data-stu-id="6288f-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6288f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="6288f-111">S_OK</span></span>|<span data-ttu-id="6288f-112">`OnDefaultAction` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="6288f-112">`OnDefaultAction` returned successfully.</span></span>|  
|<span data-ttu-id="6288f-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6288f-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6288f-114">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter l’appel.</span><span class="sxs-lookup"><span data-stu-id="6288f-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="6288f-115">correctement</span><span class="sxs-lookup"><span data-stu-id="6288f-115">successfully</span></span>|  
|<span data-ttu-id="6288f-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6288f-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6288f-117">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="6288f-117">The call timed out.</span></span>|  
|<span data-ttu-id="6288f-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6288f-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6288f-119">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="6288f-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6288f-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6288f-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6288f-121">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="6288f-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6288f-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6288f-122">E_FAIL</span></span>|<span data-ttu-id="6288f-123">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="6288f-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6288f-124">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="6288f-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6288f-125">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6288f-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6288f-126">spécifications</span><span class="sxs-lookup"><span data-stu-id="6288f-126">Requirements</span></span>  
 <span data-ttu-id="6288f-127">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6288f-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6288f-128">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6288f-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6288f-129">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6288f-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6288f-130">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6288f-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6288f-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6288f-131">See also</span></span>

- [<span data-ttu-id="6288f-132">EClrOperation, énumération</span><span class="sxs-lookup"><span data-stu-id="6288f-132">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="6288f-133">EPolicyAction, énumération</span><span class="sxs-lookup"><span data-stu-id="6288f-133">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="6288f-134">ICLRPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="6288f-134">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="6288f-135">IHostPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="6288f-135">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
