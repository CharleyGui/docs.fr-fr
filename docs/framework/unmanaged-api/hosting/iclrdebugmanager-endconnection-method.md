---
title: ICLRDebugManager::EndConnection, méthode
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.EndConnection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::EndConnection
helpviewer_keywords:
- ICLRDebugManager::EndConnection method [.NET Framework hosting]
- EndConnection method [.NET Framework hosting]
ms.assetid: 89dc7363-2f29-4eb2-8f23-fccdda6a76a6
topic_type:
- apiref
ms.openlocfilehash: f524cadf77caec0823411784c68f339207433601
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615781"
---
# <a name="iclrdebugmanagerendconnection-method"></a><span data-ttu-id="7d1d4-102">ICLRDebugManager::EndConnection, méthode</span><span class="sxs-lookup"><span data-stu-id="7d1d4-102">ICLRDebugManager::EndConnection Method</span></span>
<span data-ttu-id="7d1d4-103">Supprime l’association entre une liste de tâches et un identificateur et un nom convivial.</span><span class="sxs-lookup"><span data-stu-id="7d1d4-103">Removes the association between a list of tasks and an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d1d4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d1d4-104">Syntax</span></span>  
  
```cpp  
HRESULT EndConnection (  
    [in] CONNID dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d1d4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7d1d4-105">Parameters</span></span>  
 `dwConnectionId`  
 <span data-ttu-id="7d1d4-106">dans Identificateur spécifique à l’hôte pour la connexion et la liste associée de tâches common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="7d1d4-106">[in] The host-specific identifier for the connection and the associated list of common language runtime (CLR) tasks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7d1d4-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="7d1d4-107">Return Value</span></span>  
  
|<span data-ttu-id="7d1d4-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7d1d4-108">HRESULT</span></span>|<span data-ttu-id="7d1d4-109">Description</span><span class="sxs-lookup"><span data-stu-id="7d1d4-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7d1d4-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7d1d4-110">S_OK</span></span>|<span data-ttu-id="7d1d4-111">`EndConnection`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="7d1d4-111">`EndConnection` returned successfully.</span></span>|  
|<span data-ttu-id="7d1d4-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7d1d4-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7d1d4-113">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="7d1d4-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7d1d4-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7d1d4-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7d1d4-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="7d1d4-115">The call timed out.</span></span>|  
|<span data-ttu-id="7d1d4-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7d1d4-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7d1d4-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="7d1d4-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7d1d4-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7d1d4-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7d1d4-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="7d1d4-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7d1d4-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7d1d4-120">E_FAIL</span></span>|<span data-ttu-id="7d1d4-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="7d1d4-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7d1d4-122">Une fois que la méthode a retourné E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="7d1d4-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7d1d4-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7d1d4-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7d1d4-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="7d1d4-124">E_INVALIDARG</span></span>|<span data-ttu-id="7d1d4-125">[BeginConnection](iclrdebugmanager-beginconnection-method.md) n’a jamais été appelé à l’aide `dwConnectionId` de, ou `dwConnectionId` était égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="7d1d4-125">[BeginConnection](iclrdebugmanager-beginconnection-method.md) was never called using `dwConnectionId`, or `dwConnectionId` was zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d1d4-126">Notes</span><span class="sxs-lookup"><span data-stu-id="7d1d4-126">Remarks</span></span>  
 <span data-ttu-id="7d1d4-127">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) fournit trois méthodes, `BeginConnection` , [SetConnectionTasks](iclrdebugmanager-setconnectiontasks-method.md)et `EndConnection` , pour associer des listes de tâches à des identificateurs et des noms conviviaux.</span><span class="sxs-lookup"><span data-stu-id="7d1d4-127">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, [SetConnectionTasks](iclrdebugmanager-setconnectiontasks-method.md), and `EndConnection`, for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7d1d4-128">Ces trois méthodes doivent être appelées dans un ordre spécifique pour chaque ensemble de tâches.</span><span class="sxs-lookup"><span data-stu-id="7d1d4-128">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="7d1d4-129">`BeginConnection`est appelé en premier pour établir une nouvelle connexion.</span><span class="sxs-lookup"><span data-stu-id="7d1d4-129">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="7d1d4-130">`SetConnectionTasks`est appelé ensuite pour fournir l’ensemble des tâches à associer à cette connexion.</span><span class="sxs-lookup"><span data-stu-id="7d1d4-130">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="7d1d4-131">`EndConnection`est appelé en dernier pour supprimer l’association entre la liste des tâches et l’identificateur et le nom convivial. Toutefois, les appels de différentes connexions peuvent être imbriqués.</span><span class="sxs-lookup"><span data-stu-id="7d1d4-131">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d1d4-132">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="7d1d4-132">Requirements</span></span>  
 <span data-ttu-id="7d1d4-133">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d1d4-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d1d4-134">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7d1d4-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7d1d4-135">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7d1d4-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7d1d4-136">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d1d4-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d1d4-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7d1d4-137">See also</span></span>

- [<span data-ttu-id="7d1d4-138">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="7d1d4-138">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="7d1d4-139">ICLRDebugManager, interface</span><span class="sxs-lookup"><span data-stu-id="7d1d4-139">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="7d1d4-140">BeginConnection, méthode</span><span class="sxs-lookup"><span data-stu-id="7d1d4-140">BeginConnection Method</span></span>](iclrdebugmanager-beginconnection-method.md)
- [<span data-ttu-id="7d1d4-141">SetConnectionTasks, méthode</span><span class="sxs-lookup"><span data-stu-id="7d1d4-141">SetConnectionTasks Method</span></span>](iclrdebugmanager-setconnectiontasks-method.md)
- [<span data-ttu-id="7d1d4-142">IHostControl, interface</span><span class="sxs-lookup"><span data-stu-id="7d1d4-142">IHostControl Interface</span></span>](ihostcontrol-interface.md)
