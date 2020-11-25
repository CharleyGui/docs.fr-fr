---
title: IHostTask::Join, méthode
ms.date: 03/30/2017
api_name:
- IHostTask.Join
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::Join
helpviewer_keywords:
- IHostTask::Join method [.NET Framework hosting]
- Join method, IHostTask interface [.NET Framework hosting]
ms.assetid: 2cffcc52-19e0-4ced-a440-fc7375078ac9
topic_type:
- apiref
ms.openlocfilehash: 37156b03b184d06e0c7b03d7d7a9a018793bbb98
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721632"
---
# <a name="ihosttaskjoin-method"></a><span data-ttu-id="78b37-102">IHostTask::Join, méthode</span><span class="sxs-lookup"><span data-stu-id="78b37-102">IHostTask::Join Method</span></span>

<span data-ttu-id="78b37-103">Bloque la tâche appelante jusqu’à ce que la tâche représentée par l’instance [IHostTask](ihosttask-interface.md) en cours se termine, que l’intervalle de temps spécifié s’écoule, ou que la méthode [IHostTask :: Alert](ihosttask-alert-method.md) soit appelée.</span><span class="sxs-lookup"><span data-stu-id="78b37-103">Blocks the calling task until the task represented by the current [IHostTask](ihosttask-interface.md) instance completes, the specified time interval elapses, or [IHostTask::Alert](ihosttask-alert-method.md) is called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78b37-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78b37-104">Syntax</span></span>  
  
```cpp  
HRESULT Join (  
    [in] DWORD milliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78b37-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="78b37-105">Parameters</span></span>  

 `milliseconds`  
 <span data-ttu-id="78b37-106">dans Intervalle de temps, en millisecondes, à attendre que la tâche se termine.</span><span class="sxs-lookup"><span data-stu-id="78b37-106">[in] The time interval, in milliseconds, to wait for the task to terminate.</span></span> <span data-ttu-id="78b37-107">Si cet intervalle s’écoule avant la fin de la tâche, la tâche appelante est débloquée.</span><span class="sxs-lookup"><span data-stu-id="78b37-107">If this interval elapses before the task terminates, the calling task unblocks.</span></span>  
  
 `option`  
 <span data-ttu-id="78b37-108">dans L’une des valeurs [WAIT_OPTION](wait-option-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="78b37-108">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) values.</span></span> <span data-ttu-id="78b37-109">La valeur WAIT_ALERTABLE indique à l’hôte de réveiller la tâche si `Alert` est appelé avant que ne soit `milliseconds` écoulé.</span><span class="sxs-lookup"><span data-stu-id="78b37-109">A value of WAIT_ALERTABLE instructs the host to wake the task if `Alert` is called before `milliseconds` elapses.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="78b37-110">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="78b37-110">Return Value</span></span>  
  
|<span data-ttu-id="78b37-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="78b37-111">HRESULT</span></span>|<span data-ttu-id="78b37-112">Description</span><span class="sxs-lookup"><span data-stu-id="78b37-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="78b37-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="78b37-113">S_OK</span></span>|<span data-ttu-id="78b37-114">`Join` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="78b37-114">`Join` returned successfully.</span></span>|  
|<span data-ttu-id="78b37-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="78b37-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="78b37-116">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="78b37-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="78b37-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="78b37-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="78b37-118">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="78b37-118">The call timed out.</span></span>|  
|<span data-ttu-id="78b37-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="78b37-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="78b37-120">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="78b37-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="78b37-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="78b37-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="78b37-122">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente sur celui-ci, ou l' `IHostTask` instance actuelle n’est pas associée à une tâche.</span><span class="sxs-lookup"><span data-stu-id="78b37-122">An event was canceled while a blocked thread or fiber was waiting on it, or the current `IHostTask` instance is not associated with a task.</span></span>|  
|<span data-ttu-id="78b37-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="78b37-123">E_FAIL</span></span>|<span data-ttu-id="78b37-124">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="78b37-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="78b37-125">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="78b37-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="78b37-126">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="78b37-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="78b37-127">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="78b37-127">Requirements</span></span>  

 <span data-ttu-id="78b37-128">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78b37-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78b37-129">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="78b37-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="78b37-130">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="78b37-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="78b37-131">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78b37-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78b37-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="78b37-132">See also</span></span>

- [<span data-ttu-id="78b37-133">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="78b37-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="78b37-134">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="78b37-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="78b37-135">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="78b37-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="78b37-136">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="78b37-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="78b37-137">WAIT_OPTION, énumération</span><span class="sxs-lookup"><span data-stu-id="78b37-137">WAIT_OPTION Enumeration</span></span>](wait-option-enumeration.md)
