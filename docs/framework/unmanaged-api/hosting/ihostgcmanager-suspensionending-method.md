---
title: IHostGCManager::SuspensionEnding, méthode
ms.date: 03/30/2017
api_name:
- IHostGCManager.SuspensionEnding
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager::SuspensionEnding
helpviewer_keywords:
- SuspensionEnding method, IHostGCManager interface [.NET Framework hosting]
- IHostGCManager::SuspensionEnding method [.NET Framework hosting]
ms.assetid: 8849a1db-17f0-44b7-880a-bd36d431eb91
topic_type:
- apiref
ms.openlocfilehash: 4c05ee766bf40be2e9c39f01c7e1b16cb9fab50d
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804835"
---
# <a name="ihostgcmanagersuspensionending-method"></a><span data-ttu-id="38d9c-102">IHostGCManager::SuspensionEnding, méthode</span><span class="sxs-lookup"><span data-stu-id="38d9c-102">IHostGCManager::SuspensionEnding Method</span></span>
<span data-ttu-id="38d9c-103">Avertit l’hôte que le common language runtime (CLR) reprend l’exécution des tâches sur les threads suspendus pour un garbage collection.</span><span class="sxs-lookup"><span data-stu-id="38d9c-103">Notifies the host that the common language runtime (CLR) is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38d9c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38d9c-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionEnding (  
    [in] DWORD generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38d9c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="38d9c-105">Parameters</span></span>  
 `generation`  
 <span data-ttu-id="38d9c-106">dans Génération de garbage collection qui se termine simplement, à partir de laquelle le thread est en train de reprendre.</span><span class="sxs-lookup"><span data-stu-id="38d9c-106">[in] The garbage collection generation that is just finishing, from which the thread is resuming.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="38d9c-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="38d9c-107">Return Value</span></span>  
  
|<span data-ttu-id="38d9c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="38d9c-108">HRESULT</span></span>|<span data-ttu-id="38d9c-109">Description</span><span class="sxs-lookup"><span data-stu-id="38d9c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="38d9c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="38d9c-110">S_OK</span></span>|<span data-ttu-id="38d9c-111">`SuspensionEnding`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="38d9c-111">`SuspensionEnding` returned successfully.</span></span>|  
|<span data-ttu-id="38d9c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="38d9c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="38d9c-113">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="38d9c-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="38d9c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="38d9c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="38d9c-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="38d9c-115">The call timed out.</span></span>|  
|<span data-ttu-id="38d9c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="38d9c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="38d9c-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="38d9c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="38d9c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="38d9c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="38d9c-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="38d9c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="38d9c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="38d9c-120">E_FAIL</span></span>|<span data-ttu-id="38d9c-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="38d9c-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="38d9c-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="38d9c-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="38d9c-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="38d9c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38d9c-124">Notes</span><span class="sxs-lookup"><span data-stu-id="38d9c-124">Remarks</span></span>  
 <span data-ttu-id="38d9c-125">Le CLR appelle une `SuspensionEnding` fois qu’il a exécuté une garbage collection, afin d’informer l’hôte que le thread reprend l’exécution.</span><span class="sxs-lookup"><span data-stu-id="38d9c-125">The CLR calls `SuspensionEnding` after it performs a garbage collection, to inform the host that the thread is resuming execution.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="38d9c-126">Ne replanifiez pas le thread à partir duquel l’appel de méthode a été effectué.</span><span class="sxs-lookup"><span data-stu-id="38d9c-126">Do not reschedule the thread the method call was made from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38d9c-127">Spécifications</span><span class="sxs-lookup"><span data-stu-id="38d9c-127">Requirements</span></span>  
 <span data-ttu-id="38d9c-128">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38d9c-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38d9c-129">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="38d9c-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="38d9c-130">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="38d9c-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="38d9c-131">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38d9c-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38d9c-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38d9c-132">See also</span></span>

- [<span data-ttu-id="38d9c-133">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="38d9c-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="38d9c-134">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="38d9c-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="38d9c-135">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="38d9c-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="38d9c-136">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="38d9c-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="38d9c-137">IHostGCManager, interface</span><span class="sxs-lookup"><span data-stu-id="38d9c-137">IHostGCManager Interface</span></span>](ihostgcmanager-interface.md)
