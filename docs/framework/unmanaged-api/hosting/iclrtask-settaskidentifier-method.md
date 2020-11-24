---
title: ICLRTask::SetTaskIdentifier, méthode
ms.date: 03/30/2017
api_name:
- ICLRTask.SetTaskIdentifier
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::SetTaskIdentifier
helpviewer_keywords:
- SetTaskIdentifier method [.NET Framework hosting]
- ICLRTask::SetTaskIdentifier method [.NET Framework hosting]
ms.assetid: bdb7f047-1e90-40fc-9e3b-d44a16509073
topic_type:
- apiref
ms.openlocfilehash: d1f731e00d4917b997dfba392cb9b6ce2afc082e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690744"
---
# <a name="iclrtasksettaskidentifier-method"></a><span data-ttu-id="ea66d-102">ICLRTask::SetTaskIdentifier, méthode</span><span class="sxs-lookup"><span data-stu-id="ea66d-102">ICLRTask::SetTaskIdentifier Method</span></span>

<span data-ttu-id="ea66d-103">Demande à l’common language runtime (CLR) d’associer la valeur d’identificateur spécifiée à la tâche représentée par l’instance d' [ICLRTask](iclrtask-interface.md) actuelle.</span><span class="sxs-lookup"><span data-stu-id="ea66d-103">Instructs the common language runtime (CLR) to associate the specified identifier value with the task represented by the current [ICLRTask](iclrtask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea66d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ea66d-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTaskIdentifier (  
    [in] DWORD Asked  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea66d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ea66d-105">Parameters</span></span>  

 `Asked`  
 <span data-ttu-id="ea66d-106">dans Identificateur unique de l’common language runtime à associer à la tâche représentée par l' `ICLRTask` instance actuelle.</span><span class="sxs-lookup"><span data-stu-id="ea66d-106">[in] The unique identifier for the common language runtime to associate with the task represented by the current `ICLRTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ea66d-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="ea66d-107">Return Value</span></span>  
  
|<span data-ttu-id="ea66d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ea66d-108">HRESULT</span></span>|<span data-ttu-id="ea66d-109">Description</span><span class="sxs-lookup"><span data-stu-id="ea66d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ea66d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="ea66d-110">S_OK</span></span>|<span data-ttu-id="ea66d-111">`SetTaskIdentifier` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="ea66d-111">`SetTaskIdentifier` returned successfully.</span></span>|  
|<span data-ttu-id="ea66d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ea66d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ea66d-113">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="ea66d-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ea66d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ea66d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ea66d-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="ea66d-115">The call timed out.</span></span>|  
|<span data-ttu-id="ea66d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ea66d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ea66d-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="ea66d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ea66d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ea66d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ea66d-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="ea66d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ea66d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ea66d-120">E_FAIL</span></span>|<span data-ttu-id="ea66d-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="ea66d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ea66d-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="ea66d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ea66d-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ea66d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ea66d-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="ea66d-124">Remarks</span></span>  

 <span data-ttu-id="ea66d-125">L’hôte peut associer un identificateur à une tâche pour faciliter l’intégration du CLR et de l’hôte dans un environnement de débogage.</span><span class="sxs-lookup"><span data-stu-id="ea66d-125">The host can associate an identifier with a task to help integrate the CLR and the host in a debugging environment.</span></span> <span data-ttu-id="ea66d-126">L’identificateur n’a aucune signification pour le CLR.</span><span class="sxs-lookup"><span data-stu-id="ea66d-126">The identifier has no meaning for the CLR.</span></span> <span data-ttu-id="ea66d-127">Le CLR le transmet à une application du débogueur.</span><span class="sxs-lookup"><span data-stu-id="ea66d-127">The CLR passes it along to a debugger application.</span></span> <span data-ttu-id="ea66d-128">Le débogueur peut utiliser cet identificateur pour associer une pile des appels CLR à une pile des appels de l’hôte, et permettre à leurs informations de traçage respectives d’être unifiées lorsqu’elles sont affichées dans l’interface utilisateur du débogueur.</span><span class="sxs-lookup"><span data-stu-id="ea66d-128">The debugger can use this identifier to associate a CLR call stack with a host call stack, and enable their respective trace information to be unified when viewed in the debugger's user interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea66d-129">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ea66d-129">Requirements</span></span>  

 <span data-ttu-id="ea66d-130">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea66d-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea66d-131">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ea66d-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ea66d-132">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ea66d-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ea66d-133">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea66d-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea66d-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ea66d-134">See also</span></span>

- [<span data-ttu-id="ea66d-135">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="ea66d-135">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="ea66d-136">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="ea66d-136">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="ea66d-137">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="ea66d-137">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="ea66d-138">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="ea66d-138">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
