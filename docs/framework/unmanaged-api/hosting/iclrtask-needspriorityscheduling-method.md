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
ms.openlocfilehash: df20e98a9e88c10bac748a5acfc91adcb133da79
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762988"
---
# <a name="iclrtaskneedspriorityscheduling-method"></a><span data-ttu-id="e5ca2-102">ICLRTask::NeedsPriorityScheduling, méthode</span><span class="sxs-lookup"><span data-stu-id="e5ca2-102">ICLRTask::NeedsPriorityScheduling Method</span></span>
<span data-ttu-id="e5ca2-103">Obtient une valeur qui indique si la tâche en cours, qui est en cours de basculement, doit être marquée comme haute priorité pour la replanification.</span><span class="sxs-lookup"><span data-stu-id="e5ca2-103">Gets a value that indicates whether the current task, which is being switched out, needs to be marked as a high priority for rescheduling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5ca2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5ca2-104">Syntax</span></span>  
  
```cpp  
HRESULT NeedsPriorityScheduling (  
    [out] BOOL *pbNeedsPriorityScheduling  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5ca2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e5ca2-105">Parameters</span></span>  
 `pbNeedsPriorityRescheduling`  
 <span data-ttu-id="e5ca2-106">[out] `true` , si l’hôte doit tenter de replanifier l’instance de tâche en cours dès que possible ; sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="e5ca2-106">[out] `true`, if the host should attempt to reschedule the current task instance as soon as possible; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e5ca2-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e5ca2-107">Return Value</span></span>  
  
|<span data-ttu-id="e5ca2-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e5ca2-108">HRESULT</span></span>|<span data-ttu-id="e5ca2-109">Description</span><span class="sxs-lookup"><span data-stu-id="e5ca2-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e5ca2-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e5ca2-110">S_OK</span></span>|<span data-ttu-id="e5ca2-111">`NeedsPriorityRescheduling`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="e5ca2-111">`NeedsPriorityRescheduling` returned successfully.</span></span>|  
|<span data-ttu-id="e5ca2-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e5ca2-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e5ca2-113">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="e5ca2-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e5ca2-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e5ca2-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e5ca2-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="e5ca2-115">The call timed out.</span></span>|  
|<span data-ttu-id="e5ca2-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e5ca2-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e5ca2-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="e5ca2-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e5ca2-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e5ca2-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e5ca2-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="e5ca2-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e5ca2-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e5ca2-120">E_FAIL</span></span>|<span data-ttu-id="e5ca2-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="e5ca2-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e5ca2-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="e5ca2-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e5ca2-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e5ca2-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5ca2-124">Notes</span><span class="sxs-lookup"><span data-stu-id="e5ca2-124">Remarks</span></span>  
 <span data-ttu-id="e5ca2-125">Dans les situations où la tâche est proche de la collecte par le garbage collector, le CLR définit la valeur de `pbNeedsPriorityScheduling` sur `true` , indiquant une replanification à priorité élevée.</span><span class="sxs-lookup"><span data-stu-id="e5ca2-125">In situations where the task is close to being collected by the garbage collector, the CLR sets the value of `pbNeedsPriorityScheduling` to `true`, indicating high-priority rescheduling.</span></span> <span data-ttu-id="e5ca2-126">Cela permet à l’hôte de replanifier rapidement la tâche, réduisant ainsi le risque de retards dans garbage collection et d’autoriser l’hôte et le runtime à coopérer à la préservation des ressources mémoire.</span><span class="sxs-lookup"><span data-stu-id="e5ca2-126">This allows the host to reschedule the task quickly, thereby minimizing the potential for delays in garbage collection, and enabling the host and the runtime to cooperate in conserving memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5ca2-127">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="e5ca2-127">Requirements</span></span>  
 <span data-ttu-id="e5ca2-128">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5ca2-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5ca2-129">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e5ca2-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e5ca2-130">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e5ca2-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e5ca2-131">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5ca2-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5ca2-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e5ca2-132">See also</span></span>

- [<span data-ttu-id="e5ca2-133">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="e5ca2-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="e5ca2-134">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="e5ca2-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="e5ca2-135">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="e5ca2-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="e5ca2-136">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="e5ca2-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
