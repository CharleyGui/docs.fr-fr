---
title: ICLRIoCompletionManager, interface
ms.date: 03/30/2017
api_name:
- ICLRIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRIoCompletionManager
helpviewer_keywords:
- ICLRIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c6c3ace6-e5e7-4450-8cc5-a9a48208c493
topic_type:
- apiref
ms.openlocfilehash: b63d4269a8d48ee49016a4c51d63bf81bdba8da2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141029"
---
# <a name="iclriocompletionmanager-interface"></a><span data-ttu-id="5432d-102">ICLRIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="5432d-102">ICLRIoCompletionManager Interface</span></span>
<span data-ttu-id="5432d-103">Implémente une méthode de rappel qui permet à l’hôte de notifier le common language runtime (CLR) de l’état des demandes d’e/s spécifiées.</span><span class="sxs-lookup"><span data-stu-id="5432d-103">Implements a callback method that allows the host to notify the common language runtime (CLR) of the status of specified I/O requests.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5432d-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="5432d-104">Methods</span></span>  
  
|<span data-ttu-id="5432d-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="5432d-105">Method</span></span>|<span data-ttu-id="5432d-106">Description</span><span class="sxs-lookup"><span data-stu-id="5432d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5432d-107">OnComplete, méthode</span><span class="sxs-lookup"><span data-stu-id="5432d-107">OnComplete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)|<span data-ttu-id="5432d-108">Notifie le CLR de l’état d’une demande d’e/s qui a été effectuée à l’aide d’un appel à la méthode [IHostIoCompletionManager :: bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5432d-108">Notifies the CLR of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5432d-109">Notes</span><span class="sxs-lookup"><span data-stu-id="5432d-109">Remarks</span></span>  
 <span data-ttu-id="5432d-110">L’hôte implémente l’abstraction de la fin d’exécution d’e/s à l’aide de l’interface [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="5432d-110">The host implements the I/O completion abstraction by using the [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md) interface.</span></span> <span data-ttu-id="5432d-111">Le CLR effectue des demandes d’e/s via cette interface, et l’hôte notifie l’exécution du résultat de ces requêtes à l’aide de l’interface `ICLRIoCompletionManager`.</span><span class="sxs-lookup"><span data-stu-id="5432d-111">The CLR makes I/O requests through this interface, and the host notifies the runtime of the outcome of such requests by using the `ICLRIoCompletionManager` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5432d-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="5432d-112">Requirements</span></span>  
 <span data-ttu-id="5432d-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5432d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5432d-114">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5432d-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5432d-115">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5432d-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5432d-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5432d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5432d-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5432d-117">See also</span></span>

- [<span data-ttu-id="5432d-118">IHostIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="5432d-118">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="5432d-119">IHostThreadPoolManager, interface</span><span class="sxs-lookup"><span data-stu-id="5432d-119">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
- [<span data-ttu-id="5432d-120">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="5432d-120">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
