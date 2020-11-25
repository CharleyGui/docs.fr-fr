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
ms.openlocfilehash: 7fdf25d44bdf630e306cf0f5dcb3387a3b0f7c76
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731681"
---
# <a name="ihosttaskmanagercreatetask-method"></a><span data-ttu-id="21341-102">IHostTaskManager::CreateTask, méthode</span><span class="sxs-lookup"><span data-stu-id="21341-102">IHostTaskManager::CreateTask Method</span></span>

<span data-ttu-id="21341-103">Demande que l’hôte crée une nouvelle tâche.</span><span class="sxs-lookup"><span data-stu-id="21341-103">Requests that the host create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21341-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21341-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateTask (  
    [in]  DWORD stacksize,
    [in]  LPTHREAD_START_ROUTINE pStartAddress,  
    [in]  PVOID pParameter,  
    [out] IHostTask **ppTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21341-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="21341-105">Parameters</span></span>  

 `stacksize`  
 <span data-ttu-id="21341-106">dans Taille demandée, en octets, de la pile demandée, ou 0 (zéro) pour la taille par défaut.</span><span class="sxs-lookup"><span data-stu-id="21341-106">[in] The requested size, in bytes, of the requested stack, or 0 (zero) for the default size.</span></span>  
  
 `pStartAddress`  
 <span data-ttu-id="21341-107">dans Pointeur vers la fonction que la tâche doit exécuter.</span><span class="sxs-lookup"><span data-stu-id="21341-107">[in] A pointer to the function the task is to execute.</span></span>  
  
 `pParameter`  
 <span data-ttu-id="21341-108">dans Pointeur vers les données utilisateur à passer à la fonction, ou null si la fonction n’accepte aucun paramètre.</span><span class="sxs-lookup"><span data-stu-id="21341-108">[in] A pointer to the user data to be passed to the function, or null if the function takes no parameters.</span></span>  
  
 `ppTask`  
 <span data-ttu-id="21341-109">à Pointeur vers l’adresse d’une instance [IHostTask](ihosttask-interface.md) créée par l’hôte, ou null si la tâche ne peut pas être créée.</span><span class="sxs-lookup"><span data-stu-id="21341-109">[out] A pointer to the address of an [IHostTask](ihosttask-interface.md) instance created by the host, or null if the task cannot be created.</span></span> <span data-ttu-id="21341-110">La tâche reste dans un état suspendu jusqu’à ce qu’elle soit explicitement démarrée par un appel à [IHostTask :: Start](ihosttask-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="21341-110">The task remains in a suspended state until it is explicitly started by a call to [IHostTask::Start](ihosttask-start-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="21341-111">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="21341-111">Return Value</span></span>  
  
|<span data-ttu-id="21341-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="21341-112">HRESULT</span></span>|<span data-ttu-id="21341-113">Description</span><span class="sxs-lookup"><span data-stu-id="21341-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="21341-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="21341-114">S_OK</span></span>|<span data-ttu-id="21341-115">`CreateTask` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="21341-115">`CreateTask` returned successfully.</span></span>|  
|<span data-ttu-id="21341-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="21341-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="21341-117">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="21341-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="21341-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="21341-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="21341-119">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="21341-119">The call timed out.</span></span>|  
|<span data-ttu-id="21341-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="21341-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="21341-121">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="21341-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="21341-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="21341-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="21341-123">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="21341-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="21341-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="21341-124">E_FAIL</span></span>|<span data-ttu-id="21341-125">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="21341-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="21341-126">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="21341-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="21341-127">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="21341-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="21341-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="21341-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="21341-129">Mémoire disponible insuffisante pour créer la tâche demandée.</span><span class="sxs-lookup"><span data-stu-id="21341-129">Not enough memory was available to create the requested task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21341-130">Remarques</span><span class="sxs-lookup"><span data-stu-id="21341-130">Remarks</span></span>  

 <span data-ttu-id="21341-131">Le CLR appelle `CreateTask` pour demander que l’hôte crée une nouvelle tâche.</span><span class="sxs-lookup"><span data-stu-id="21341-131">The CLR calls `CreateTask` to request that the host create a new task.</span></span> <span data-ttu-id="21341-132">L’hôte retourne un pointeur d’interface vers une `IHostTask` instance.</span><span class="sxs-lookup"><span data-stu-id="21341-132">The host returns an interface pointer to an `IHostTask` instance.</span></span> <span data-ttu-id="21341-133">La tâche retournée doit rester suspendue jusqu’à ce qu’elle soit explicitement démarrée par un appel à `IHostTask::Start` .</span><span class="sxs-lookup"><span data-stu-id="21341-133">The returned task must remain suspended until it is explicitly started by a call to `IHostTask::Start`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21341-134">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="21341-134">Requirements</span></span>  

 <span data-ttu-id="21341-135">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21341-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21341-136">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="21341-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="21341-137">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="21341-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="21341-138">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21341-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21341-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21341-139">See also</span></span>

- [<span data-ttu-id="21341-140">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="21341-140">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="21341-141">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="21341-141">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="21341-142">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="21341-142">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="21341-143">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="21341-143">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
