---
title: IHostTaskManager::CreateTask, méthode
ms.date: 03/30/2017
api_name:
- IHostTaskManager.CreateTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::CreateTask
helpviewer_keywords:
- CreateTask method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::CreateTask method [.NET Framework hosting]
ms.assetid: a6f8ad36-61e1-42b0-9db2-add575646d18
topic_type:
- apiref
ms.openlocfilehash: fef2f56fd000a8610a40661a30aa306ae5a7884e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178000"
---
# <a name="ihosttaskmanagercreatetask-method"></a><span data-ttu-id="e7e74-102">IHostTaskManager::CreateTask, méthode</span><span class="sxs-lookup"><span data-stu-id="e7e74-102">IHostTaskManager::CreateTask Method</span></span>
<span data-ttu-id="e7e74-103">Demande que l’hôte crée une nouvelle tâche.</span><span class="sxs-lookup"><span data-stu-id="e7e74-103">Requests that the host create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7e74-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7e74-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateTask (  
    [in]  DWORD stacksize,
    [in]  LPTHREAD_START_ROUTINE pStartAddress,  
    [in]  PVOID pParameter,  
    [out] IHostTask **ppTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7e74-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e7e74-105">Parameters</span></span>  
 `stacksize`  
 <span data-ttu-id="e7e74-106">[dans] La taille demandée, dans les octets, de la pile demandée, ou 0 (zéro) pour la taille par défaut.</span><span class="sxs-lookup"><span data-stu-id="e7e74-106">[in] The requested size, in bytes, of the requested stack, or 0 (zero) for the default size.</span></span>  
  
 `pStartAddress`  
 <span data-ttu-id="e7e74-107">[dans] Un pointeur à la fonction de la tâche est d’exécuter.</span><span class="sxs-lookup"><span data-stu-id="e7e74-107">[in] A pointer to the function the task is to execute.</span></span>  
  
 `pParameter`  
 <span data-ttu-id="e7e74-108">[dans] Un pointeur sur les données de l’utilisateur à transmettre à la fonction, ou nul si la fonction ne prend aucun paramètre.</span><span class="sxs-lookup"><span data-stu-id="e7e74-108">[in] A pointer to the user data to be passed to the function, or null if the function takes no parameters.</span></span>  
  
 `ppTask`  
 <span data-ttu-id="e7e74-109">[out] Un pointeur à l’adresse d’une instance [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) créé par l’hôte, ou nul si la tâche ne peut pas être créée.</span><span class="sxs-lookup"><span data-stu-id="e7e74-109">[out] A pointer to the address of an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance created by the host, or null if the task cannot be created.</span></span> <span data-ttu-id="e7e74-110">La tâche reste dans un état suspendu jusqu’à ce qu’il soit explicitement commencé par un appel à [IHostTask::Démarrer](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="e7e74-110">The task remains in a suspended state until it is explicitly started by a call to [IHostTask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e7e74-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e7e74-111">Return Value</span></span>  
  
|<span data-ttu-id="e7e74-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e7e74-112">HRESULT</span></span>|<span data-ttu-id="e7e74-113">Description</span><span class="sxs-lookup"><span data-stu-id="e7e74-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e7e74-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="e7e74-114">S_OK</span></span>|<span data-ttu-id="e7e74-115">`CreateTask`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="e7e74-115">`CreateTask` returned successfully.</span></span>|  
|<span data-ttu-id="e7e74-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e7e74-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e7e74-117">L’heure courante de l’exécution de la langue (CLR) n’a pas été chargée dans un processus, ou le CLR est dans un état où il ne peut pas exécuter le code géré ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="e7e74-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e7e74-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e7e74-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e7e74-119">L’appel s’est fait chronométrer.</span><span class="sxs-lookup"><span data-stu-id="e7e74-119">The call timed out.</span></span>|  
|<span data-ttu-id="e7e74-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e7e74-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e7e74-121">L’appelant n’est pas propriétaire de la serrure.</span><span class="sxs-lookup"><span data-stu-id="e7e74-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e7e74-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e7e74-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e7e74-123">Un événement a été annulé alors qu’un fil bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="e7e74-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e7e74-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e7e74-124">E_FAIL</span></span>|<span data-ttu-id="e7e74-125">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="e7e74-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e7e74-126">Lorsqu’une méthode revient E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="e7e74-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e7e74-127">Les appels ultérieurs aux méthodes d’hébergement reviennent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e7e74-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e7e74-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="e7e74-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="e7e74-129">Pas assez de mémoire était disponible pour créer la tâche demandée.</span><span class="sxs-lookup"><span data-stu-id="e7e74-129">Not enough memory was available to create the requested task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7e74-130">Notes </span><span class="sxs-lookup"><span data-stu-id="e7e74-130">Remarks</span></span>  
 <span data-ttu-id="e7e74-131">Le CLR `CreateTask` appelle à demander à l’hôte de créer une nouvelle tâche.</span><span class="sxs-lookup"><span data-stu-id="e7e74-131">The CLR calls `CreateTask` to request that the host create a new task.</span></span> <span data-ttu-id="e7e74-132">L’hôte renvoie un `IHostTask` pointeur d’interface à une instance.</span><span class="sxs-lookup"><span data-stu-id="e7e74-132">The host returns an interface pointer to an `IHostTask` instance.</span></span> <span data-ttu-id="e7e74-133">La tâche retournée doit rester suspendue jusqu’à `IHostTask::Start`ce qu’elle soit explicitement commencée par un appel à .</span><span class="sxs-lookup"><span data-stu-id="e7e74-133">The returned task must remain suspended until it is explicitly started by a call to `IHostTask::Start`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7e74-134">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e7e74-134">Requirements</span></span>  
 <span data-ttu-id="e7e74-135">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7e74-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7e74-136">**En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor</span><span class="sxs-lookup"><span data-stu-id="e7e74-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e7e74-137">**Bibliothèque:** Inclus comme une ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e7e74-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e7e74-138">**.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7e74-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7e74-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7e74-139">See also</span></span>

- [<span data-ttu-id="e7e74-140">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="e7e74-140">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="e7e74-141">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="e7e74-141">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="e7e74-142">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="e7e74-142">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="e7e74-143">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="e7e74-143">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
