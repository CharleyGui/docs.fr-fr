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
ms.openlocfilehash: 359dd84032fce920892631dda2615f63aa54fa6b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504379"
---
# <a name="ememorycriticallevel-enumeration"></a><span data-ttu-id="cdd28-102">EMemoryCriticalLevel, énumération</span><span class="sxs-lookup"><span data-stu-id="cdd28-102">EMemoryCriticalLevel Enumeration</span></span>
<span data-ttu-id="cdd28-103">Contient des valeurs qui indiquent l’impact d’un échec lorsqu’une allocation de mémoire spécifique a été demandée, mais ne peut pas être satisfaite.</span><span class="sxs-lookup"><span data-stu-id="cdd28-103">Contains values that indicate the impact of a failure when a specific memory allocation has been requested but cannot be satisfied.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdd28-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cdd28-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eTaskCritical      = 0,  
    eAppDomainCritical = 1,  
    eProcessCritical   = 2  
} EMemoryCriticalLevel;  
```  
  
## <a name="members"></a><span data-ttu-id="cdd28-105">Membres</span><span class="sxs-lookup"><span data-stu-id="cdd28-105">Members</span></span>  
  
|<span data-ttu-id="cdd28-106">Membre</span><span class="sxs-lookup"><span data-stu-id="cdd28-106">Member</span></span>|<span data-ttu-id="cdd28-107">Description</span><span class="sxs-lookup"><span data-stu-id="cdd28-107">Description</span></span>|  
|------------|-----------------|  
|`eAppDomainCritical`|<span data-ttu-id="cdd28-108">Indique que l’allocation est essentielle pour l’exécution du code managé dans le domaine qui a demandé l’allocation.</span><span class="sxs-lookup"><span data-stu-id="cdd28-108">Indicates that the allocation is critical for executing managed code in the domain that has requested the allocation.</span></span> <span data-ttu-id="cdd28-109">Si la mémoire ne peut pas être allouée, le CLR ne peut pas garantir que le domaine est toujours utilisable.</span><span class="sxs-lookup"><span data-stu-id="cdd28-109">If memory cannot be allocated, the CLR cannot guarantee that the domain is still usable.</span></span> <span data-ttu-id="cdd28-110">L’hôte décide de l’action à entreprendre lorsque l’allocation ne peut pas être satisfaite.</span><span class="sxs-lookup"><span data-stu-id="cdd28-110">The host decides what action to take when the allocation cannot be satisfied.</span></span> <span data-ttu-id="cdd28-111">Elle peut demander au CLR d’abandonner `AppDomain` automatiquement ou de l’autoriser à continuer à s’exécuter en appelant des méthodes sur [ICLRPolicyManager](iclrpolicymanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="cdd28-111">It can instruct the CLR to abort the `AppDomain` automatically, or allow it to keep running by calling methods on [ICLRPolicyManager](iclrpolicymanager-interface.md).</span></span>|  
|`eProcessCritical`|<span data-ttu-id="cdd28-112">Indique que l’allocation est essentielle à l’exécution du code managé dans le processus.</span><span class="sxs-lookup"><span data-stu-id="cdd28-112">Indicates that the allocation is critical to the execution of managed code in the process.</span></span> <span data-ttu-id="cdd28-113">Cette valeur est utilisée lors du démarrage et lors de l’exécution des finaliseurs.</span><span class="sxs-lookup"><span data-stu-id="cdd28-113">This value is used during startup and when running finalizers.</span></span> <span data-ttu-id="cdd28-114">Si la mémoire ne peut pas être allouée, le CLR ne peut pas fonctionner dans le processus.</span><span class="sxs-lookup"><span data-stu-id="cdd28-114">If memory cannot be allocated, the CLR cannot operate in the process.</span></span> <span data-ttu-id="cdd28-115">Si l’allocation échoue, le CLR est effectivement désactivé.</span><span class="sxs-lookup"><span data-stu-id="cdd28-115">If the allocation fails, the CLR is effectively disabled.</span></span> <span data-ttu-id="cdd28-116">Tous les appels suivants dans le CLR échouent avec HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="cdd28-116">All subsequent calls into the CLR fail with HOST_E_CLRNOTAVAILABLE.</span></span>|  
|`eTaskCritical`|<span data-ttu-id="cdd28-117">Indique que l’allocation est essentielle à l’exécution de la tâche qui a demandé l’allocation.</span><span class="sxs-lookup"><span data-stu-id="cdd28-117">Indicates that the allocation is critical to running the task that has requested the allocation.</span></span> <span data-ttu-id="cdd28-118">Si la mémoire ne peut pas être allouée, le CLR ne peut pas garantir que la tâche peut être exécutée.</span><span class="sxs-lookup"><span data-stu-id="cdd28-118">If memory cannot be allocated, the CLR cannot guarantee that the task can be executed.</span></span> <span data-ttu-id="cdd28-119">En cas de défaillance, le CLR déclenche une <xref:System.Threading.ThreadAbortException> sur le thread du système d’opération physique.</span><span class="sxs-lookup"><span data-stu-id="cdd28-119">In the event of failure, the CLR raises a <xref:System.Threading.ThreadAbortException> on the physical operation system thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cdd28-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="cdd28-120">Remarks</span></span>  
 <span data-ttu-id="cdd28-121">Les méthodes d’allocation de mémoire définies dans les interfaces [IHostMemoryManager](ihostmemorymanager-interface.md) et [IHostMalloc](ihostmalloc-interface.md) prennent un paramètre de ce type.</span><span class="sxs-lookup"><span data-stu-id="cdd28-121">The memory allocation methods defined in the [IHostMemoryManager](ihostmemorymanager-interface.md) and [IHostMAlloc](ihostmalloc-interface.md) interfaces take a parameter of this type.</span></span> <span data-ttu-id="cdd28-122">En fonction de la gravité d’un échec, un hôte peut décider s’il faut faire échouer la demande d’allocation immédiatement ou attendre qu’elle soit satisfaite.</span><span class="sxs-lookup"><span data-stu-id="cdd28-122">Depending upon the severity of a failure, a host can decide whether to fail the allocation request immediately or to wait until it can be satisfied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cdd28-123">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="cdd28-123">Requirements</span></span>  
 <span data-ttu-id="cdd28-124">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cdd28-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cdd28-125">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cdd28-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cdd28-126">**Bibliothèque :** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="cdd28-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cdd28-127">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cdd28-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdd28-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cdd28-128">See also</span></span>

- [<span data-ttu-id="cdd28-129">ICLRMemoryNotificationCallback, interface</span><span class="sxs-lookup"><span data-stu-id="cdd28-129">ICLRMemoryNotificationCallback Interface</span></span>](iclrmemorynotificationcallback-interface.md)
- [<span data-ttu-id="cdd28-130">Énumérations d'hébergement</span><span class="sxs-lookup"><span data-stu-id="cdd28-130">Hosting Enumerations</span></span>](hosting-enumerations.md)
