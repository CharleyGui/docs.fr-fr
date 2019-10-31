---
title: ICLRTaskManager, interface
ms.date: 03/30/2017
api_name:
- ICLRTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager
helpviewer_keywords:
- ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: 2bd55e0c-001b-41fd-b29d-f01670fe8216
topic_type:
- apiref
ms.openlocfilehash: e25a6a03a836b8b4964b8260c974c8e8d8d9998d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092185"
---
# <a name="iclrtaskmanager-interface"></a><span data-ttu-id="8d018-102">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="8d018-102">ICLRTaskManager Interface</span></span>
<span data-ttu-id="8d018-103">Fournit des méthodes qui permettent à l’hôte de demander explicitement que le common language runtime (CLR) crée une nouvelle tâche, d’obtenir la tâche en cours d’exécution et de définir la langue géographique et la culture de la tâche.</span><span class="sxs-lookup"><span data-stu-id="8d018-103">Provides methods that allow the host to request explicitly that the common language runtime (CLR) create a new task, get the currently executing task, and set the geographic language and culture for the task.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8d018-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="8d018-104">Methods</span></span>  
  
|<span data-ttu-id="8d018-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="8d018-105">Method</span></span>|<span data-ttu-id="8d018-106">Description</span><span class="sxs-lookup"><span data-stu-id="8d018-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8d018-107">CreateTask, méthode</span><span class="sxs-lookup"><span data-stu-id="8d018-107">CreateTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-createtask-method.md)|<span data-ttu-id="8d018-108">Demande explicitement que le CLR crée une nouvelle instance [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="8d018-108">Requests explicitly that the CLR create a new [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance.</span></span>|  
|[<span data-ttu-id="8d018-109">GetCurrentTask, méthode</span><span class="sxs-lookup"><span data-stu-id="8d018-109">GetCurrentTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttask-method.md)|<span data-ttu-id="8d018-110">Obtient l’instance de `ICLRTask` qui représente la tâche en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="8d018-110">Gets the `ICLRTask` instance that represents the task that is currently executing.</span></span>|  
|[<span data-ttu-id="8d018-111">GetCurrentTaskType, méthode</span><span class="sxs-lookup"><span data-stu-id="8d018-111">GetCurrentTaskType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttasktype-method.md)|<span data-ttu-id="8d018-112">Obtient le type de la tâche en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="8d018-112">Gets the type of the task that is currently executing.</span></span>|  
|[<span data-ttu-id="8d018-113">SetLocale, méthode</span><span class="sxs-lookup"><span data-stu-id="8d018-113">SetLocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setlocale-method.md)|<span data-ttu-id="8d018-114">Notifie le CLR que l’hôte a modifié l’identificateur de paramètres régionaux sur la tâche en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="8d018-114">Notifies the CLR that the host has modified the locale identifier on the currently executing task.</span></span>|  
|[<span data-ttu-id="8d018-115">SetUILocale, méthode</span><span class="sxs-lookup"><span data-stu-id="8d018-115">SetUILocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setuilocale-method.md)|<span data-ttu-id="8d018-116">Avertit le common language runtime que l’hôte a modifié l’identificateur de paramètres régionaux de l’interface utilisateur sur la tâche en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="8d018-116">Notifies the common language runtime that the host has modified the user interface locale identifier on the currently executing task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d018-117">Notes</span><span class="sxs-lookup"><span data-stu-id="8d018-117">Remarks</span></span>  
 <span data-ttu-id="8d018-118">Chaque tâche qui s’exécute dans un environnement hébergé a des représentations à la fois du côté hôte (une instance de [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) et du côté CLR (une instance d' [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)).</span><span class="sxs-lookup"><span data-stu-id="8d018-118">Each task that is running in a hosted environment has representations both on the host side (an instance of [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) and on the CLR side (an instance of [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)).</span></span> <span data-ttu-id="8d018-119">L’hôte ou le CLR peut lancer la création d’une tâche, mais la représentation côté hôte doit être associée à une représentation côté CLR correspondante pour garantir la réussite de la communication entre l’hôte et le CLR concernant la tâche.</span><span class="sxs-lookup"><span data-stu-id="8d018-119">Either the host or the CLR can initiate the creation of a task, but the host-side representation must be associated with a corresponding CLR-side representation to ensure successful communication between the host and the CLR regarding the task.</span></span> <span data-ttu-id="8d018-120">Les deux objets doivent être créés et instanciés pour que le code managé puisse s’exécuter sur un thread de système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="8d018-120">The two objects must be created and instantiated before managed code can execute on an operating system thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d018-121">spécifications</span><span class="sxs-lookup"><span data-stu-id="8d018-121">Requirements</span></span>  
 <span data-ttu-id="8d018-122">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d018-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d018-123">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8d018-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8d018-124">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8d018-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8d018-125">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d018-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d018-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d018-126">See also</span></span>

- [<span data-ttu-id="8d018-127">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="8d018-127">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="8d018-128">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="8d018-128">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="8d018-129">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="8d018-129">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="8d018-130">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="8d018-130">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
