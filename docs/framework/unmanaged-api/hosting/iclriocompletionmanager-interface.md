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
ms.openlocfilehash: 822b51531b7afc1c824c74b9580d9208e347e13b
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703554"
---
# <a name="iclriocompletionmanager-interface"></a><span data-ttu-id="e42fa-102">ICLRIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="e42fa-102">ICLRIoCompletionManager Interface</span></span>
<span data-ttu-id="e42fa-103">Implémente une méthode de rappel qui permet à l’hôte de notifier le common language runtime (CLR) de l’état des demandes d’e/s spécifiées.</span><span class="sxs-lookup"><span data-stu-id="e42fa-103">Implements a callback method that allows the host to notify the common language runtime (CLR) of the status of specified I/O requests.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e42fa-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="e42fa-104">Methods</span></span>  
  
|<span data-ttu-id="e42fa-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="e42fa-105">Method</span></span>|<span data-ttu-id="e42fa-106">Description</span><span class="sxs-lookup"><span data-stu-id="e42fa-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e42fa-107">OnComplete, méthode</span><span class="sxs-lookup"><span data-stu-id="e42fa-107">OnComplete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)|<span data-ttu-id="e42fa-108">Notifie le CLR de l’état d’une demande d’e/s qui a été effectuée à l’aide d’un appel à la méthode [IHostIoCompletionManager :: bind](ihostiocompletionmanager-bind-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e42fa-108">Notifies the CLR of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](ihostiocompletionmanager-bind-method.md) method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e42fa-109">Notes</span><span class="sxs-lookup"><span data-stu-id="e42fa-109">Remarks</span></span>  
 <span data-ttu-id="e42fa-110">L’hôte implémente l’abstraction de la fin d’exécution d’e/s à l’aide de l’interface [IHostIoCompletionManager](ihostiocompletionmanager-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="e42fa-110">The host implements the I/O completion abstraction by using the [IHostIoCompletionManager](ihostiocompletionmanager-interface.md) interface.</span></span> <span data-ttu-id="e42fa-111">Le CLR effectue des demandes d’e/s via cette interface, et l’hôte notifie l’exécution du résultat de ces requêtes à l’aide de l' `ICLRIoCompletionManager` interface.</span><span class="sxs-lookup"><span data-stu-id="e42fa-111">The CLR makes I/O requests through this interface, and the host notifies the runtime of the outcome of such requests by using the `ICLRIoCompletionManager` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e42fa-112">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="e42fa-112">Requirements</span></span>  
 <span data-ttu-id="e42fa-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e42fa-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e42fa-114">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e42fa-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e42fa-115">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e42fa-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e42fa-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e42fa-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e42fa-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e42fa-117">See also</span></span>

- [<span data-ttu-id="e42fa-118">IHostIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="e42fa-118">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="e42fa-119">IHostThreadPoolManager, interface</span><span class="sxs-lookup"><span data-stu-id="e42fa-119">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
- [<span data-ttu-id="e42fa-120">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="e42fa-120">Hosting Interfaces</span></span>](hosting-interfaces.md)
