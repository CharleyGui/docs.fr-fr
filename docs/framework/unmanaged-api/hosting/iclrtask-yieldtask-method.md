---
title: ICLRTask::YieldTask, méthode
ms.date: 03/30/2017
api_name:
- ICLRTask.YieldTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::YieldTask
helpviewer_keywords:
- ICLRTask::YieldTask method [.NET Framework hosting]
- YieldTask method [.NET Framework hosting]
ms.assetid: b8eb4095-3a8f-4be3-9446-63e9893dce7d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6fde9586c1b3736b5db2c4814058dd23713dd34d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67770335"
---
# <a name="iclrtaskyieldtask-method"></a><span data-ttu-id="ad1f8-102">ICLRTask::YieldTask, méthode</span><span class="sxs-lookup"><span data-stu-id="ad1f8-102">ICLRTask::YieldTask Method</span></span>
<span data-ttu-id="ad1f8-103">Demande que le common language runtime (CLR) mette de côté la tâche qui en cours [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) représente l’instance et rendre le temps processeur disponible pour les autres tâches.</span><span class="sxs-lookup"><span data-stu-id="ad1f8-103">Requests that the common language runtime (CLR) put aside the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents, and make the processor time available to other tasks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad1f8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad1f8-104">Syntax</span></span>  
  
```cpp  
HRESULT YieldTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="ad1f8-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ad1f8-105">Return Value</span></span>  
  
|<span data-ttu-id="ad1f8-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ad1f8-106">HRESULT</span></span>|<span data-ttu-id="ad1f8-107">Description</span><span class="sxs-lookup"><span data-stu-id="ad1f8-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ad1f8-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="ad1f8-108">S_OK</span></span>|<span data-ttu-id="ad1f8-109">`YieldTask` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="ad1f8-109">`YieldTask` returned successfully.</span></span>|  
|<span data-ttu-id="ad1f8-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ad1f8-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ad1f8-111">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="ad1f8-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ad1f8-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ad1f8-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ad1f8-113">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="ad1f8-113">The call timed out.</span></span>|  
|<span data-ttu-id="ad1f8-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ad1f8-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ad1f8-115">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="ad1f8-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ad1f8-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ad1f8-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ad1f8-117">Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="ad1f8-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ad1f8-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ad1f8-118">E_FAIL</span></span>|<span data-ttu-id="ad1f8-119">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="ad1f8-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ad1f8-120">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus.</span><span class="sxs-lookup"><span data-stu-id="ad1f8-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ad1f8-121">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ad1f8-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad1f8-122">Notes</span><span class="sxs-lookup"><span data-stu-id="ad1f8-122">Remarks</span></span>  
 <span data-ttu-id="ad1f8-123">Un hôte appelle `YieldTask` pour demander des ressources processeur pour les autres tâches ou processus.</span><span class="sxs-lookup"><span data-stu-id="ad1f8-123">A host calls `YieldTask` to request processor resources for other tasks or processes.</span></span> <span data-ttu-id="ad1f8-124">Cette méthode est principalement destinée à autoriser le code longue d’abandonner le temps processeur.</span><span class="sxs-lookup"><span data-stu-id="ad1f8-124">This method is primarily intended to allow long-running code to give up CPU time.</span></span> <span data-ttu-id="ad1f8-125">Le runtime tente de placer la tâche qui en cours `ICLRTask` instance représente dans un état où il peut produire des temps de traitement, mais aucune garantie de succès.</span><span class="sxs-lookup"><span data-stu-id="ad1f8-125">The runtime attempts to put the task that the current `ICLRTask` instance represents in a state where it can yield processing time, but makes no guarantee of success.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad1f8-126">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ad1f8-126">Requirements</span></span>  
 <span data-ttu-id="ad1f8-127">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad1f8-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad1f8-128">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ad1f8-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ad1f8-129">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ad1f8-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ad1f8-130">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad1f8-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad1f8-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ad1f8-131">See also</span></span>

- [<span data-ttu-id="ad1f8-132">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="ad1f8-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="ad1f8-133">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="ad1f8-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="ad1f8-134">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="ad1f8-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="ad1f8-135">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="ad1f8-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
