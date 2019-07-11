---
title: EMemoryCriticalLevel, énumération
ms.date: 03/30/2017
api_name:
- EMemoryCriticalLevel
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EMemoryCriticalLevel
helpviewer_keywords:
- EMemoryCriticalLevel enumeration [.NET Framework hosting]
ms.assetid: 2ca8a7a2-7b54-4ba3-8e73-277c7df485f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 26b3761ab49f36c5f687ff2c62882667e044d299
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774219"
---
# <a name="ememorycriticallevel-enumeration"></a><span data-ttu-id="a008a-102">EMemoryCriticalLevel, énumération</span><span class="sxs-lookup"><span data-stu-id="a008a-102">EMemoryCriticalLevel Enumeration</span></span>
<span data-ttu-id="a008a-103">Contient des valeurs qui indiquent l’impact d’un échec lors de l’allocation de mémoire spécifique a été demandée mais ne peut pas être satisfaite.</span><span class="sxs-lookup"><span data-stu-id="a008a-103">Contains values that indicate the impact of a failure when a specific memory allocation has been requested but cannot be satisfied.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a008a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a008a-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eTaskCritical      = 0,  
    eAppDomainCritical = 1,  
    eProcessCritical   = 2  
} EMemoryCriticalLevel;  
```  
  
## <a name="members"></a><span data-ttu-id="a008a-105">Membres</span><span class="sxs-lookup"><span data-stu-id="a008a-105">Members</span></span>  
  
|<span data-ttu-id="a008a-106">Membre</span><span class="sxs-lookup"><span data-stu-id="a008a-106">Member</span></span>|<span data-ttu-id="a008a-107">Description</span><span class="sxs-lookup"><span data-stu-id="a008a-107">Description</span></span>|  
|------------|-----------------|  
|`eAppDomainCritical`|<span data-ttu-id="a008a-108">Indique que l’allocation est critique pour l’exécution de code managé dans le domaine qui a demandé l’allocation.</span><span class="sxs-lookup"><span data-stu-id="a008a-108">Indicates that the allocation is critical for executing managed code in the domain that has requested the allocation.</span></span> <span data-ttu-id="a008a-109">Si la mémoire ne peut pas être allouée, le CLR ne garantit pas que le domaine est toujours utilisable.</span><span class="sxs-lookup"><span data-stu-id="a008a-109">If memory cannot be allocated, the CLR cannot guarantee that the domain is still usable.</span></span> <span data-ttu-id="a008a-110">L’hôte décide d’action à entreprendre lorsque l’allocation ne peut pas être satisfaite.</span><span class="sxs-lookup"><span data-stu-id="a008a-110">The host decides what action to take when the allocation cannot be satisfied.</span></span> <span data-ttu-id="a008a-111">Il peut indiquer au CLR pour abandonner la `AppDomain` automatiquement, ou lui permettre de poursuivre son exécution en appelant des méthodes sur [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="a008a-111">It can instruct the CLR to abort the `AppDomain` automatically, or allow it to keep running by calling methods on [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span></span>|  
|`eProcessCritical`|<span data-ttu-id="a008a-112">Indique que l’allocation est critique pour l’exécution du code managé dans le processus.</span><span class="sxs-lookup"><span data-stu-id="a008a-112">Indicates that the allocation is critical to the execution of managed code in the process.</span></span> <span data-ttu-id="a008a-113">Cette valeur est utilisée lors du démarrage et lors de l’exécution des finaliseurs.</span><span class="sxs-lookup"><span data-stu-id="a008a-113">This value is used during startup and when running finalizers.</span></span> <span data-ttu-id="a008a-114">Si la mémoire ne peut pas être allouée, le CLR ne peut pas fonctionner dans le processus.</span><span class="sxs-lookup"><span data-stu-id="a008a-114">If memory cannot be allocated, the CLR cannot operate in the process.</span></span> <span data-ttu-id="a008a-115">Si l’allocation échoue, le CLR est désactivé.</span><span class="sxs-lookup"><span data-stu-id="a008a-115">If the allocation fails, the CLR is effectively disabled.</span></span> <span data-ttu-id="a008a-116">Tous les appels ultérieurs dans le CLR échouent avec HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a008a-116">All subsequent calls into the CLR fail with HOST_E_CLRNOTAVAILABLE.</span></span>|  
|`eTaskCritical`|<span data-ttu-id="a008a-117">Indique que l’allocation est critique pour l’exécution de la tâche qui a demandé l’allocation.</span><span class="sxs-lookup"><span data-stu-id="a008a-117">Indicates that the allocation is critical to running the task that has requested the allocation.</span></span> <span data-ttu-id="a008a-118">Si la mémoire ne peut pas être allouée, le CLR ne garantit pas que la tâche peut être exécutée.</span><span class="sxs-lookup"><span data-stu-id="a008a-118">If memory cannot be allocated, the CLR cannot guarantee that the task can be executed.</span></span> <span data-ttu-id="a008a-119">En cas de défaillance, le CLR lève une <xref:System.Threading.ThreadAbortException> sur le thread de système d’opération physique.</span><span class="sxs-lookup"><span data-stu-id="a008a-119">In the event of failure, the CLR raises a <xref:System.Threading.ThreadAbortException> on the physical operation system thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a008a-120">Notes</span><span class="sxs-lookup"><span data-stu-id="a008a-120">Remarks</span></span>  
 <span data-ttu-id="a008a-121">Les méthodes d’allocation de mémoire définies dans le [IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md) et [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) interfaces prennent un paramètre de ce type.</span><span class="sxs-lookup"><span data-stu-id="a008a-121">The memory allocation methods defined in the [IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md) and [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) interfaces take a parameter of this type.</span></span> <span data-ttu-id="a008a-122">Selon la gravité d’une défaillance, un hôte peut décider à échouer la demande d’allocation immédiatement ou attendre jusqu'à ce qu’il peut être satisfaite.</span><span class="sxs-lookup"><span data-stu-id="a008a-122">Depending upon the severity of a failure, a host can decide whether to fail the allocation request immediately or to wait until it can be satisfied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a008a-123">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a008a-123">Requirements</span></span>  
 <span data-ttu-id="a008a-124">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a008a-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a008a-125">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a008a-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a008a-126">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a008a-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a008a-127">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a008a-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a008a-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a008a-128">See also</span></span>

- [<span data-ttu-id="a008a-129">ICLRMemoryNotificationCallback, interface</span><span class="sxs-lookup"><span data-stu-id="a008a-129">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
- [<span data-ttu-id="a008a-130">Énumérations d’hébergement</span><span class="sxs-lookup"><span data-stu-id="a008a-130">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
