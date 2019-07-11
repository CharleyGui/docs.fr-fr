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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 888c9aa092d8eb01f2c0a7b915721828055a6f28
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773173"
---
# <a name="iclrdebugmanagerbeginconnection-method"></a><span data-ttu-id="bbd10-102">ICLRDebugManager::BeginConnection, méthode</span><span class="sxs-lookup"><span data-stu-id="bbd10-102">ICLRDebugManager::BeginConnection Method</span></span>
<span data-ttu-id="bbd10-103">Établit une nouvelle connexion entre l’hôte et le débogueur pour associer une liste de tâches à un identificateur et un nom convivial.</span><span class="sxs-lookup"><span data-stu-id="bbd10-103">Establishes a new connection between the host and the debugger to associate a list of tasks with an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbd10-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bbd10-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginConnection (  
    [in] CONNID dwConnectionId,  
    [in, string] wchar_t* szConnectionName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bbd10-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bbd10-105">Parameters</span></span>  
 `dwConnectionId`  
 <span data-ttu-id="bbd10-106">[in] Identificateur à associer à la liste des tâches de runtime (CLR) de langage courantes.</span><span class="sxs-lookup"><span data-stu-id="bbd10-106">[in] An identifier to associate with the list of common language runtime (CLR) tasks.</span></span>  
  
 `szConnectionName`  
 <span data-ttu-id="bbd10-107">[in] Un nom convivial à associer à la liste des tâches CLR.</span><span class="sxs-lookup"><span data-stu-id="bbd10-107">[in] A friendly name to associate with the list of CLR tasks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bbd10-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="bbd10-108">Return Value</span></span>  
  
|<span data-ttu-id="bbd10-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bbd10-109">HRESULT</span></span>|<span data-ttu-id="bbd10-110">Description</span><span class="sxs-lookup"><span data-stu-id="bbd10-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bbd10-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="bbd10-111">S_OK</span></span>|<span data-ttu-id="bbd10-112">`BeginConnection` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="bbd10-112">`BeginConnection` returned successfully.</span></span>|  
|<span data-ttu-id="bbd10-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bbd10-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bbd10-114">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="bbd10-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bbd10-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bbd10-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bbd10-116">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="bbd10-116">The call timed out.</span></span>|  
|<span data-ttu-id="bbd10-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bbd10-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bbd10-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="bbd10-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bbd10-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bbd10-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bbd10-120">Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="bbd10-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bbd10-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bbd10-121">E_FAIL</span></span>|<span data-ttu-id="bbd10-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="bbd10-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bbd10-123">Une fois une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus.</span><span class="sxs-lookup"><span data-stu-id="bbd10-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bbd10-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="bbd10-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="bbd10-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="bbd10-125">E_INVALIDARG</span></span>|<span data-ttu-id="bbd10-126">`dwConnectionId` est égal à zéro, ou `BeginConnection` a déjà été appelée à l’aide de ce `dwConnectionId` valeur, ou `szConnectionName` était null.</span><span class="sxs-lookup"><span data-stu-id="bbd10-126">`dwConnectionId` was zero, or `BeginConnection` was already called using this `dwConnectionId` value, or `szConnectionName` was null.</span></span>|  
|<span data-ttu-id="bbd10-127">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="bbd10-127">E_OUTOFMEMORY</span></span>|<span data-ttu-id="bbd10-128">Pas assez de mémoire peut être allouée pour contenir la liste des tâches associées à cette connexion.</span><span class="sxs-lookup"><span data-stu-id="bbd10-128">Not enough memory could be allocated to hold the list of tasks associated with this connection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bbd10-129">Notes</span><span class="sxs-lookup"><span data-stu-id="bbd10-129">Remarks</span></span>  
 <span data-ttu-id="bbd10-130">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) fournit trois méthodes, `BeginConnection`, [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), et [EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), permettant d’associer des listes de tâches à des identificateurs et noms conviviaux.</span><span class="sxs-lookup"><span data-stu-id="bbd10-130">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), and [EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bbd10-131">Ces trois méthodes doivent être appelées dans un ordre spécifique pour chaque ensemble de tâches.</span><span class="sxs-lookup"><span data-stu-id="bbd10-131">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="bbd10-132">`BeginConnection` est appelée en premier pour établir une nouvelle connexion.</span><span class="sxs-lookup"><span data-stu-id="bbd10-132">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="bbd10-133">`SetConnectionTasks` est ensuite appelée pour fournir l’ensemble des tâches à associer à cette connexion.</span><span class="sxs-lookup"><span data-stu-id="bbd10-133">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="bbd10-134">`EndConnection` est appelée en dernier pour supprimer l’association entre la liste des tâches et l’identificateur et le nom convivial. Toutefois, les appels pour des connexions différentes peuvent être imbriqués.</span><span class="sxs-lookup"><span data-stu-id="bbd10-134">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbd10-135">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="bbd10-135">Requirements</span></span>  
 <span data-ttu-id="bbd10-136">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bbd10-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbd10-137">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bbd10-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bbd10-138">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bbd10-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bbd10-139">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbd10-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbd10-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bbd10-140">See also</span></span>

- [<span data-ttu-id="bbd10-141">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="bbd10-141">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="bbd10-142">ICLRDebugManager, interface</span><span class="sxs-lookup"><span data-stu-id="bbd10-142">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="bbd10-143">EndConnection, méthode</span><span class="sxs-lookup"><span data-stu-id="bbd10-143">EndConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)
- [<span data-ttu-id="bbd10-144">SetConnectionTasks, méthode</span><span class="sxs-lookup"><span data-stu-id="bbd10-144">SetConnectionTasks Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)
- [<span data-ttu-id="bbd10-145">IHostControl, interface</span><span class="sxs-lookup"><span data-stu-id="bbd10-145">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
