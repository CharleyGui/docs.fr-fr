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
ms.openlocfilehash: 8d987614c1a5a2c90ccb3faa11c605767ae5cfda
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178021"
---
# <a name="ihostpolicymanagerondefaultaction-method"></a><span data-ttu-id="57e6a-102">IHostPolicyManager::OnDefaultAction, méthode</span><span class="sxs-lookup"><span data-stu-id="57e6a-102">IHostPolicyManager::OnDefaultAction Method</span></span>
<span data-ttu-id="57e6a-103">Informe l’animateur que l’heure courante (CLR) est sur le point de prendre l’action par défaut qui a été fixée par un appel <xref:System.AppDomain> à [l’ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) méthode en réponse à un thread abort ou décharger.</span><span class="sxs-lookup"><span data-stu-id="57e6a-103">Notifies the host that the common language runtime (CLR) is about to take the default action that was set by a call to the [ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) method in response to a thread abort or <xref:System.AppDomain> unload.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57e6a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="57e6a-104">Syntax</span></span>  
  
```cpp  
HRESULT OnDefaultAction (  
    [in] EClrOperation  operation,
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57e6a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="57e6a-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="57e6a-106">[dans] L’une des valeurs [EClrOperation,](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) indiquant le genre d’événement auquel le CLR répond.</span><span class="sxs-lookup"><span data-stu-id="57e6a-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the kind of event to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="57e6a-107">[dans] L’une des valeurs [EPolicyAction,](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) indiquant l’action que le CLR prend en réponse à l’événement.</span><span class="sxs-lookup"><span data-stu-id="57e6a-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action that the CLR is taking in response to the event.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="57e6a-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="57e6a-108">Return Value</span></span>  
  
|<span data-ttu-id="57e6a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="57e6a-109">HRESULT</span></span>|<span data-ttu-id="57e6a-110">Description</span><span class="sxs-lookup"><span data-stu-id="57e6a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="57e6a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="57e6a-111">S_OK</span></span>|<span data-ttu-id="57e6a-112">`OnDefaultAction`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="57e6a-112">`OnDefaultAction` returned successfully.</span></span>|  
|<span data-ttu-id="57e6a-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="57e6a-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="57e6a-114">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un état dans lequel il ne peut pas exécuter le code géré ou traiter l’appel.</span><span class="sxs-lookup"><span data-stu-id="57e6a-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="57e6a-115">Réussi</span><span class="sxs-lookup"><span data-stu-id="57e6a-115">successfully</span></span>|  
|<span data-ttu-id="57e6a-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="57e6a-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="57e6a-117">L’appel s’est fait chronométrer.</span><span class="sxs-lookup"><span data-stu-id="57e6a-117">The call timed out.</span></span>|  
|<span data-ttu-id="57e6a-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="57e6a-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="57e6a-119">L’appelant n’est pas propriétaire de la serrure.</span><span class="sxs-lookup"><span data-stu-id="57e6a-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="57e6a-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="57e6a-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="57e6a-121">Un événement a été annulé alors qu’un fil bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="57e6a-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="57e6a-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="57e6a-122">E_FAIL</span></span>|<span data-ttu-id="57e6a-123">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="57e6a-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="57e6a-124">Lorsqu’une méthode revient E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="57e6a-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="57e6a-125">Les appels ultérieurs aux méthodes d’hébergement reviennent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="57e6a-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="57e6a-126">Spécifications</span><span class="sxs-lookup"><span data-stu-id="57e6a-126">Requirements</span></span>  
 <span data-ttu-id="57e6a-127">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57e6a-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57e6a-128">**En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor</span><span class="sxs-lookup"><span data-stu-id="57e6a-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="57e6a-129">**Bibliothèque:** Inclus comme une ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="57e6a-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="57e6a-130">**.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57e6a-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57e6a-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="57e6a-131">See also</span></span>

- [<span data-ttu-id="57e6a-132">EClrOperation, énumération</span><span class="sxs-lookup"><span data-stu-id="57e6a-132">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="57e6a-133">EPolicyAction, énumération</span><span class="sxs-lookup"><span data-stu-id="57e6a-133">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="57e6a-134">ICLRPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="57e6a-134">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="57e6a-135">IHostPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="57e6a-135">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
