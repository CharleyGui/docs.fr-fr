---
title: IHostTaskManager::CallNeedsHostHook, méthode
ms.date: 03/30/2017
api_name:
- IHostTaskManager.CallNeedsHostHook
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::CallNeedsHostHook
helpviewer_keywords:
- CallNeedsHostHook method [.NET Framework hosting]
- IHostTaskManager::CallNeedsHostHook method [.NET Framework hosting]
ms.assetid: b60f1f59-9825-4b57-961f-d2979518e6a7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9a33f71ef2e0b19a33255f3745ac4d5a84cdf4ad
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749743"
---
# <a name="ihosttaskmanagercallneedshosthook-method"></a><span data-ttu-id="a2c00-102">IHostTaskManager::CallNeedsHostHook, méthode</span><span class="sxs-lookup"><span data-stu-id="a2c00-102">IHostTaskManager::CallNeedsHostHook Method</span></span>
<span data-ttu-id="a2c00-103">Permet à l’hôte de spécifier si le common language runtime (CLR) peut inline l’appel spécifié à une fonction non managée.</span><span class="sxs-lookup"><span data-stu-id="a2c00-103">Enables the host to specify whether the common language runtime (CLR) can inline the specified call to an unmanaged function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2c00-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a2c00-104">Syntax</span></span>  
  
```cpp  
HRESULT CallNeedsHostHook (  
    [in]  SIZE_T target,   
    [out] BOOL   *pbCallNeedsHostHook  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2c00-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a2c00-105">Parameters</span></span>  
 `target`  
 <span data-ttu-id="a2c00-106">[in] L’adresse dans le fichier mappé exécutable portable (PE) de la fonction non managée qui doit être appelé.</span><span class="sxs-lookup"><span data-stu-id="a2c00-106">[in] The address within the mapped portable executable (PE) file of the unmanaged function that is to be called.</span></span>  
  
 `pbCallNeedsHostHook`  
 <span data-ttu-id="a2c00-107">[out] Pointeur vers une valeur booléenne qui indique si l’hôte requiert l’appel à être raccordé.</span><span class="sxs-lookup"><span data-stu-id="a2c00-107">[out] A pointer to a Boolean value that indicates whether the host requires the call to be hooked.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a2c00-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="a2c00-108">Return Value</span></span>  
  
|<span data-ttu-id="a2c00-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a2c00-109">HRESULT</span></span>|<span data-ttu-id="a2c00-110">Description</span><span class="sxs-lookup"><span data-stu-id="a2c00-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a2c00-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a2c00-111">S_OK</span></span>|<span data-ttu-id="a2c00-112">`CallNeedsHostHook` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="a2c00-112">`CallNeedsHostHook` returned successfully.</span></span>|  
|<span data-ttu-id="a2c00-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a2c00-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a2c00-114">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="a2c00-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a2c00-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a2c00-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a2c00-116">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="a2c00-116">The call timed out.</span></span>|  
|<span data-ttu-id="a2c00-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a2c00-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a2c00-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="a2c00-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a2c00-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a2c00-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a2c00-120">Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="a2c00-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a2c00-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a2c00-121">E_FAIL</span></span>|<span data-ttu-id="a2c00-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="a2c00-122">An unknown catastrophic failure has occurred.</span></span> <span data-ttu-id="a2c00-123">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus.</span><span class="sxs-lookup"><span data-stu-id="a2c00-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a2c00-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a2c00-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2c00-125">Notes</span><span class="sxs-lookup"><span data-stu-id="a2c00-125">Remarks</span></span>  
 <span data-ttu-id="a2c00-126">Afin d’optimiser l’exécution de code, le CLR effectue une analyse de chaque appel pendant la compilation pour déterminer si l’appel peut être inline.</span><span class="sxs-lookup"><span data-stu-id="a2c00-126">To help optimize code execution, the CLR performs an analysis of each platform invoke call during compilation to determine whether the call can be inlined.</span></span> <span data-ttu-id="a2c00-127">`CallNeedsHostHook` permet à l’hôte de substituer cette décision en exigeant que le raccordement un appel à une fonction non managée.</span><span class="sxs-lookup"><span data-stu-id="a2c00-127">`CallNeedsHostHook` enables the host to override that decision by requiring that a call to an unmanaged function be hooked.</span></span> <span data-ttu-id="a2c00-128">Si l’hôte requiert un raccordement, le runtime n’incorpore pas l’appel.</span><span class="sxs-lookup"><span data-stu-id="a2c00-128">If the host requires a hook, the runtime does not inline the call.</span></span>  
  
 <span data-ttu-id="a2c00-129">L’hôte requiert généralement un raccordement où il doit ajuster un état à virgule flottante, ou lors de la réception de notification qu’un appel entre dans un état où l’hôte ne peut pas suivre les demandes du runtime pour la mémoire ou les verrous pris.</span><span class="sxs-lookup"><span data-stu-id="a2c00-129">The host typically would require a hook where it must adjust a floating-point state, or upon receiving notification that a call is entering a state where the host cannot track the runtime's requests for memory or any locks taken.</span></span> <span data-ttu-id="a2c00-130">Lorsque l’hôte requiert le raccordement de l’appel, le runtime notifie l’hôte des transitions vers et à partir de code managé à l’aide d’appels à [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), [ ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), et [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="a2c00-130">When the host requires that the call be hooked, the runtime notifies the host of transitions to and from managed code by using calls to [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), and [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2c00-131">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a2c00-131">Requirements</span></span>  
 <span data-ttu-id="a2c00-132">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2c00-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2c00-133">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a2c00-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a2c00-134">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a2c00-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a2c00-135">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2c00-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2c00-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a2c00-136">See also</span></span>

- [<span data-ttu-id="a2c00-137">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="a2c00-137">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="a2c00-138">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="a2c00-138">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="a2c00-139">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="a2c00-139">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="a2c00-140">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="a2c00-140">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
