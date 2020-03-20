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
ms.openlocfilehash: 8b8b8521a09fa54a105e8263a471ab0467fb6ccc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176290"
---
# <a name="ihosttaskmanagercallneedshosthook-method"></a><span data-ttu-id="43715-102">IHostTaskManager::CallNeedsHostHook, méthode</span><span class="sxs-lookup"><span data-stu-id="43715-102">IHostTaskManager::CallNeedsHostHook Method</span></span>
<span data-ttu-id="43715-103">Permet à l’hôte de spécifier si l’heure de fonctionnement de la langue commune (CLR) peut inlimiter l’appel spécifié à une fonction non gérée.</span><span class="sxs-lookup"><span data-stu-id="43715-103">Enables the host to specify whether the common language runtime (CLR) can inline the specified call to an unmanaged function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43715-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43715-104">Syntax</span></span>  
  
```cpp  
HRESULT CallNeedsHostHook (  
    [in]  SIZE_T target,
    [out] BOOL   *pbCallNeedsHostHook  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="43715-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="43715-105">Parameters</span></span>  
 `target`  
 <span data-ttu-id="43715-106">[dans] L’adresse dans le fichier portable cartographié exécutable (PE) de la fonction non gestion qui doit être appelée.</span><span class="sxs-lookup"><span data-stu-id="43715-106">[in] The address within the mapped portable executable (PE) file of the unmanaged function that is to be called.</span></span>  
  
 `pbCallNeedsHostHook`  
 <span data-ttu-id="43715-107">[out] Un pointeur à une valeur Boolean qui indique si l’hôte nécessite l’appel pour être accroché.</span><span class="sxs-lookup"><span data-stu-id="43715-107">[out] A pointer to a Boolean value that indicates whether the host requires the call to be hooked.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="43715-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="43715-108">Return Value</span></span>  
  
|<span data-ttu-id="43715-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="43715-109">HRESULT</span></span>|<span data-ttu-id="43715-110">Description</span><span class="sxs-lookup"><span data-stu-id="43715-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="43715-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="43715-111">S_OK</span></span>|<span data-ttu-id="43715-112">`CallNeedsHostHook`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="43715-112">`CallNeedsHostHook` returned successfully.</span></span>|  
|<span data-ttu-id="43715-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="43715-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="43715-114">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un état dans lequel il ne peut pas exécuter le code géré ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="43715-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="43715-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="43715-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="43715-116">L’appel s’est fait chronométrer.</span><span class="sxs-lookup"><span data-stu-id="43715-116">The call timed out.</span></span>|  
|<span data-ttu-id="43715-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="43715-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="43715-118">L’appelant n’est pas propriétaire de la serrure.</span><span class="sxs-lookup"><span data-stu-id="43715-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="43715-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="43715-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="43715-120">Un événement a été annulé alors qu’un fil bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="43715-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="43715-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="43715-121">E_FAIL</span></span>|<span data-ttu-id="43715-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="43715-122">An unknown catastrophic failure has occurred.</span></span> <span data-ttu-id="43715-123">Lorsqu’une méthode revient E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="43715-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="43715-124">Les appels ultérieurs aux méthodes d’hébergement reviennent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="43715-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43715-125">Notes </span><span class="sxs-lookup"><span data-stu-id="43715-125">Remarks</span></span>  
 <span data-ttu-id="43715-126">Pour aider à optimiser l’exécution du code, le CLR effectue une analyse de chaque plate-forme invoquer l’appel pendant la compilation pour déterminer si l’appel peut être inlined.</span><span class="sxs-lookup"><span data-stu-id="43715-126">To help optimize code execution, the CLR performs an analysis of each platform invoke call during compilation to determine whether the call can be inlined.</span></span> <span data-ttu-id="43715-127">`CallNeedsHostHook`permet à l’hôte de passer outre à cette décision en exigeant qu’un appel à une fonction non gestion soit accroché.</span><span class="sxs-lookup"><span data-stu-id="43715-127">`CallNeedsHostHook` enables the host to override that decision by requiring that a call to an unmanaged function be hooked.</span></span> <span data-ttu-id="43715-128">Si l’hôte a besoin d’un crochet, l’heure d’exécution n’inline pas l’appel.</span><span class="sxs-lookup"><span data-stu-id="43715-128">If the host requires a hook, the runtime does not inline the call.</span></span>  
  
 <span data-ttu-id="43715-129">L’hôte aurait généralement besoin d’un crochet où il doit ajuster un état de point flottant, ou après réception de la notification qu’un appel entre dans un état où l’hôte ne peut pas suivre les demandes de mémoire du temps d’exécution ou les verrous pris.</span><span class="sxs-lookup"><span data-stu-id="43715-129">The host typically would require a hook where it must adjust a floating-point state, or upon receiving notification that a call is entering a state where the host cannot track the runtime's requests for memory or any locks taken.</span></span> <span data-ttu-id="43715-130">Lorsque l’hôte exige que l’appel soit accroché, le temps d’exécution informe l’hôte des transitions vers et depuis le code géré en utilisant des appels à [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), et [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="43715-130">When the host requires that the call be hooked, the runtime notifies the host of transitions to and from managed code by using calls to [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), and [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43715-131">Spécifications</span><span class="sxs-lookup"><span data-stu-id="43715-131">Requirements</span></span>  
 <span data-ttu-id="43715-132">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43715-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43715-133">**En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor</span><span class="sxs-lookup"><span data-stu-id="43715-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="43715-134">**Bibliothèque:** Inclus comme une ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="43715-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="43715-135">**.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43715-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43715-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="43715-136">See also</span></span>

- [<span data-ttu-id="43715-137">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="43715-137">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="43715-138">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="43715-138">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="43715-139">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="43715-139">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="43715-140">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="43715-140">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
