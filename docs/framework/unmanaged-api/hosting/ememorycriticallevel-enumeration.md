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
ms.openlocfilehash: 8364d38f7ab81b73fd8b47d2251bc0ff1b2c71e8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138250"
---
# <a name="ememorycriticallevel-enumeration"></a><span data-ttu-id="18342-102">EMemoryCriticalLevel, énumération</span><span class="sxs-lookup"><span data-stu-id="18342-102">EMemoryCriticalLevel Enumeration</span></span>
<span data-ttu-id="18342-103">Contient des valeurs qui indiquent l’impact d’un échec lorsqu’une allocation de mémoire spécifique a été demandée, mais ne peut pas être satisfaite.</span><span class="sxs-lookup"><span data-stu-id="18342-103">Contains values that indicate the impact of a failure when a specific memory allocation has been requested but cannot be satisfied.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18342-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="18342-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eTaskCritical      = 0,  
    eAppDomainCritical = 1,  
    eProcessCritical   = 2  
} EMemoryCriticalLevel;  
```  
  
## <a name="members"></a><span data-ttu-id="18342-105">Membres</span><span class="sxs-lookup"><span data-stu-id="18342-105">Members</span></span>  
  
|<span data-ttu-id="18342-106">Membre</span><span class="sxs-lookup"><span data-stu-id="18342-106">Member</span></span>|<span data-ttu-id="18342-107">Description</span><span class="sxs-lookup"><span data-stu-id="18342-107">Description</span></span>|  
|------------|-----------------|  
|`eAppDomainCritical`|<span data-ttu-id="18342-108">Indique que l’allocation est essentielle pour l’exécution du code managé dans le domaine qui a demandé l’allocation.</span><span class="sxs-lookup"><span data-stu-id="18342-108">Indicates that the allocation is critical for executing managed code in the domain that has requested the allocation.</span></span> <span data-ttu-id="18342-109">Si la mémoire ne peut pas être allouée, le CLR ne peut pas garantir que le domaine est toujours utilisable.</span><span class="sxs-lookup"><span data-stu-id="18342-109">If memory cannot be allocated, the CLR cannot guarantee that the domain is still usable.</span></span> <span data-ttu-id="18342-110">L’hôte décide de l’action à entreprendre lorsque l’allocation ne peut pas être satisfaite.</span><span class="sxs-lookup"><span data-stu-id="18342-110">The host decides what action to take when the allocation cannot be satisfied.</span></span> <span data-ttu-id="18342-111">Elle peut demander au CLR d’abandonner automatiquement le `AppDomain` ou de l’autoriser à continuer à s’exécuter en appelant des méthodes sur [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="18342-111">It can instruct the CLR to abort the `AppDomain` automatically, or allow it to keep running by calling methods on [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span></span>|  
|`eProcessCritical`|<span data-ttu-id="18342-112">Indique que l’allocation est essentielle à l’exécution du code managé dans le processus.</span><span class="sxs-lookup"><span data-stu-id="18342-112">Indicates that the allocation is critical to the execution of managed code in the process.</span></span> <span data-ttu-id="18342-113">Cette valeur est utilisée lors du démarrage et lors de l’exécution des finaliseurs.</span><span class="sxs-lookup"><span data-stu-id="18342-113">This value is used during startup and when running finalizers.</span></span> <span data-ttu-id="18342-114">Si la mémoire ne peut pas être allouée, le CLR ne peut pas fonctionner dans le processus.</span><span class="sxs-lookup"><span data-stu-id="18342-114">If memory cannot be allocated, the CLR cannot operate in the process.</span></span> <span data-ttu-id="18342-115">Si l’allocation échoue, le CLR est effectivement désactivé.</span><span class="sxs-lookup"><span data-stu-id="18342-115">If the allocation fails, the CLR is effectively disabled.</span></span> <span data-ttu-id="18342-116">Tous les appels suivants dans le CLR échouent avec HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="18342-116">All subsequent calls into the CLR fail with HOST_E_CLRNOTAVAILABLE.</span></span>|  
|`eTaskCritical`|<span data-ttu-id="18342-117">Indique que l’allocation est essentielle à l’exécution de la tâche qui a demandé l’allocation.</span><span class="sxs-lookup"><span data-stu-id="18342-117">Indicates that the allocation is critical to running the task that has requested the allocation.</span></span> <span data-ttu-id="18342-118">Si la mémoire ne peut pas être allouée, le CLR ne peut pas garantir que la tâche peut être exécutée.</span><span class="sxs-lookup"><span data-stu-id="18342-118">If memory cannot be allocated, the CLR cannot guarantee that the task can be executed.</span></span> <span data-ttu-id="18342-119">En cas de défaillance, le CLR déclenche une <xref:System.Threading.ThreadAbortException> sur le thread du système d’opération physique.</span><span class="sxs-lookup"><span data-stu-id="18342-119">In the event of failure, the CLR raises a <xref:System.Threading.ThreadAbortException> on the physical operation system thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18342-120">Notes</span><span class="sxs-lookup"><span data-stu-id="18342-120">Remarks</span></span>  
 <span data-ttu-id="18342-121">Les méthodes d’allocation de mémoire définies dans les interfaces [IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md) et [IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) prennent un paramètre de ce type.</span><span class="sxs-lookup"><span data-stu-id="18342-121">The memory allocation methods defined in the [IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md) and [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) interfaces take a parameter of this type.</span></span> <span data-ttu-id="18342-122">En fonction de la gravité d’un échec, un hôte peut décider s’il faut faire échouer la demande d’allocation immédiatement ou attendre qu’elle soit satisfaite.</span><span class="sxs-lookup"><span data-stu-id="18342-122">Depending upon the severity of a failure, a host can decide whether to fail the allocation request immediately or to wait until it can be satisfied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18342-123">spécifications</span><span class="sxs-lookup"><span data-stu-id="18342-123">Requirements</span></span>  
 <span data-ttu-id="18342-124">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18342-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18342-125">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="18342-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="18342-126">**Bibliothèque :** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="18342-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="18342-127">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18342-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18342-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="18342-128">See also</span></span>

- [<span data-ttu-id="18342-129">ICLRMemoryNotificationCallback, interface</span><span class="sxs-lookup"><span data-stu-id="18342-129">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
- [<span data-ttu-id="18342-130">Énumérations d’hébergement</span><span class="sxs-lookup"><span data-stu-id="18342-130">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
