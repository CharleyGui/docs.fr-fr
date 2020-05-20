---
title: ICLRDebugManager::SetConnectionTasks, méthode
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.SetConnectionTasks
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::SetConnectionTasks
helpviewer_keywords:
- SetConnectionTasks method [.NET Framework hosting]
- ICLRDebugManager::SetConnectionTasks method [.NET Framework hosting]
ms.assetid: b38bbc9a-872c-41a9-b8c3-ca011d25456a
topic_type:
- apiref
ms.openlocfilehash: 81b6f009ea61294f398a21c4def927ef2609f32b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615743"
---
# <a name="iclrdebugmanagersetconnectiontasks-method"></a><span data-ttu-id="c9973-102">ICLRDebugManager::SetConnectionTasks, méthode</span><span class="sxs-lookup"><span data-stu-id="c9973-102">ICLRDebugManager::SetConnectionTasks Method</span></span>
<span data-ttu-id="c9973-103">Associe une liste d’instances d' [ICLRTask](iclrtask-interface.md) à un identificateur et un nom convivial.</span><span class="sxs-lookup"><span data-stu-id="c9973-103">Associates a list of [ICLRTask](iclrtask-interface.md) instances with an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9973-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9973-104">Syntax</span></span>  
  
```cpp  
HRESULT SetConnectionTasks (  
    [in] CONNID id,  
    [in] DWORD dwCount,  
    [in, size_is(dwCount)] ICLRTask **ppCLRTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9973-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c9973-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="c9973-106">dans Identificateur spécifique à l’hôte pour la connexion avec laquelle associer le `ppCLRTask` tableau.</span><span class="sxs-lookup"><span data-stu-id="c9973-106">[in] The host-specific identifier for the connection with which to associate the `ppCLRTask` array.</span></span>  
  
 `dwCount`  
 <span data-ttu-id="c9973-107">dans Nombre de membres de `ppCLRTask` .</span><span class="sxs-lookup"><span data-stu-id="c9973-107">[in] The number of members of `ppCLRTask`.</span></span> <span data-ttu-id="c9973-108">Ce nombre doit être supérieur à zéro.</span><span class="sxs-lookup"><span data-stu-id="c9973-108">This number must be greater than zero.</span></span>  
  
 `ppCLRTask`  
 <span data-ttu-id="c9973-109">dans Tableau de `ICLRTask` pointeurs à associer à la connexion identifiée par `id` .</span><span class="sxs-lookup"><span data-stu-id="c9973-109">[in] An array of `ICLRTask` pointers to associate with the connection identified by `id`.</span></span> <span data-ttu-id="c9973-110">Ce tableau doit contenir au moins un membre.</span><span class="sxs-lookup"><span data-stu-id="c9973-110">This array must contain at least one member.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c9973-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c9973-111">Return Value</span></span>  
  
|<span data-ttu-id="c9973-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c9973-112">HRESULT</span></span>|<span data-ttu-id="c9973-113">Description</span><span class="sxs-lookup"><span data-stu-id="c9973-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c9973-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="c9973-114">S_OK</span></span>|<span data-ttu-id="c9973-115">`SetConnectionTasks`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="c9973-115">`SetConnectionTasks` returned successfully.</span></span>|  
|<span data-ttu-id="c9973-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c9973-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c9973-117">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="c9973-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c9973-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c9973-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c9973-119">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="c9973-119">The call timed out.</span></span>|  
|<span data-ttu-id="c9973-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c9973-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c9973-121">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="c9973-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c9973-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c9973-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c9973-123">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="c9973-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c9973-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c9973-124">E_FAIL</span></span>|<span data-ttu-id="c9973-125">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="c9973-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c9973-126">Une fois que la méthode a retourné E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="c9973-126">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c9973-127">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c9973-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c9973-128">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c9973-128">E_INVALIDARG</span></span>|<span data-ttu-id="c9973-129">[BeginConnection](iclrdebugmanager-beginconnection-method.md) n’a pas été appelé à l’aide de la valeur de `id` , ou `dwCount` ou `id` est égal à zéro, ou l’un des éléments de a la valeur `ppCLRTask` null.</span><span class="sxs-lookup"><span data-stu-id="c9973-129">[BeginConnection](iclrdebugmanager-beginconnection-method.md) has not been called using this value of `id`, or `dwCount` or `id` is zero, or one of the elements of `ppCLRTask` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9973-130">Notes</span><span class="sxs-lookup"><span data-stu-id="c9973-130">Remarks</span></span>  
 <span data-ttu-id="c9973-131">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) fournit trois méthodes, `BeginConnection` , `SetConnectionTasks` et [EndConnection](iclrdebugmanager-endconnection-method.md), pour associer des listes de tâches à des identificateurs et des noms conviviaux.</span><span class="sxs-lookup"><span data-stu-id="c9973-131">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, `SetConnectionTasks`, and [EndConnection](iclrdebugmanager-endconnection-method.md), for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c9973-132">Ces trois méthodes doivent être appelées dans un ordre spécifique pour chaque ensemble de tâches.</span><span class="sxs-lookup"><span data-stu-id="c9973-132">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="c9973-133">`BeginConnection`est appelé en premier pour établir une nouvelle connexion.</span><span class="sxs-lookup"><span data-stu-id="c9973-133">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="c9973-134">`SetConnectionTasks`est appelé ensuite pour fournir l’ensemble des tâches à associer à cette connexion.</span><span class="sxs-lookup"><span data-stu-id="c9973-134">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="c9973-135">`EndConnection`est appelé en dernier pour supprimer l’association entre la liste des tâches et l’identificateur et le nom convivial. Toutefois, les appels de différentes connexions peuvent être imbriqués.</span><span class="sxs-lookup"><span data-stu-id="c9973-135">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9973-136">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="c9973-136">Requirements</span></span>  
 <span data-ttu-id="c9973-137">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9973-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9973-138">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c9973-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c9973-139">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c9973-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c9973-140">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9973-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9973-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c9973-141">See also</span></span>

- [<span data-ttu-id="c9973-142">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="c9973-142">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="c9973-143">ICLRDebugManager, interface</span><span class="sxs-lookup"><span data-stu-id="c9973-143">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="c9973-144">BeginConnection, méthode</span><span class="sxs-lookup"><span data-stu-id="c9973-144">BeginConnection Method</span></span>](iclrdebugmanager-beginconnection-method.md)
- [<span data-ttu-id="c9973-145">EndConnection, méthode</span><span class="sxs-lookup"><span data-stu-id="c9973-145">EndConnection Method</span></span>](iclrdebugmanager-endconnection-method.md)
- [<span data-ttu-id="c9973-146">IHostControl, interface</span><span class="sxs-lookup"><span data-stu-id="c9973-146">IHostControl Interface</span></span>](ihostcontrol-interface.md)
