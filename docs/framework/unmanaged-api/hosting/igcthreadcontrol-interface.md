---
title: IGCThreadControl, interface
ms.date: 03/30/2017
api_name:
- IGCThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCThreadControl
helpviewer_keywords:
- IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 3ff04d75-85ac-4df9-886d-dbaa037c0552
topic_type:
- apiref
ms.openlocfilehash: 3aba31f60af25144b9f01aa9ca8cc633d4c1a438
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134800"
---
# <a name="igcthreadcontrol-interface"></a><span data-ttu-id="13510-102">IGCThreadControl, interface</span><span class="sxs-lookup"><span data-stu-id="13510-102">IGCThreadControl Interface</span></span>
<span data-ttu-id="13510-103">Fournit des méthodes pour participer à la planification des threads qui seraient sinon bloqués pour un garbage collection.</span><span class="sxs-lookup"><span data-stu-id="13510-103">Provides methods for participating in the scheduling of threads that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="13510-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="13510-104">Methods</span></span>  
  
|<span data-ttu-id="13510-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="13510-105">Method</span></span>|<span data-ttu-id="13510-106">Description</span><span class="sxs-lookup"><span data-stu-id="13510-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="13510-107">SuspensionEnding, méthode</span><span class="sxs-lookup"><span data-stu-id="13510-107">SuspensionEnding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionending-method.md)|<span data-ttu-id="13510-108">Indique à l’hôte que le runtime reprend les threads après une garbage collection ou une autre suspension.</span><span class="sxs-lookup"><span data-stu-id="13510-108">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="13510-109">SuspensionStarting, méthode</span><span class="sxs-lookup"><span data-stu-id="13510-109">SuspensionStarting Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionstarting-method.md)|<span data-ttu-id="13510-110">Indique à l’hôte que le runtime commence une suspension de thread pour une garbage collection ou une autre suspension.</span><span class="sxs-lookup"><span data-stu-id="13510-110">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="13510-111">ThreadIsBlockingForSuspension, méthode</span><span class="sxs-lookup"><span data-stu-id="13510-111">ThreadIsBlockingForSuspension Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md)|<span data-ttu-id="13510-112">Avertit l’hôte que le thread qui effectue l’appel est sur le présent bloqué, peut-être pour une garbage collection ou une autre suspension.</span><span class="sxs-lookup"><span data-stu-id="13510-112">Notifies the host that the thread making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="13510-113">spécifications</span><span class="sxs-lookup"><span data-stu-id="13510-113">Requirements</span></span>  
 <span data-ttu-id="13510-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13510-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13510-115">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="13510-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="13510-116">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="13510-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="13510-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13510-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13510-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="13510-118">See also</span></span>

- [<span data-ttu-id="13510-119">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="13510-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
