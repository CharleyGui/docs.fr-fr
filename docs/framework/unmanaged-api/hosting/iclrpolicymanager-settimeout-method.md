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
ms.openlocfilehash: 459c5bc0699487b62d5dcf76f1044faf53ebab8b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732461"
---
# <a name="iclrpolicymanagersettimeout-method"></a><span data-ttu-id="5f4ee-102">ICLRPolicyManager::SetTimeout, méthode</span><span class="sxs-lookup"><span data-stu-id="5f4ee-102">ICLRPolicyManager::SetTimeout Method</span></span>

<span data-ttu-id="5f4ee-103">Définit une valeur de délai d’attente pour l’opération spécifiée.</span><span class="sxs-lookup"><span data-stu-id="5f4ee-103">Sets a timeout value for the specified operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f4ee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5f4ee-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTimeout (  
    [in] EClrOperation operation,  
    [in] DWORD dsMilliseconds  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f4ee-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5f4ee-105">Parameters</span></span>  

 `operation`  
 <span data-ttu-id="5f4ee-106">dans L’une des valeurs [EClrOperation](eclroperation-enumeration.md) , indiquant l’opération de Common Language Runtime (CLR) pour laquelle définir un délai d’attente.</span><span class="sxs-lookup"><span data-stu-id="5f4ee-106">[in] One of the [EClrOperation](eclroperation-enumeration.md) values, indicating the common language runtime (CLR) operation for which to set a timeout.</span></span> <span data-ttu-id="5f4ee-107">Les valeurs suivantes sont admises :</span><span class="sxs-lookup"><span data-stu-id="5f4ee-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="5f4ee-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="5f4ee-108">OPR_AppDomainUnload</span></span>  
  
- <span data-ttu-id="5f4ee-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="5f4ee-109">OPR_ProcessExit</span></span>  
  
- <span data-ttu-id="5f4ee-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="5f4ee-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
- <span data-ttu-id="5f4ee-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="5f4ee-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="5f4ee-112">dans Nouvelle valeur du délai d’attente, en millisecondes.</span><span class="sxs-lookup"><span data-stu-id="5f4ee-112">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="5f4ee-113">Si la valeur est Infinite, l’opération n’expire jamais.</span><span class="sxs-lookup"><span data-stu-id="5f4ee-113">A value of INFINITE causes the operation never to time out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5f4ee-114">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="5f4ee-114">Return Value</span></span>  
  
|<span data-ttu-id="5f4ee-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5f4ee-115">HRESULT</span></span>|<span data-ttu-id="5f4ee-116">Description</span><span class="sxs-lookup"><span data-stu-id="5f4ee-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5f4ee-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="5f4ee-117">S_OK</span></span>|<span data-ttu-id="5f4ee-118">`SetTimeout` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="5f4ee-118">`SetTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="5f4ee-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5f4ee-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5f4ee-120">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="5f4ee-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5f4ee-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5f4ee-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5f4ee-122">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="5f4ee-122">The call timed out.</span></span>|  
|<span data-ttu-id="5f4ee-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5f4ee-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5f4ee-124">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="5f4ee-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5f4ee-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5f4ee-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5f4ee-126">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="5f4ee-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5f4ee-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5f4ee-127">E_FAIL</span></span>|<span data-ttu-id="5f4ee-128">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="5f4ee-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5f4ee-129">Une fois que la méthode a retourné E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="5f4ee-129">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5f4ee-130">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5f4ee-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5f4ee-131">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="5f4ee-131">E_INVALIDARG</span></span>|<span data-ttu-id="5f4ee-132">Un délai d’expiration ne peut pas être défini pour le spécifié `operation` , ou une valeur non valide a été fournie pour `operation` .</span><span class="sxs-lookup"><span data-stu-id="5f4ee-132">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5f4ee-133">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5f4ee-133">Requirements</span></span>  

 <span data-ttu-id="5f4ee-134">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f4ee-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f4ee-135">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5f4ee-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5f4ee-136">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5f4ee-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5f4ee-137">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f4ee-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f4ee-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5f4ee-138">See also</span></span>

- [<span data-ttu-id="5f4ee-139">EClrOperation, énumération</span><span class="sxs-lookup"><span data-stu-id="5f4ee-139">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="5f4ee-140">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="5f4ee-140">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="5f4ee-141">ICLRPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="5f4ee-141">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
