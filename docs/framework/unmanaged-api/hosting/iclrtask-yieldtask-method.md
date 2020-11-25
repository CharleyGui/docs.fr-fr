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
ms.openlocfilehash: 7b9b47daa96ffcb1f66b462ff8e227250c5a81ca
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720276"
---
# <a name="iclrtaskyieldtask-method"></a><span data-ttu-id="6f7d5-102">ICLRTask::YieldTask, méthode</span><span class="sxs-lookup"><span data-stu-id="6f7d5-102">ICLRTask::YieldTask Method</span></span>

<span data-ttu-id="6f7d5-103">Demande que le common language runtime (CLR) mette de côté la tâche que l’instance d' [ICLRTask](iclrtask-interface.md) actuelle représente, et rend le temps processeur disponible pour d’autres tâches.</span><span class="sxs-lookup"><span data-stu-id="6f7d5-103">Requests that the common language runtime (CLR) put aside the task that the current [ICLRTask](iclrtask-interface.md) instance represents, and make the processor time available to other tasks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f7d5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6f7d5-104">Syntax</span></span>  
  
```cpp  
HRESULT YieldTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="6f7d5-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="6f7d5-105">Return Value</span></span>  
  
|<span data-ttu-id="6f7d5-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6f7d5-106">HRESULT</span></span>|<span data-ttu-id="6f7d5-107">Description</span><span class="sxs-lookup"><span data-stu-id="6f7d5-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6f7d5-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="6f7d5-108">S_OK</span></span>|<span data-ttu-id="6f7d5-109">`YieldTask` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="6f7d5-109">`YieldTask` returned successfully.</span></span>|  
|<span data-ttu-id="6f7d5-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6f7d5-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6f7d5-111">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="6f7d5-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6f7d5-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6f7d5-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6f7d5-113">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="6f7d5-113">The call timed out.</span></span>|  
|<span data-ttu-id="6f7d5-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6f7d5-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6f7d5-115">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="6f7d5-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6f7d5-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6f7d5-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6f7d5-117">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="6f7d5-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6f7d5-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6f7d5-118">E_FAIL</span></span>|<span data-ttu-id="6f7d5-119">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="6f7d5-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6f7d5-120">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="6f7d5-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6f7d5-121">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6f7d5-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f7d5-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="6f7d5-122">Remarks</span></span>  

 <span data-ttu-id="6f7d5-123">Un hôte appelle `YieldTask` pour demander des ressources de processeur pour d’autres tâches ou processus.</span><span class="sxs-lookup"><span data-stu-id="6f7d5-123">A host calls `YieldTask` to request processor resources for other tasks or processes.</span></span> <span data-ttu-id="6f7d5-124">Cette méthode est principalement destinée à permettre à du code de longue durée d’abandonner le temps processeur.</span><span class="sxs-lookup"><span data-stu-id="6f7d5-124">This method is primarily intended to allow long-running code to give up CPU time.</span></span> <span data-ttu-id="6f7d5-125">Le runtime tente de placer la tâche que l' `ICLRTask` instance actuelle représente dans un État où elle peut générer du temps de traitement, mais n’offre aucune garantie de réussite.</span><span class="sxs-lookup"><span data-stu-id="6f7d5-125">The runtime attempts to put the task that the current `ICLRTask` instance represents in a state where it can yield processing time, but makes no guarantee of success.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f7d5-126">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6f7d5-126">Requirements</span></span>  

 <span data-ttu-id="6f7d5-127">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f7d5-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f7d5-128">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6f7d5-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6f7d5-129">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6f7d5-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6f7d5-130">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f7d5-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f7d5-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6f7d5-131">See also</span></span>

- [<span data-ttu-id="6f7d5-132">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="6f7d5-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="6f7d5-133">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="6f7d5-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="6f7d5-134">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="6f7d5-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="6f7d5-135">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="6f7d5-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
