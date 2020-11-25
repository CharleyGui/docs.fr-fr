---
title: ICLRSyncManager::GetRWLockOwnerNext, méthode
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.GetRWLockOwnerNext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::GetRWLockOwnerNext
helpviewer_keywords:
- ICLRSyncManager::GetRWLockOwnerNext method [.NET Framework hosting]
- GetRWLockOwnerNext method [.NET Framework hosting]
ms.assetid: 0e025b6a-280e-40a2-a2d0-b15f58777b81
topic_type:
- apiref
ms.openlocfilehash: 93a8b3884d831b7da412b6c53dd599af216cbbf2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728314"
---
# <a name="iclrsyncmanagergetrwlockownernext-method"></a><span data-ttu-id="8763c-102">ICLRSyncManager::GetRWLockOwnerNext, méthode</span><span class="sxs-lookup"><span data-stu-id="8763c-102">ICLRSyncManager::GetRWLockOwnerNext Method</span></span>

<span data-ttu-id="8763c-103">Obtient l’instance de [IHostTask](ihosttask-interface.md) suivante qui est bloquée sur le verrou de lecteur-writer actuel.</span><span class="sxs-lookup"><span data-stu-id="8763c-103">Gets the next [IHostTask](ihosttask-interface.md) instance that is blocked on the current reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8763c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8763c-104">Syntax</span></span>  
  
```cpp
HRESULT GetRWLockOwnerNext (  
    [in] SIZE_T       Iterator,  
    [out] IHostTask  *ppOwnerHostTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8763c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8763c-105">Parameters</span></span>  

 `Iterator`  
 <span data-ttu-id="8763c-106">dans Itérateur qui a été créé à l’aide d’un appel à [CreateRWLockOwnerIterator](iclrsyncmanager-createrwlockowneriterator-method.md).</span><span class="sxs-lookup"><span data-stu-id="8763c-106">[in] The iterator that was created by using a call to [CreateRWLockOwnerIterator](iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="8763c-107">à Pointeur vers le suivant `IHostTask` qui attend le verrou, ou null si aucune tâche n’est en attente.</span><span class="sxs-lookup"><span data-stu-id="8763c-107">[out] A pointer to the next `IHostTask` that is waiting on the lock, or null if no task is waiting.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8763c-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="8763c-108">Return Value</span></span>  
  
|<span data-ttu-id="8763c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8763c-109">HRESULT</span></span>|<span data-ttu-id="8763c-110">Description</span><span class="sxs-lookup"><span data-stu-id="8763c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8763c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="8763c-111">S_OK</span></span>|<span data-ttu-id="8763c-112">`GetRWLockOwnerNext` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="8763c-112">`GetRWLockOwnerNext` returned successfully.</span></span>|  
|<span data-ttu-id="8763c-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8763c-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8763c-114">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="8763c-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8763c-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8763c-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8763c-116">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="8763c-116">The call timed out.</span></span>|  
|<span data-ttu-id="8763c-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8763c-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8763c-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="8763c-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8763c-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8763c-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8763c-120">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="8763c-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8763c-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8763c-121">E_FAIL</span></span>|<span data-ttu-id="8763c-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="8763c-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8763c-123">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="8763c-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8763c-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8763c-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8763c-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="8763c-125">Remarks</span></span>  

 <span data-ttu-id="8763c-126">Si `ppOwnerHostTask` a la valeur null, l’itération s’est terminée et l’hôte doit appeler la méthode [DeleteRWLockOwnerIterator,](iclrsyncmanager-deleterwlockowneriterator-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8763c-126">If `ppOwnerHostTask` is set to null, the iteration has terminated, and the host should call the [DeleteRWLockOwnerIterator](iclrsyncmanager-deleterwlockowneriterator-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8763c-127">Le CLR appelle `AddRef` sur le `IHostTask` vers lequel `ppOwnerHostTask` pointe pour empêcher la sortie de cette tâche pendant que l’hôte maintient le pointeur.</span><span class="sxs-lookup"><span data-stu-id="8763c-127">The CLR calls `AddRef` on the `IHostTask` to which `ppOwnerHostTask` points to prevent this task from exiting while the host holds the pointer.</span></span> <span data-ttu-id="8763c-128">L’hôte doit appeler `Release` pour décrémenter le nombre de références lorsqu’il est terminé.</span><span class="sxs-lookup"><span data-stu-id="8763c-128">The host must call `Release` to decrement the reference count when it is finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8763c-129">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8763c-129">Requirements</span></span>  

 <span data-ttu-id="8763c-130">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8763c-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8763c-131">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8763c-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8763c-132">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8763c-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8763c-133">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8763c-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8763c-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8763c-134">See also</span></span>

- [<span data-ttu-id="8763c-135">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="8763c-135">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="8763c-136">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="8763c-136">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
