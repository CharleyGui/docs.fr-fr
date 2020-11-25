---
title: ICLRTaskManager::GetCurrentTask, méthode
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.GetCurrentTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::GetCurrentTask
helpviewer_keywords:
- GetCurrentTask method, ICLRTaskManager interface [.NET Framework hosting]
- ICLRTaskManager::GetCurrentTask method [.NET Framework hosting]
ms.assetid: c0b82a9f-edc6-4878-9c81-48de53c02142
topic_type:
- apiref
ms.openlocfilehash: af855e3ba47dc329a4fb722c3e13d5f1816beba4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723270"
---
# <a name="iclrtaskmanagergetcurrenttask-method"></a><span data-ttu-id="97aee-102">ICLRTaskManager::GetCurrentTask, méthode</span><span class="sxs-lookup"><span data-stu-id="97aee-102">ICLRTaskManager::GetCurrentTask Method</span></span>

<span data-ttu-id="97aee-103">Obtient l’instance d' [ICLRTask](iclrtask-interface.md) en cours d’exécution sur le thread de système d’exploitation d’où provient l’appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="97aee-103">Gets the [ICLRTask](iclrtask-interface.md) instance that is currently running on the operating system thread from which the method call originated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97aee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="97aee-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentTask (  
    [out] ICLRTask **ppTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97aee-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="97aee-105">Parameters</span></span>  

 `ppTask`  
 <span data-ttu-id="97aee-106">à Pointeur vers l’adresse d’une `ICLRTask` instance en cours d’exécution sur le thread de système d’exploitation d’où provient l’appel ou valeur null si aucune tâche n’est en cours d’exécution sur ce thread.</span><span class="sxs-lookup"><span data-stu-id="97aee-106">[out] A pointer to the address of an `ICLRTask` instance that is currently executing on the operating system thread from which the call originated, or null if no task is currently executing on this thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="97aee-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="97aee-107">Return Value</span></span>  
  
|<span data-ttu-id="97aee-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="97aee-108">HRESULT</span></span>|<span data-ttu-id="97aee-109">Description</span><span class="sxs-lookup"><span data-stu-id="97aee-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="97aee-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="97aee-110">S_OK</span></span>|<span data-ttu-id="97aee-111">Retour réussi de la méthode.</span><span class="sxs-lookup"><span data-stu-id="97aee-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="97aee-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="97aee-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="97aee-113">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="97aee-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="97aee-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="97aee-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="97aee-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="97aee-115">The call timed out.</span></span>|  
|<span data-ttu-id="97aee-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="97aee-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="97aee-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="97aee-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="97aee-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="97aee-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="97aee-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="97aee-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="97aee-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="97aee-120">E_FAIL</span></span>|<span data-ttu-id="97aee-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="97aee-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="97aee-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="97aee-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="97aee-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="97aee-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97aee-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="97aee-124">Remarks</span></span>  

 <span data-ttu-id="97aee-125">L' `ICLRTask` instance vers laquelle `ppTask` pointe le paramètre représente la tâche en cours d’exécution pour le CLR.</span><span class="sxs-lookup"><span data-stu-id="97aee-125">The `ICLRTask` instance that the `ppTask` parameter points to represents the currently executing task for the CLR.</span></span> <span data-ttu-id="97aee-126">L' `ICLRTask` instance est associée à une instance [IHostTask](ihosttask-interface.md) correspondante qui représente la tâche pour l’hôte.</span><span class="sxs-lookup"><span data-stu-id="97aee-126">The `ICLRTask` instance is associated with a corresponding [IHostTask](ihosttask-interface.md) instance that represents the task for the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97aee-127">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="97aee-127">Requirements</span></span>  

 <span data-ttu-id="97aee-128">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97aee-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97aee-129">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="97aee-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="97aee-130">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="97aee-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="97aee-131">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97aee-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97aee-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="97aee-132">See also</span></span>

- [<span data-ttu-id="97aee-133">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="97aee-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="97aee-134">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="97aee-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="97aee-135">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="97aee-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="97aee-136">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="97aee-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
