---
title: ICLRTask::NeedsPriorityScheduling, méthode
ms.date: 03/30/2017
api_name:
- ICLRTask.NeedsPriorityScheduling
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::NeedsPriorityScheduling
helpviewer_keywords:
- ICLRTask::NeedsPriorityScheduling method [.NET Framework hosting]
- NeedsPriorityScheduling method [.NET Framework hosting]
ms.assetid: 9c9db3f3-26bf-4317-88de-5eb926a22a1d
topic_type:
- apiref
ms.openlocfilehash: 86e0899b883f09f2e7b27c0f957e943deb73bb66
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690796"
---
# <a name="iclrtaskneedspriorityscheduling-method"></a><span data-ttu-id="2e9c3-102">ICLRTask::NeedsPriorityScheduling, méthode</span><span class="sxs-lookup"><span data-stu-id="2e9c3-102">ICLRTask::NeedsPriorityScheduling Method</span></span>

<span data-ttu-id="2e9c3-103">Obtient une valeur qui indique si la tâche en cours, qui est en cours de basculement, doit être marquée comme haute priorité pour la replanification.</span><span class="sxs-lookup"><span data-stu-id="2e9c3-103">Gets a value that indicates whether the current task, which is being switched out, needs to be marked as a high priority for rescheduling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e9c3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e9c3-104">Syntax</span></span>  
  
```cpp  
HRESULT NeedsPriorityScheduling (  
    [out] BOOL *pbNeedsPriorityScheduling  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e9c3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2e9c3-105">Parameters</span></span>  

 `pbNeedsPriorityRescheduling`  
 <span data-ttu-id="2e9c3-106">[out] `true` , si l’hôte doit tenter de replanifier l’instance de tâche en cours dès que possible ; sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="2e9c3-106">[out] `true`, if the host should attempt to reschedule the current task instance as soon as possible; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2e9c3-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="2e9c3-107">Return Value</span></span>  
  
|<span data-ttu-id="2e9c3-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2e9c3-108">HRESULT</span></span>|<span data-ttu-id="2e9c3-109">Description</span><span class="sxs-lookup"><span data-stu-id="2e9c3-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2e9c3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="2e9c3-110">S_OK</span></span>|<span data-ttu-id="2e9c3-111">`NeedsPriorityRescheduling` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="2e9c3-111">`NeedsPriorityRescheduling` returned successfully.</span></span>|  
|<span data-ttu-id="2e9c3-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2e9c3-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2e9c3-113">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="2e9c3-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2e9c3-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2e9c3-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2e9c3-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="2e9c3-115">The call timed out.</span></span>|  
|<span data-ttu-id="2e9c3-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2e9c3-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2e9c3-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="2e9c3-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2e9c3-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2e9c3-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2e9c3-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="2e9c3-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2e9c3-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2e9c3-120">E_FAIL</span></span>|<span data-ttu-id="2e9c3-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="2e9c3-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2e9c3-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="2e9c3-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2e9c3-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2e9c3-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2e9c3-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="2e9c3-124">Remarks</span></span>  

 <span data-ttu-id="2e9c3-125">Dans les situations où la tâche est proche de la collecte par le garbage collector, le CLR définit la valeur de `pbNeedsPriorityScheduling` sur `true` , indiquant une replanification à priorité élevée.</span><span class="sxs-lookup"><span data-stu-id="2e9c3-125">In situations where the task is close to being collected by the garbage collector, the CLR sets the value of `pbNeedsPriorityScheduling` to `true`, indicating high-priority rescheduling.</span></span> <span data-ttu-id="2e9c3-126">Cela permet à l’hôte de replanifier rapidement la tâche, réduisant ainsi le risque de retards dans garbage collection et d’autoriser l’hôte et le runtime à coopérer à la préservation des ressources mémoire.</span><span class="sxs-lookup"><span data-stu-id="2e9c3-126">This allows the host to reschedule the task quickly, thereby minimizing the potential for delays in garbage collection, and enabling the host and the runtime to cooperate in conserving memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e9c3-127">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2e9c3-127">Requirements</span></span>  

 <span data-ttu-id="2e9c3-128">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e9c3-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e9c3-129">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2e9c3-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2e9c3-130">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2e9c3-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2e9c3-131">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e9c3-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e9c3-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e9c3-132">See also</span></span>

- [<span data-ttu-id="2e9c3-133">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="2e9c3-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="2e9c3-134">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="2e9c3-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="2e9c3-135">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="2e9c3-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="2e9c3-136">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="2e9c3-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
