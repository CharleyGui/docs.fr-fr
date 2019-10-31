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
ms.openlocfilehash: 43f2048c8ab85fa7e94f73aad430400ad4c8352f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124595"
---
# <a name="iclrtaskyieldtask-method"></a><span data-ttu-id="79a37-102">ICLRTask::YieldTask, méthode</span><span class="sxs-lookup"><span data-stu-id="79a37-102">ICLRTask::YieldTask Method</span></span>
<span data-ttu-id="79a37-103">Demande que le common language runtime (CLR) mette de côté la tâche que l’instance d' [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) actuelle représente, et rend le temps processeur disponible pour d’autres tâches.</span><span class="sxs-lookup"><span data-stu-id="79a37-103">Requests that the common language runtime (CLR) put aside the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents, and make the processor time available to other tasks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79a37-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="79a37-104">Syntax</span></span>  
  
```cpp  
HRESULT YieldTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="79a37-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="79a37-105">Return Value</span></span>  
  
|<span data-ttu-id="79a37-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="79a37-106">HRESULT</span></span>|<span data-ttu-id="79a37-107">Description</span><span class="sxs-lookup"><span data-stu-id="79a37-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="79a37-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="79a37-108">S_OK</span></span>|<span data-ttu-id="79a37-109">`YieldTask` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="79a37-109">`YieldTask` returned successfully.</span></span>|  
|<span data-ttu-id="79a37-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="79a37-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="79a37-111">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="79a37-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="79a37-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="79a37-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="79a37-113">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="79a37-113">The call timed out.</span></span>|  
|<span data-ttu-id="79a37-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="79a37-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="79a37-115">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="79a37-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="79a37-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="79a37-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="79a37-117">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="79a37-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="79a37-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="79a37-118">E_FAIL</span></span>|<span data-ttu-id="79a37-119">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="79a37-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="79a37-120">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="79a37-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="79a37-121">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="79a37-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="79a37-122">Notes</span><span class="sxs-lookup"><span data-stu-id="79a37-122">Remarks</span></span>  
 <span data-ttu-id="79a37-123">Un hôte appelle `YieldTask` pour demander des ressources de processeur pour d’autres tâches ou processus.</span><span class="sxs-lookup"><span data-stu-id="79a37-123">A host calls `YieldTask` to request processor resources for other tasks or processes.</span></span> <span data-ttu-id="79a37-124">Cette méthode est principalement destinée à permettre à du code de longue durée d’abandonner le temps processeur.</span><span class="sxs-lookup"><span data-stu-id="79a37-124">This method is primarily intended to allow long-running code to give up CPU time.</span></span> <span data-ttu-id="79a37-125">Le runtime tente de placer la tâche que l’instance de `ICLRTask` actuelle représente dans un État où elle peut générer du temps de traitement, mais n’offre aucune garantie de réussite.</span><span class="sxs-lookup"><span data-stu-id="79a37-125">The runtime attempts to put the task that the current `ICLRTask` instance represents in a state where it can yield processing time, but makes no guarantee of success.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79a37-126">spécifications</span><span class="sxs-lookup"><span data-stu-id="79a37-126">Requirements</span></span>  
 <span data-ttu-id="79a37-127">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79a37-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79a37-128">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="79a37-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="79a37-129">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="79a37-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="79a37-130">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79a37-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79a37-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="79a37-131">See also</span></span>

- [<span data-ttu-id="79a37-132">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="79a37-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="79a37-133">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="79a37-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="79a37-134">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="79a37-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="79a37-135">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="79a37-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
