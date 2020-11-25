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
ms.openlocfilehash: 02facbb0ff1c0f8978d4f4f720ab370f70f07fe2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721684"
---
# <a name="igcthreadcontrol-interface"></a><span data-ttu-id="3f20b-102">IGCThreadControl, interface</span><span class="sxs-lookup"><span data-stu-id="3f20b-102">IGCThreadControl Interface</span></span>

<span data-ttu-id="3f20b-103">Fournit des méthodes pour participer à la planification des threads qui seraient sinon bloqués pour un garbage collection.</span><span class="sxs-lookup"><span data-stu-id="3f20b-103">Provides methods for participating in the scheduling of threads that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3f20b-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="3f20b-104">Methods</span></span>  
  
|<span data-ttu-id="3f20b-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="3f20b-105">Method</span></span>|<span data-ttu-id="3f20b-106">Description</span><span class="sxs-lookup"><span data-stu-id="3f20b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3f20b-107">SuspensionEnding, méthode</span><span class="sxs-lookup"><span data-stu-id="3f20b-107">SuspensionEnding Method</span></span>](igcthreadcontrol-suspensionending-method.md)|<span data-ttu-id="3f20b-108">Indique à l’hôte que le runtime reprend les threads après une garbage collection ou une autre suspension.</span><span class="sxs-lookup"><span data-stu-id="3f20b-108">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="3f20b-109">SuspensionStarting, méthode</span><span class="sxs-lookup"><span data-stu-id="3f20b-109">SuspensionStarting Method</span></span>](igcthreadcontrol-suspensionstarting-method.md)|<span data-ttu-id="3f20b-110">Indique à l’hôte que le runtime commence une suspension de thread pour une garbage collection ou une autre suspension.</span><span class="sxs-lookup"><span data-stu-id="3f20b-110">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="3f20b-111">ThreadIsBlockingForSuspension, méthode</span><span class="sxs-lookup"><span data-stu-id="3f20b-111">ThreadIsBlockingForSuspension Method</span></span>](igcthreadcontrol-threadisblockingforsuspension-method.md)|<span data-ttu-id="3f20b-112">Avertit l’hôte que le thread qui effectue l’appel est sur le présent bloqué, peut-être pour une garbage collection ou une autre suspension.</span><span class="sxs-lookup"><span data-stu-id="3f20b-112">Notifies the host that the thread making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3f20b-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3f20b-113">Requirements</span></span>  

 <span data-ttu-id="3f20b-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f20b-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f20b-115">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3f20b-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3f20b-116">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3f20b-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3f20b-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f20b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f20b-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f20b-118">See also</span></span>

- [<span data-ttu-id="3f20b-119">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="3f20b-119">Hosting Interfaces</span></span>](hosting-interfaces.md)
