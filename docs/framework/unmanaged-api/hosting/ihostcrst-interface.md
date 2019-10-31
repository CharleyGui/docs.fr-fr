---
title: IHostCrst, interface
ms.date: 03/30/2017
api_name:
- IHostCrst
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst
helpviewer_keywords:
- IHostCrst interface [.NET Framework hosting]
ms.assetid: ac298ebd-0815-47e4-a823-30b31baab903
topic_type:
- apiref
ms.openlocfilehash: 108492ba298e9f8429b2acd890ab3404365bc602
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130523"
---
# <a name="ihostcrst-interface"></a><span data-ttu-id="2301d-102">IHostCrst, interface</span><span class="sxs-lookup"><span data-stu-id="2301d-102">IHostCrst Interface</span></span>
<span data-ttu-id="2301d-103">Sert de représentation de l’hôte d’une section critique pour le Threading.</span><span class="sxs-lookup"><span data-stu-id="2301d-103">Serves as the host's representation of a critical section for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2301d-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="2301d-104">Methods</span></span>  
  
|<span data-ttu-id="2301d-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="2301d-105">Method</span></span>|<span data-ttu-id="2301d-106">Description</span><span class="sxs-lookup"><span data-stu-id="2301d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2301d-107">Enter, méthode</span><span class="sxs-lookup"><span data-stu-id="2301d-107">Enter Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-enter-method.md)|<span data-ttu-id="2301d-108">Entre dans la section critique.</span><span class="sxs-lookup"><span data-stu-id="2301d-108">Enters the critical section.</span></span>|  
|[<span data-ttu-id="2301d-109">Leave, méthode</span><span class="sxs-lookup"><span data-stu-id="2301d-109">Leave Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-leave-method.md)|<span data-ttu-id="2301d-110">Quitte la section critique.</span><span class="sxs-lookup"><span data-stu-id="2301d-110">Leaves the critical section.</span></span>|  
|[<span data-ttu-id="2301d-111">SetSpinCount, méthode</span><span class="sxs-lookup"><span data-stu-id="2301d-111">SetSpinCount Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-setspincount-method.md)|<span data-ttu-id="2301d-112">Définit le nombre de spins pour la section critique.</span><span class="sxs-lookup"><span data-stu-id="2301d-112">Sets the spin count for the critical section.</span></span>|  
|[<span data-ttu-id="2301d-113">TryEnter, méthode</span><span class="sxs-lookup"><span data-stu-id="2301d-113">TryEnter Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-tryenter-method.md)|<span data-ttu-id="2301d-114">Tente d’entrer dans la section critique et signale la réussite ou l’échec immédiatement.</span><span class="sxs-lookup"><span data-stu-id="2301d-114">Attempts to enter the critical section, and reports success or failure immediately.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2301d-115">Notes</span><span class="sxs-lookup"><span data-stu-id="2301d-115">Remarks</span></span>  
 <span data-ttu-id="2301d-116">`IHostCrst` permet au common language runtime (CLR) de communiquer directement avec la représentation de l’hôte d’une section critique, plutôt que d’utiliser des fonctions Win32 comme `EnterCriticalSection` ou `LeaveCriticalSection`.</span><span class="sxs-lookup"><span data-stu-id="2301d-116">`IHostCrst` allows the common language runtime (CLR) to communicate directly with the host's representation of a critical section, rather than using Win32 functions such as `EnterCriticalSection` or `LeaveCriticalSection`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2301d-117">spécifications</span><span class="sxs-lookup"><span data-stu-id="2301d-117">Requirements</span></span>  
 <span data-ttu-id="2301d-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2301d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2301d-119">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2301d-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2301d-120">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2301d-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2301d-121">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2301d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2301d-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2301d-122">See also</span></span>

- [<span data-ttu-id="2301d-123">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="2301d-123">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="2301d-124">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="2301d-124">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="2301d-125">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="2301d-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
