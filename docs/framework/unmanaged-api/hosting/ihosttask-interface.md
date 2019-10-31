---
title: IHostTask, interface
ms.date: 03/30/2017
api_name:
- IHostTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask
helpviewer_keywords:
- IHostTask interface [.NET Framework hosting]
ms.assetid: a71dbbd5-64b8-47eb-9f03-8e8c85fbe2bc
topic_type:
- apiref
ms.openlocfilehash: 18dfee606f3d41229aa58a5b4bb9380b87c4efa5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121390"
---
# <a name="ihosttask-interface"></a><span data-ttu-id="93bc0-102">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="93bc0-102">IHostTask Interface</span></span>
<span data-ttu-id="93bc0-103">Fournit des méthodes qui permettent au common language runtime (CLR) de communiquer avec l’hôte pour gérer des tâches.</span><span class="sxs-lookup"><span data-stu-id="93bc0-103">Provides methods that allow the common language runtime (CLR) to communicate with the host to manage tasks.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="93bc0-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="93bc0-104">Methods</span></span>  
  
|<span data-ttu-id="93bc0-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="93bc0-105">Method</span></span>|<span data-ttu-id="93bc0-106">Description</span><span class="sxs-lookup"><span data-stu-id="93bc0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="93bc0-107">Alert, méthode</span><span class="sxs-lookup"><span data-stu-id="93bc0-107">Alert Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)|<span data-ttu-id="93bc0-108">Demande que l’hôte réactive la tâche représentée par l’instance de `IHostTask` actuelle, afin que la tâche puisse être abandonnée.</span><span class="sxs-lookup"><span data-stu-id="93bc0-108">Requests that the host wake the task represented by the current `IHostTask` instance, so the task can be aborted.</span></span>|  
|[<span data-ttu-id="93bc0-109">GetPriority, méthode</span><span class="sxs-lookup"><span data-stu-id="93bc0-109">GetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)|<span data-ttu-id="93bc0-110">Obtient le niveau de priorité de thread de la tâche représentée par l’instance de `IHostTask` actuelle.</span><span class="sxs-lookup"><span data-stu-id="93bc0-110">Gets the thread priority level of the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="93bc0-111">Join, méthode</span><span class="sxs-lookup"><span data-stu-id="93bc0-111">Join Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md)|<span data-ttu-id="93bc0-112">Bloque la tâche appelante jusqu’à ce que la tâche représentée par l’instance de `IHostTask` actuelle se termine, que l’intervalle de temps spécifié s’écoule, ou que la méthode [IHostTask :: Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) soit appelée.</span><span class="sxs-lookup"><span data-stu-id="93bc0-112">Blocks the calling task until the task represented by the current `IHostTask` instance completes, the specified time interval elapses, or [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) is called.</span></span>|  
|[<span data-ttu-id="93bc0-113">SetCLRTask, méthode</span><span class="sxs-lookup"><span data-stu-id="93bc0-113">SetCLRTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md)|<span data-ttu-id="93bc0-114">Associe une instance d' [interface ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) à l’instance de `IHostTask` actuelle.</span><span class="sxs-lookup"><span data-stu-id="93bc0-114">Associates an [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance with the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="93bc0-115">SetPriority, méthode</span><span class="sxs-lookup"><span data-stu-id="93bc0-115">SetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setpriority-method.md)|<span data-ttu-id="93bc0-116">Demande que l’hôte ajuste le niveau de priorité de thread pour la tâche représentée par l’instance de `IHostTask` actuelle.</span><span class="sxs-lookup"><span data-stu-id="93bc0-116">Requests that the host adjust the thread priority level for the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="93bc0-117">Start, méthode</span><span class="sxs-lookup"><span data-stu-id="93bc0-117">Start Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)|<span data-ttu-id="93bc0-118">Demande que l’hôte déplace la tâche représentée par l’instance de `IHostTask` actuelle d’un état suspendu à un état actif, dans lequel le code peut être exécuté.</span><span class="sxs-lookup"><span data-stu-id="93bc0-118">Requests that the host move the task represented by the current `IHostTask` instance from a suspended state to a live state, in which code can be executed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93bc0-119">Notes</span><span class="sxs-lookup"><span data-stu-id="93bc0-119">Remarks</span></span>  
 <span data-ttu-id="93bc0-120">Le CLR appelle des méthodes définies par `IHostTask` pour démarrer une tâche, définir son niveau de priorité de thread, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="93bc0-120">The CLR calls methods defined by `IHostTask` to start a task, set its thread priority level, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93bc0-121">spécifications</span><span class="sxs-lookup"><span data-stu-id="93bc0-121">Requirements</span></span>  
 <span data-ttu-id="93bc0-122">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93bc0-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93bc0-123">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="93bc0-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="93bc0-124">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="93bc0-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="93bc0-125">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93bc0-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93bc0-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="93bc0-126">See also</span></span>

- [<span data-ttu-id="93bc0-127">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="93bc0-127">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="93bc0-128">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="93bc0-128">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="93bc0-129">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="93bc0-129">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="93bc0-130">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="93bc0-130">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
