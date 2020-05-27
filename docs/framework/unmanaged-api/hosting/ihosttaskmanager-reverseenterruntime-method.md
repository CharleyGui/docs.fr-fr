---
title: IHostTaskManager::ReverseEnterRuntime, méthode
ms.date: 03/30/2017
api_name:
- IHostTaskManager.ReverseEnterRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::ReverseEnterRuntime
helpviewer_keywords:
- IHostTaskManager::ReverseEnterRuntime method [.NET Framework hosting]
- ReverseEnterRuntime method [.NET Framework hosting]
ms.assetid: b1e26bff-d3ea-436e-9867-29720df999f4
topic_type:
- apiref
ms.openlocfilehash: 41955bd2f64d53e3620dede6b6da4cef2aab45f4
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842294"
---
# <a name="ihosttaskmanagerreverseenterruntime-method"></a><span data-ttu-id="1b794-102">IHostTaskManager::ReverseEnterRuntime, méthode</span><span class="sxs-lookup"><span data-stu-id="1b794-102">IHostTaskManager::ReverseEnterRuntime Method</span></span>
<span data-ttu-id="1b794-103">Indique à l’hôte qu’un appel est effectué dans le common language runtime (CLR) à partir du code non managé.</span><span class="sxs-lookup"><span data-stu-id="1b794-103">Notifies the host that a call is being made into the common language runtime (CLR) from unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b794-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1b794-104">Syntax</span></span>  
  
```cpp  
HRESULT ReverseEnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="1b794-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="1b794-105">Return Value</span></span>  
  
|<span data-ttu-id="1b794-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1b794-106">HRESULT</span></span>|<span data-ttu-id="1b794-107">Description</span><span class="sxs-lookup"><span data-stu-id="1b794-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1b794-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="1b794-108">S_OK</span></span>|<span data-ttu-id="1b794-109">`ReverseEnterRuntime`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="1b794-109">`ReverseEnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="1b794-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1b794-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1b794-111">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="1b794-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1b794-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1b794-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1b794-113">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="1b794-113">The call timed out.</span></span>|  
|<span data-ttu-id="1b794-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1b794-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1b794-115">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="1b794-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1b794-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1b794-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1b794-117">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="1b794-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1b794-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1b794-118">E_FAIL</span></span>|<span data-ttu-id="1b794-119">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="1b794-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1b794-120">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="1b794-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1b794-121">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1b794-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1b794-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="1b794-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="1b794-123">La mémoire disponible est insuffisante pour terminer l’allocation de ressources demandée.</span><span class="sxs-lookup"><span data-stu-id="1b794-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b794-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="1b794-124">Remarks</span></span>  
 <span data-ttu-id="1b794-125">Si l’appel dans le CLR est effectué à partir d’une séquence provenant du code managé, chaque appel à `ReverseEnterRuntime` correspond à un appel à [ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="1b794-125">If the call into the CLR is made from a sequence that originated in managed code, each call to `ReverseEnterRuntime` corresponds to a call to [ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1b794-126">Les appels peuvent provenir du code non managé sans être imbriqués.</span><span class="sxs-lookup"><span data-stu-id="1b794-126">Calls can originate from unmanaged code without being nested.</span></span> <span data-ttu-id="1b794-127">Dans ce cas, il n’y a aucun appel à [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](ihosttaskmanager-leaveruntime-method.md)ou `ReverseLeaveRuntime` , et le nombre d’appels à `ReverseEnterRuntime` n’est pas égal au nombre d’appels à `ReverseLeaveRuntime` .</span><span class="sxs-lookup"><span data-stu-id="1b794-127">In this case, there is no call to [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](ihosttaskmanager-leaveruntime-method.md), or `ReverseLeaveRuntime`, and the number of calls to `ReverseEnterRuntime` does not equal the number of calls to `ReverseLeaveRuntime`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b794-128">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1b794-128">Requirements</span></span>  
 <span data-ttu-id="1b794-129">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b794-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b794-130">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1b794-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1b794-131">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1b794-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1b794-132">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b794-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b794-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1b794-133">See also</span></span>

- [<span data-ttu-id="1b794-134">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="1b794-134">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="1b794-135">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="1b794-135">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="1b794-136">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="1b794-136">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="1b794-137">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="1b794-137">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
