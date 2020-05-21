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
ms.openlocfilehash: 9e26071181e8e0712c753fa03d5e16eb85e5ee68
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762826"
---
# <a name="iclrtaskmanager-interface"></a><span data-ttu-id="755fa-102">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="755fa-102">ICLRTaskManager Interface</span></span>
<span data-ttu-id="755fa-103">Fournit des méthodes qui permettent à l’hôte de demander explicitement que le common language runtime (CLR) crée une nouvelle tâche, d’obtenir la tâche en cours d’exécution et de définir la langue géographique et la culture de la tâche.</span><span class="sxs-lookup"><span data-stu-id="755fa-103">Provides methods that allow the host to request explicitly that the common language runtime (CLR) create a new task, get the currently executing task, and set the geographic language and culture for the task.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="755fa-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="755fa-104">Methods</span></span>  
  
|<span data-ttu-id="755fa-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="755fa-105">Method</span></span>|<span data-ttu-id="755fa-106">Description</span><span class="sxs-lookup"><span data-stu-id="755fa-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="755fa-107">CreateTask, méthode</span><span class="sxs-lookup"><span data-stu-id="755fa-107">CreateTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-createtask-method.md)|<span data-ttu-id="755fa-108">Demande explicitement que le CLR crée une nouvelle instance [ICLRTask](iclrtask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="755fa-108">Requests explicitly that the CLR create a new [ICLRTask](iclrtask-interface.md) instance.</span></span>|  
|[<span data-ttu-id="755fa-109">GetCurrentTask, méthode</span><span class="sxs-lookup"><span data-stu-id="755fa-109">GetCurrentTask Method</span></span>](iclrtaskmanager-getcurrenttask-method.md)|<span data-ttu-id="755fa-110">Obtient l' `ICLRTask` instance qui représente la tâche en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="755fa-110">Gets the `ICLRTask` instance that represents the task that is currently executing.</span></span>|  
|[<span data-ttu-id="755fa-111">GetCurrentTaskType, méthode</span><span class="sxs-lookup"><span data-stu-id="755fa-111">GetCurrentTaskType Method</span></span>](iclrtaskmanager-getcurrenttasktype-method.md)|<span data-ttu-id="755fa-112">Obtient le type de la tâche en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="755fa-112">Gets the type of the task that is currently executing.</span></span>|  
|[<span data-ttu-id="755fa-113">SetLocale, méthode</span><span class="sxs-lookup"><span data-stu-id="755fa-113">SetLocale Method</span></span>](iclrtaskmanager-setlocale-method.md)|<span data-ttu-id="755fa-114">Notifie le CLR que l’hôte a modifié l’identificateur de paramètres régionaux sur la tâche en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="755fa-114">Notifies the CLR that the host has modified the locale identifier on the currently executing task.</span></span>|  
|[<span data-ttu-id="755fa-115">SetUILocale, méthode</span><span class="sxs-lookup"><span data-stu-id="755fa-115">SetUILocale Method</span></span>](iclrtaskmanager-setuilocale-method.md)|<span data-ttu-id="755fa-116">Avertit le common language runtime que l’hôte a modifié l’identificateur de paramètres régionaux de l’interface utilisateur sur la tâche en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="755fa-116">Notifies the common language runtime that the host has modified the user interface locale identifier on the currently executing task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="755fa-117">Notes</span><span class="sxs-lookup"><span data-stu-id="755fa-117">Remarks</span></span>  
 <span data-ttu-id="755fa-118">Chaque tâche qui s’exécute dans un environnement hébergé a des représentations à la fois du côté hôte (une instance de [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) et du côté CLR (une instance d' [ICLRTask](iclrtask-interface.md)).</span><span class="sxs-lookup"><span data-stu-id="755fa-118">Each task that is running in a hosted environment has representations both on the host side (an instance of [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) and on the CLR side (an instance of [ICLRTask](iclrtask-interface.md)).</span></span> <span data-ttu-id="755fa-119">L’hôte ou le CLR peut lancer la création d’une tâche, mais la représentation côté hôte doit être associée à une représentation côté CLR correspondante pour garantir la réussite de la communication entre l’hôte et le CLR concernant la tâche.</span><span class="sxs-lookup"><span data-stu-id="755fa-119">Either the host or the CLR can initiate the creation of a task, but the host-side representation must be associated with a corresponding CLR-side representation to ensure successful communication between the host and the CLR regarding the task.</span></span> <span data-ttu-id="755fa-120">Les deux objets doivent être créés et instanciés pour que le code managé puisse s’exécuter sur un thread de système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="755fa-120">The two objects must be created and instantiated before managed code can execute on an operating system thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="755fa-121">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="755fa-121">Requirements</span></span>  
 <span data-ttu-id="755fa-122">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="755fa-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="755fa-123">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="755fa-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="755fa-124">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="755fa-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="755fa-125">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="755fa-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="755fa-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="755fa-126">See also</span></span>

- [<span data-ttu-id="755fa-127">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="755fa-127">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="755fa-128">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="755fa-128">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="755fa-129">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="755fa-129">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="755fa-130">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="755fa-130">Hosting Interfaces</span></span>](hosting-interfaces.md)
