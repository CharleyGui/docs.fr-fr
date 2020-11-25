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
ms.openlocfilehash: 10efe853c9a7ad7676058bc01b07063c557623d8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699220"
---
# <a name="ihosttask-interface"></a><span data-ttu-id="741d2-102">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="741d2-102">IHostTask Interface</span></span>

<span data-ttu-id="741d2-103">Fournit des méthodes qui permettent au common language runtime (CLR) de communiquer avec l’hôte pour gérer des tâches.</span><span class="sxs-lookup"><span data-stu-id="741d2-103">Provides methods that allow the common language runtime (CLR) to communicate with the host to manage tasks.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="741d2-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="741d2-104">Methods</span></span>  
  
|<span data-ttu-id="741d2-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="741d2-105">Method</span></span>|<span data-ttu-id="741d2-106">Description</span><span class="sxs-lookup"><span data-stu-id="741d2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="741d2-107">Alert, méthode</span><span class="sxs-lookup"><span data-stu-id="741d2-107">Alert Method</span></span>](ihosttask-alert-method.md)|<span data-ttu-id="741d2-108">Demande que l’hôte réactive la tâche représentée par l' `IHostTask` instance actuelle, afin que la tâche puisse être abandonnée.</span><span class="sxs-lookup"><span data-stu-id="741d2-108">Requests that the host wake the task represented by the current `IHostTask` instance, so the task can be aborted.</span></span>|  
|[<span data-ttu-id="741d2-109">GetPriority, méthode</span><span class="sxs-lookup"><span data-stu-id="741d2-109">GetPriority Method</span></span>](ihosttask-getpriority-method.md)|<span data-ttu-id="741d2-110">Obtient le niveau de priorité de thread de la tâche représentée par l' `IHostTask` instance actuelle.</span><span class="sxs-lookup"><span data-stu-id="741d2-110">Gets the thread priority level of the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="741d2-111">Join, méthode</span><span class="sxs-lookup"><span data-stu-id="741d2-111">Join Method</span></span>](ihosttask-join-method.md)|<span data-ttu-id="741d2-112">Bloque la tâche appelante jusqu’à ce que la tâche représentée par l' `IHostTask` instance actuelle se termine, que l’intervalle de temps spécifié s’écoule, ou que la méthode [IHostTask :: Alert](ihosttask-alert-method.md) soit appelée.</span><span class="sxs-lookup"><span data-stu-id="741d2-112">Blocks the calling task until the task represented by the current `IHostTask` instance completes, the specified time interval elapses, or [IHostTask::Alert](ihosttask-alert-method.md) is called.</span></span>|  
|[<span data-ttu-id="741d2-113">SetCLRTask, méthode</span><span class="sxs-lookup"><span data-stu-id="741d2-113">SetCLRTask Method</span></span>](ihosttask-setclrtask-method.md)|<span data-ttu-id="741d2-114">Associe une instance d' [interface ICLRTask](iclrtask-interface.md) à l' `IHostTask` instance actuelle.</span><span class="sxs-lookup"><span data-stu-id="741d2-114">Associates an [ICLRTask Interface](iclrtask-interface.md) instance with the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="741d2-115">SetPriority, méthode</span><span class="sxs-lookup"><span data-stu-id="741d2-115">SetPriority Method</span></span>](ihosttask-setpriority-method.md)|<span data-ttu-id="741d2-116">Demande que l’hôte ajuste le niveau de priorité de thread pour la tâche représentée par l' `IHostTask` instance actuelle.</span><span class="sxs-lookup"><span data-stu-id="741d2-116">Requests that the host adjust the thread priority level for the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="741d2-117">Start, méthode</span><span class="sxs-lookup"><span data-stu-id="741d2-117">Start Method</span></span>](ihosttask-start-method.md)|<span data-ttu-id="741d2-118">Demande que l’hôte déplace la tâche représentée par l' `IHostTask` instance actuelle d’un état suspendu à un état actif, dans lequel le code peut être exécuté.</span><span class="sxs-lookup"><span data-stu-id="741d2-118">Requests that the host move the task represented by the current `IHostTask` instance from a suspended state to a live state, in which code can be executed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="741d2-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="741d2-119">Remarks</span></span>  

 <span data-ttu-id="741d2-120">Le CLR appelle des méthodes définies par `IHostTask` pour démarrer une tâche, définir son niveau de priorité de thread, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="741d2-120">The CLR calls methods defined by `IHostTask` to start a task, set its thread priority level, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="741d2-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="741d2-121">Requirements</span></span>  

 <span data-ttu-id="741d2-122">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="741d2-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="741d2-123">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="741d2-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="741d2-124">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="741d2-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="741d2-125">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="741d2-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="741d2-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="741d2-126">See also</span></span>

- [<span data-ttu-id="741d2-127">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="741d2-127">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="741d2-128">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="741d2-128">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="741d2-129">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="741d2-129">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="741d2-130">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="741d2-130">Hosting Interfaces</span></span>](hosting-interfaces.md)
