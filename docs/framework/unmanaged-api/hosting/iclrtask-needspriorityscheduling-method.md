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
ms.openlocfilehash: 91c1ea51969447861ff6d0956c5714baa0054450
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124671"
---
# <a name="iclrtaskneedspriorityscheduling-method"></a><span data-ttu-id="fc956-102">ICLRTask::NeedsPriorityScheduling, méthode</span><span class="sxs-lookup"><span data-stu-id="fc956-102">ICLRTask::NeedsPriorityScheduling Method</span></span>
<span data-ttu-id="fc956-103">Obtient une valeur qui indique si la tâche en cours, qui est en cours de basculement, doit être marquée comme haute priorité pour la replanification.</span><span class="sxs-lookup"><span data-stu-id="fc956-103">Gets a value that indicates whether the current task, which is being switched out, needs to be marked as a high priority for rescheduling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc956-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fc956-104">Syntax</span></span>  
  
```cpp  
HRESULT NeedsPriorityScheduling (  
    [out] BOOL *pbNeedsPriorityScheduling  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc956-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fc956-105">Parameters</span></span>  
 `pbNeedsPriorityRescheduling`  
 <span data-ttu-id="fc956-106">[out] `true`, si l’hôte doit tenter de replanifier l’instance de tâche actuelle dès que possible ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="fc956-106">[out] `true`, if the host should attempt to reschedule the current task instance as soon as possible; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fc956-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="fc956-107">Return Value</span></span>  
  
|<span data-ttu-id="fc956-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fc956-108">HRESULT</span></span>|<span data-ttu-id="fc956-109">Description</span><span class="sxs-lookup"><span data-stu-id="fc956-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fc956-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="fc956-110">S_OK</span></span>|<span data-ttu-id="fc956-111">`NeedsPriorityRescheduling` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="fc956-111">`NeedsPriorityRescheduling` returned successfully.</span></span>|  
|<span data-ttu-id="fc956-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fc956-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fc956-113">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="fc956-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fc956-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fc956-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fc956-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="fc956-115">The call timed out.</span></span>|  
|<span data-ttu-id="fc956-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fc956-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fc956-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="fc956-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fc956-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fc956-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fc956-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="fc956-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fc956-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fc956-120">E_FAIL</span></span>|<span data-ttu-id="fc956-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="fc956-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fc956-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="fc956-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fc956-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fc956-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc956-124">Notes</span><span class="sxs-lookup"><span data-stu-id="fc956-124">Remarks</span></span>  
 <span data-ttu-id="fc956-125">Dans les situations où la tâche est proche de la collecte par le garbage collector, le CLR définit la valeur de `pbNeedsPriorityScheduling` sur `true`, ce qui indique une replanification à priorité élevée.</span><span class="sxs-lookup"><span data-stu-id="fc956-125">In situations where the task is close to being collected by the garbage collector, the CLR sets the value of `pbNeedsPriorityScheduling` to `true`, indicating high-priority rescheduling.</span></span> <span data-ttu-id="fc956-126">Cela permet à l’hôte de replanifier rapidement la tâche, réduisant ainsi le risque de retards dans garbage collection et d’autoriser l’hôte et le runtime à coopérer à la préservation des ressources mémoire.</span><span class="sxs-lookup"><span data-stu-id="fc956-126">This allows the host to reschedule the task quickly, thereby minimizing the potential for delays in garbage collection, and enabling the host and the runtime to cooperate in conserving memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc956-127">spécifications</span><span class="sxs-lookup"><span data-stu-id="fc956-127">Requirements</span></span>  
 <span data-ttu-id="fc956-128">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc956-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc956-129">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fc956-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fc956-130">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="fc956-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fc956-131">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc956-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc956-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fc956-132">See also</span></span>

- [<span data-ttu-id="fc956-133">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="fc956-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="fc956-134">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="fc956-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="fc956-135">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="fc956-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="fc956-136">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="fc956-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
