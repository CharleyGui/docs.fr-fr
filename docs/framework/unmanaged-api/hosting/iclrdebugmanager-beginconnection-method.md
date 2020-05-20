---
title: ICLRDebugManager::BeginConnection, méthode
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.BeginConnection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::BeginConnection
helpviewer_keywords:
- ICLRDebugManager::BeginConnection method [.NET Framework hosting]
- BeginConnection method [.NET Framework hosting]
ms.assetid: bdd98146-ff4d-4150-a264-a4c1a32d31f3
topic_type:
- apiref
ms.openlocfilehash: fc25e250938d7549c7a9693bee937d4756268b93
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615811"
---
# <a name="iclrdebugmanagerbeginconnection-method"></a><span data-ttu-id="9441d-102">ICLRDebugManager::BeginConnection, méthode</span><span class="sxs-lookup"><span data-stu-id="9441d-102">ICLRDebugManager::BeginConnection Method</span></span>
<span data-ttu-id="9441d-103">Établit une nouvelle connexion entre l’hôte et le débogueur pour associer une liste de tâches à un identificateur et un nom convivial.</span><span class="sxs-lookup"><span data-stu-id="9441d-103">Establishes a new connection between the host and the debugger to associate a list of tasks with an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9441d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9441d-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginConnection (  
    [in] CONNID dwConnectionId,  
    [in, string] wchar_t* szConnectionName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9441d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9441d-105">Parameters</span></span>  
 `dwConnectionId`  
 <span data-ttu-id="9441d-106">dans Identificateur à associer à la liste des tâches common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="9441d-106">[in] An identifier to associate with the list of common language runtime (CLR) tasks.</span></span>  
  
 `szConnectionName`  
 <span data-ttu-id="9441d-107">dans Nom convivial à associer à la liste des tâches CLR.</span><span class="sxs-lookup"><span data-stu-id="9441d-107">[in] A friendly name to associate with the list of CLR tasks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9441d-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="9441d-108">Return Value</span></span>  
  
|<span data-ttu-id="9441d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9441d-109">HRESULT</span></span>|<span data-ttu-id="9441d-110">Description</span><span class="sxs-lookup"><span data-stu-id="9441d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9441d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="9441d-111">S_OK</span></span>|<span data-ttu-id="9441d-112">`BeginConnection`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="9441d-112">`BeginConnection` returned successfully.</span></span>|  
|<span data-ttu-id="9441d-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9441d-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9441d-114">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="9441d-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9441d-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9441d-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9441d-116">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="9441d-116">The call timed out.</span></span>|  
|<span data-ttu-id="9441d-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9441d-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9441d-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="9441d-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9441d-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9441d-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9441d-120">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="9441d-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9441d-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9441d-121">E_FAIL</span></span>|<span data-ttu-id="9441d-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="9441d-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9441d-123">Une fois que la méthode a retourné E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="9441d-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9441d-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9441d-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9441d-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="9441d-125">E_INVALIDARG</span></span>|<span data-ttu-id="9441d-126">`dwConnectionId`était égal à zéro, ou `BeginConnection` a déjà été appelé à l’aide `dwConnectionId` de cette valeur, ou `szConnectionName` était null.</span><span class="sxs-lookup"><span data-stu-id="9441d-126">`dwConnectionId` was zero, or `BeginConnection` was already called using this `dwConnectionId` value, or `szConnectionName` was null.</span></span>|  
|<span data-ttu-id="9441d-127">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="9441d-127">E_OUTOFMEMORY</span></span>|<span data-ttu-id="9441d-128">La mémoire peut être allouée pour contenir la liste des tâches associées à cette connexion.</span><span class="sxs-lookup"><span data-stu-id="9441d-128">Not enough memory could be allocated to hold the list of tasks associated with this connection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9441d-129">Notes</span><span class="sxs-lookup"><span data-stu-id="9441d-129">Remarks</span></span>  
 <span data-ttu-id="9441d-130">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) fournit trois méthodes, `BeginConnection` , [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)et [EndConnection](iclrdebugmanager-endconnection-method.md), pour associer des listes de tâches à des identificateurs et des noms conviviaux.</span><span class="sxs-lookup"><span data-stu-id="9441d-130">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), and [EndConnection](iclrdebugmanager-endconnection-method.md), for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9441d-131">Ces trois méthodes doivent être appelées dans un ordre spécifique pour chaque ensemble de tâches.</span><span class="sxs-lookup"><span data-stu-id="9441d-131">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="9441d-132">`BeginConnection`est appelé en premier pour établir une nouvelle connexion.</span><span class="sxs-lookup"><span data-stu-id="9441d-132">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="9441d-133">`SetConnectionTasks`est appelé ensuite pour fournir l’ensemble des tâches à associer à cette connexion.</span><span class="sxs-lookup"><span data-stu-id="9441d-133">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="9441d-134">`EndConnection`est appelé en dernier pour supprimer l’association entre la liste des tâches et l’identificateur et le nom convivial. Toutefois, les appels de différentes connexions peuvent être imbriqués.</span><span class="sxs-lookup"><span data-stu-id="9441d-134">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9441d-135">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="9441d-135">Requirements</span></span>  
 <span data-ttu-id="9441d-136">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9441d-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9441d-137">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9441d-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9441d-138">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9441d-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9441d-139">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9441d-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9441d-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9441d-140">See also</span></span>

- [<span data-ttu-id="9441d-141">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="9441d-141">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="9441d-142">ICLRDebugManager, interface</span><span class="sxs-lookup"><span data-stu-id="9441d-142">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="9441d-143">EndConnection, méthode</span><span class="sxs-lookup"><span data-stu-id="9441d-143">EndConnection Method</span></span>](iclrdebugmanager-endconnection-method.md)
- [<span data-ttu-id="9441d-144">SetConnectionTasks, méthode</span><span class="sxs-lookup"><span data-stu-id="9441d-144">SetConnectionTasks Method</span></span>](iclrdebugmanager-setconnectiontasks-method.md)
- [<span data-ttu-id="9441d-145">IHostControl, interface</span><span class="sxs-lookup"><span data-stu-id="9441d-145">IHostControl Interface</span></span>](ihostcontrol-interface.md)
