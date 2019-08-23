---
title: IHostTask::SetPriority, méthode
ms.date: 03/30/2017
api_name:
- IHostTask.SetPriority
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::SetPriority
helpviewer_keywords:
- IHostTask::SetPriority method [.NET Framework hosting]
- SetPriority method [.NET Framework hosting]
ms.assetid: cd8c379b-c7a0-434f-8e23-899bd26be75d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 533e3d715b46b4ef6d473795a010fa3ad297ded2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913750"
---
# <a name="ihosttasksetpriority-method"></a><span data-ttu-id="b6ae2-102">IHostTask::SetPriority, méthode</span><span class="sxs-lookup"><span data-stu-id="b6ae2-102">IHostTask::SetPriority Method</span></span>
<span data-ttu-id="b6ae2-103">Demande que l’hôte ajuste le niveau de priorité de thread pour la tâche représentée par l’instance [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) actuelle.</span><span class="sxs-lookup"><span data-stu-id="b6ae2-103">Requests that the host adjust the thread priority level for the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6ae2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6ae2-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPriority (  
    [in] int newPriority  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6ae2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b6ae2-105">Parameters</span></span>  
 `newPriority`  
 <span data-ttu-id="b6ae2-106">dans Entier qui représente la valeur de priorité de thread demandée pour la tâche représentée par l' `IHostTask` instance actuelle.</span><span class="sxs-lookup"><span data-stu-id="b6ae2-106">[in] An integer that represents the requested thread priority value for the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b6ae2-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="b6ae2-107">Return Value</span></span>  
  
|<span data-ttu-id="b6ae2-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b6ae2-108">HRESULT</span></span>|<span data-ttu-id="b6ae2-109">Description</span><span class="sxs-lookup"><span data-stu-id="b6ae2-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b6ae2-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b6ae2-110">S_OK</span></span>|<span data-ttu-id="b6ae2-111">`SetPriority`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="b6ae2-111">`SetPriority` returned successfully.</span></span>|  
|<span data-ttu-id="b6ae2-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b6ae2-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b6ae2-113">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="b6ae2-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b6ae2-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b6ae2-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b6ae2-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="b6ae2-115">The call timed out.</span></span>|  
|<span data-ttu-id="b6ae2-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b6ae2-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b6ae2-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="b6ae2-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b6ae2-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b6ae2-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b6ae2-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="b6ae2-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b6ae2-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b6ae2-120">E_FAIL</span></span>|<span data-ttu-id="b6ae2-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="b6ae2-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b6ae2-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="b6ae2-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b6ae2-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b6ae2-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6ae2-124">Notes</span><span class="sxs-lookup"><span data-stu-id="b6ae2-124">Remarks</span></span>  
 <span data-ttu-id="b6ae2-125">Le temps de traitement des threads est accordé à l’aide d’un système de tourniquet (Round Robin) basé en partie sur le niveau de priorité d’un thread.</span><span class="sxs-lookup"><span data-stu-id="b6ae2-125">Threads are granted processing time using a round-robin system that is partly based on a thread's priority level.</span></span> <span data-ttu-id="b6ae2-126">`SetPriority`permet au CLR de définir ce niveau de priorité de thread pour la tâche actuelle.</span><span class="sxs-lookup"><span data-stu-id="b6ae2-126">`SetPriority` allows the CLR to set that thread priority level for the current task.</span></span> <span data-ttu-id="b6ae2-127">Les valeurs `newPriority` suivantes sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="b6ae2-127">The following `newPriority` values are supported.</span></span>  
  
- <span data-ttu-id="b6ae2-128">THREAD_PRIORITY_ABOVE_NORMAL</span><span class="sxs-lookup"><span data-stu-id="b6ae2-128">THREAD_PRIORITY_ABOVE_NORMAL</span></span>  
  
- <span data-ttu-id="b6ae2-129">THREAD_PRIORITY_BELOW_NORMAL</span><span class="sxs-lookup"><span data-stu-id="b6ae2-129">THREAD_PRIORITY_BELOW_NORMAL</span></span>  
  
- <span data-ttu-id="b6ae2-130">THREAD_PRIORITY_HIGHEST</span><span class="sxs-lookup"><span data-stu-id="b6ae2-130">THREAD_PRIORITY_HIGHEST</span></span>  
  
- <span data-ttu-id="b6ae2-131">THREAD_PRIORITY_IDLE</span><span class="sxs-lookup"><span data-stu-id="b6ae2-131">THREAD_PRIORITY_IDLE</span></span>  
  
- <span data-ttu-id="b6ae2-132">THREAD_PRIORITY_LOWEST</span><span class="sxs-lookup"><span data-stu-id="b6ae2-132">THREAD_PRIORITY_LOWEST</span></span>  
  
- <span data-ttu-id="b6ae2-133">THREAD_PRIORITY_NORMAL</span><span class="sxs-lookup"><span data-stu-id="b6ae2-133">THREAD_PRIORITY_NORMAL</span></span>  
  
- <span data-ttu-id="b6ae2-134">THREAD_PRIORITY_TIME_CRITICAL</span><span class="sxs-lookup"><span data-stu-id="b6ae2-134">THREAD_PRIORITY_TIME_CRITICAL</span></span>  
  
 <span data-ttu-id="b6ae2-135">Le CLR appelle `SetPriority` lorsque la valeur <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> de est modifiée par le code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b6ae2-135">The CLR calls `SetPriority` when the value of the <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> is modified by user code.</span></span> <span data-ttu-id="b6ae2-136">Un hôte peut définir ses propres algorithmes pour l’affectation de priorité de thread et il est libre d’ignorer cette requête.</span><span class="sxs-lookup"><span data-stu-id="b6ae2-136">A host can define its own algorithms for thread priority assignment, and is free to ignore this request.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b6ae2-137">`SetPriority`ne signale pas si le niveau de priorité du thread a été modifié.</span><span class="sxs-lookup"><span data-stu-id="b6ae2-137">`SetPriority` does not report whether the thread priority level was changed.</span></span> <span data-ttu-id="b6ae2-138">Appelez [IHostTask:: getPriority,](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md) pour déterminer la valeur du niveau de priorité de thread de la tâche.</span><span class="sxs-lookup"><span data-stu-id="b6ae2-138">Call [IHostTask::GetPriority](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md) to determine the value of the task's thread priority level.</span></span>  
  
 <span data-ttu-id="b6ae2-139">Les valeurs de niveau de priorité de thread sont `SetThreadPriority` définies par la fonction Win32.</span><span class="sxs-lookup"><span data-stu-id="b6ae2-139">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span> <span data-ttu-id="b6ae2-140">Pour plus d’informations sur la priorité des threads, consultez la documentation de la plateforme Windows.</span><span class="sxs-lookup"><span data-stu-id="b6ae2-140">For more information about thread priority, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6ae2-141">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b6ae2-141">Requirements</span></span>  
 <span data-ttu-id="b6ae2-142">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6ae2-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6ae2-143">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b6ae2-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b6ae2-144">**Bibliothèque** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b6ae2-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b6ae2-145">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6ae2-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6ae2-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6ae2-146">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="b6ae2-147">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="b6ae2-147">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="b6ae2-148">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="b6ae2-148">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="b6ae2-149">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="b6ae2-149">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="b6ae2-150">GetPriority, méthode</span><span class="sxs-lookup"><span data-stu-id="b6ae2-150">GetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)
- [<span data-ttu-id="b6ae2-151">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="b6ae2-151">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
