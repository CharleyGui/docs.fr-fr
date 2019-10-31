---
title: ICLRTaskManager::CreateTask, méthode
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.CreateTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::CreateTask
helpviewer_keywords:
- ICLRTaskManager::CreateTask method [.NET Framework hosting]
- CreateTask method, ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: eea570d9-2e53-4320-9ea0-eb777bf9dcf3
topic_type:
- apiref
ms.openlocfilehash: fcb78dd5374ff97f23d7dfea63fe33fa96836958
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124536"
---
# <a name="iclrtaskmanagercreatetask-method"></a><span data-ttu-id="0445c-102">ICLRTaskManager::CreateTask, méthode</span><span class="sxs-lookup"><span data-stu-id="0445c-102">ICLRTaskManager::CreateTask Method</span></span>
<span data-ttu-id="0445c-103">Demande explicitement que le common language runtime (CLR) crée une nouvelle tâche.</span><span class="sxs-lookup"><span data-stu-id="0445c-103">Requests explicitly that the common language runtime (CLR) create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0445c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0445c-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateTask (  
    [out] ICLRTask **pTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0445c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0445c-105">Parameters</span></span>  
 `pTask`  
 <span data-ttu-id="0445c-106">à Pointeur vers l’adresse d’un [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)nouvellement créé, ou null, si la tâche n’a pas pu être créée.</span><span class="sxs-lookup"><span data-stu-id="0445c-106">[out] A pointer to the address of a newly created [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md), or null, if the task could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0445c-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="0445c-107">Return Value</span></span>  
  
|<span data-ttu-id="0445c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0445c-108">HRESULT</span></span>|<span data-ttu-id="0445c-109">Description</span><span class="sxs-lookup"><span data-stu-id="0445c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0445c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0445c-110">S_OK</span></span>|<span data-ttu-id="0445c-111">La méthode a été retournée avec succès.</span><span class="sxs-lookup"><span data-stu-id="0445c-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="0445c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0445c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0445c-113">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="0445c-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0445c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0445c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0445c-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="0445c-115">The call timed out.</span></span>|  
|<span data-ttu-id="0445c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0445c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0445c-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="0445c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0445c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0445c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0445c-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="0445c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0445c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0445c-120">E_FAIL</span></span>|<span data-ttu-id="0445c-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="0445c-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0445c-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="0445c-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0445c-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0445c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0445c-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="0445c-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="0445c-125">La mémoire disponible est insuffisante pour allouer la ressource demandée.</span><span class="sxs-lookup"><span data-stu-id="0445c-125">Not enough memory is available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0445c-126">Notes</span><span class="sxs-lookup"><span data-stu-id="0445c-126">Remarks</span></span>  
 <span data-ttu-id="0445c-127">Le CLR crée automatiquement une nouvelle tâche lors de l’initialisation, lorsque le code utilisateur crée un thread à l’aide de types dans l’espace de noms <xref:System.Threading> ou lorsque la taille du pool de threads augmente.</span><span class="sxs-lookup"><span data-stu-id="0445c-127">The CLR creates a new task automatically upon initialization, when user code creates a thread by using types in the <xref:System.Threading> namespace, or when the size of the thread pool is increased.</span></span> <span data-ttu-id="0445c-128">Elle crée également des tâches lorsque du code non managé effectue un appel à une fonction managée.</span><span class="sxs-lookup"><span data-stu-id="0445c-128">It also creates tasks when unmanaged code makes a call to a managed function.</span></span>  
  
 <span data-ttu-id="0445c-129">`CreateTask` permet à l’hôte de faire une demande explicite que le CLR crée une nouvelle tâche.</span><span class="sxs-lookup"><span data-stu-id="0445c-129">`CreateTask` allows the host to make an explicit request that the CLR create a new task.</span></span> <span data-ttu-id="0445c-130">Par exemple, l’hôte peut appeler cette méthode pour préinitialiser les structures de données.</span><span class="sxs-lookup"><span data-stu-id="0445c-130">For example, the host can invoke this method to preinitialize data structures.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0445c-131">La nouvelle tâche est retournée dans un état suspendu et reste suspendue jusqu’à ce que l’hôte appelle explicitement [IHostTask :: Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="0445c-131">The new task is returned in a suspended state and remains suspended until the host explicitly calls [IHostTask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0445c-132">spécifications</span><span class="sxs-lookup"><span data-stu-id="0445c-132">Requirements</span></span>  
 <span data-ttu-id="0445c-133">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0445c-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0445c-134">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0445c-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0445c-135">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0445c-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0445c-136">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0445c-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0445c-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0445c-137">See also</span></span>

- [<span data-ttu-id="0445c-138">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="0445c-138">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="0445c-139">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="0445c-139">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="0445c-140">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="0445c-140">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="0445c-141">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="0445c-141">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
