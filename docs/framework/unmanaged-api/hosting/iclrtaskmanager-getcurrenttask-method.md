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
ms.openlocfilehash: 9cb97d9f383b7b54b431457042c4c4a7fc9cd876
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762828"
---
# <a name="iclrtaskmanagergetcurrenttask-method"></a><span data-ttu-id="ecf87-102">ICLRTaskManager::GetCurrentTask, méthode</span><span class="sxs-lookup"><span data-stu-id="ecf87-102">ICLRTaskManager::GetCurrentTask Method</span></span>
<span data-ttu-id="ecf87-103">Obtient l’instance d' [ICLRTask](iclrtask-interface.md) en cours d’exécution sur le thread de système d’exploitation d’où provient l’appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="ecf87-103">Gets the [ICLRTask](iclrtask-interface.md) instance that is currently running on the operating system thread from which the method call originated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecf87-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ecf87-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentTask (  
    [out] ICLRTask **ppTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ecf87-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ecf87-105">Parameters</span></span>  
 `ppTask`  
 <span data-ttu-id="ecf87-106">à Pointeur vers l’adresse d’une `ICLRTask` instance en cours d’exécution sur le thread de système d’exploitation d’où provient l’appel ou valeur null si aucune tâche n’est en cours d’exécution sur ce thread.</span><span class="sxs-lookup"><span data-stu-id="ecf87-106">[out] A pointer to the address of an `ICLRTask` instance that is currently executing on the operating system thread from which the call originated, or null if no task is currently executing on this thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ecf87-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ecf87-107">Return Value</span></span>  
  
|<span data-ttu-id="ecf87-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ecf87-108">HRESULT</span></span>|<span data-ttu-id="ecf87-109">Description</span><span class="sxs-lookup"><span data-stu-id="ecf87-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ecf87-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="ecf87-110">S_OK</span></span>|<span data-ttu-id="ecf87-111">Retour réussi de la méthode.</span><span class="sxs-lookup"><span data-stu-id="ecf87-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="ecf87-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ecf87-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ecf87-113">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="ecf87-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ecf87-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ecf87-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ecf87-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="ecf87-115">The call timed out.</span></span>|  
|<span data-ttu-id="ecf87-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ecf87-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ecf87-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="ecf87-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ecf87-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ecf87-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ecf87-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="ecf87-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ecf87-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ecf87-120">E_FAIL</span></span>|<span data-ttu-id="ecf87-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="ecf87-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ecf87-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="ecf87-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ecf87-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ecf87-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ecf87-124">Notes</span><span class="sxs-lookup"><span data-stu-id="ecf87-124">Remarks</span></span>  
 <span data-ttu-id="ecf87-125">L' `ICLRTask` instance vers laquelle `ppTask` pointe le paramètre représente la tâche en cours d’exécution pour le CLR.</span><span class="sxs-lookup"><span data-stu-id="ecf87-125">The `ICLRTask` instance that the `ppTask` parameter points to represents the currently executing task for the CLR.</span></span> <span data-ttu-id="ecf87-126">L' `ICLRTask` instance est associée à une instance [IHostTask](ihosttask-interface.md) correspondante qui représente la tâche pour l’hôte.</span><span class="sxs-lookup"><span data-stu-id="ecf87-126">The `ICLRTask` instance is associated with a corresponding [IHostTask](ihosttask-interface.md) instance that represents the task for the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecf87-127">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="ecf87-127">Requirements</span></span>  
 <span data-ttu-id="ecf87-128">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecf87-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecf87-129">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ecf87-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ecf87-130">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ecf87-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ecf87-131">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecf87-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecf87-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ecf87-132">See also</span></span>

- [<span data-ttu-id="ecf87-133">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="ecf87-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="ecf87-134">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="ecf87-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="ecf87-135">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="ecf87-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="ecf87-136">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="ecf87-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
