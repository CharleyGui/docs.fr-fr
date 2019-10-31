---
title: EClrOperation, énumération
ms.date: 03/30/2017
api_name:
- EClrOperation
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrOperation
helpviewer_keywords:
- EClrOperation enumeration [.NET Framework hosting]
ms.assetid: 5aef6808-5aac-4b2f-a2c7-fee1575c55ed
topic_type:
- apiref
ms.openlocfilehash: 6becc44b061ff2baac63437b6a72375d1c3735b2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131163"
---
# <a name="eclroperation-enumeration"></a><span data-ttu-id="d05f9-102">EClrOperation, énumération</span><span class="sxs-lookup"><span data-stu-id="d05f9-102">EClrOperation Enumeration</span></span>
<span data-ttu-id="d05f9-103">Décrit l’ensemble des opérations pour lesquelles un hôte peut appliquer des actions de stratégie.</span><span class="sxs-lookup"><span data-stu-id="d05f9-103">Describes the set of operations for which a host can apply policy actions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d05f9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d05f9-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    OPR_ThreadAbort,  
    OPR_ThreadRudeAbortInNonCriticalRegion,  
    OPR_ThreadRudeAbortInCriticalRegion,  
    OPR_AppDomainUnload,  
    OPR_AppDomainRudeUnload,  
    OPR_ProcessExit,  
    OPR_FinalizerRun  
} EClrOperation;  
```  
  
## <a name="members"></a><span data-ttu-id="d05f9-105">Membres</span><span class="sxs-lookup"><span data-stu-id="d05f9-105">Members</span></span>  
  
|<span data-ttu-id="d05f9-106">Membre</span><span class="sxs-lookup"><span data-stu-id="d05f9-106">Member</span></span>|<span data-ttu-id="d05f9-107">Description</span><span class="sxs-lookup"><span data-stu-id="d05f9-107">Description</span></span>|  
|------------|-----------------|  
|`OPR_AppDomainRudeUnload`|<span data-ttu-id="d05f9-108">L’hôte peut spécifier des actions de stratégie à entreprendre lorsqu’un <xref:System.AppDomain> est déchargé en mode non normal (impropre).</span><span class="sxs-lookup"><span data-stu-id="d05f9-108">The host can specify policy actions to be taken when an <xref:System.AppDomain> is unloaded in a non-graceful (rude) manner.</span></span>|  
|`OPR_AppDomainUnload`|<span data-ttu-id="d05f9-109">L’hôte peut spécifier des actions de stratégie à entreprendre lors du déchargement d’un <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="d05f9-109">The host can specify policy actions to be taken when an <xref:System.AppDomain> is unloaded.</span></span>|  
|`OPR_FinalizerRun`|<span data-ttu-id="d05f9-110">L’hôte peut spécifier des actions de stratégie à effectuer lors de l’exécution des finaliseurs.</span><span class="sxs-lookup"><span data-stu-id="d05f9-110">The host can specify policy actions to be taken when finalizers run.</span></span>|  
|`OPR_ProcessExit`|<span data-ttu-id="d05f9-111">L’hôte peut spécifier des actions de stratégie à entreprendre lorsque le processus se termine.</span><span class="sxs-lookup"><span data-stu-id="d05f9-111">The host can specify policy actions to be taken when the process exits.</span></span>|  
|`OPR_ThreadAbort`|<span data-ttu-id="d05f9-112">L’hôte peut spécifier des actions de stratégie à entreprendre lorsqu’un thread est abandonné.</span><span class="sxs-lookup"><span data-stu-id="d05f9-112">The host can specify policy actions to be taken when a thread is aborted.</span></span>|  
|`OPR_ThreadRudeAbortInCriticalRegion`|<span data-ttu-id="d05f9-113">L’hôte peut spécifier des actions de stratégie à entreprendre lorsqu’une interruption de thread impropre se produit dans une zone critique de code.</span><span class="sxs-lookup"><span data-stu-id="d05f9-113">The host can specify policy actions to be taken when a rude thread abort occurs in a critical region of code.</span></span>|  
|`OPR_ThreadRudeAbortInNonCriticalRegion`|<span data-ttu-id="d05f9-114">L’hôte peut spécifier des actions de stratégie à entreprendre lorsqu’une interruption de thread impropre se produit dans une région de code non critique.</span><span class="sxs-lookup"><span data-stu-id="d05f9-114">The host can specify policy actions to be take when a rude thread abort occurs in a non-critical region of code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d05f9-115">Notes</span><span class="sxs-lookup"><span data-stu-id="d05f9-115">Remarks</span></span>  
 <span data-ttu-id="d05f9-116">L’infrastructure de fiabilité du common language runtime (CLR) distingue les abandons et les échecs d’allocation de ressources qui se produisent dans les régions de code critiques et ceux qui se produisent dans les régions de code non critiques.</span><span class="sxs-lookup"><span data-stu-id="d05f9-116">The common language runtime (CLR) reliability infrastructure distinguishes between aborts and resource allocation failures that occur in critical regions of code and those that occur in non-critical regions of code.</span></span> <span data-ttu-id="d05f9-117">Cette distinction est conçue pour permettre aux hôtes de définir différentes stratégies en fonction de l’endroit où une défaillance se produit dans le code.</span><span class="sxs-lookup"><span data-stu-id="d05f9-117">This distinction is designed to allow hosts to set different policies depending on where a failure occurs in the code.</span></span>  
  
 <span data-ttu-id="d05f9-118">Une *région critique de code* est un espace où le CLR ne peut pas garantir que l’abandon d’une tâche ou l’échec de la réalisation d’une demande de ressources affectera uniquement la tâche en cours.</span><span class="sxs-lookup"><span data-stu-id="d05f9-118">A *critical region of code* is any space where the CLR cannot guarantee that aborting a task or failing to complete a request for resources will affect only the current task.</span></span> <span data-ttu-id="d05f9-119">Par exemple, si une tâche détient un verrou et reçoit un HRESULT qui indique un échec lors de l’exécution d’une demande d’allocation de mémoire, il est insuffisant simplement d’abandonner cette tâche pour garantir la stabilité du <xref:System.AppDomain>, car le <xref:System.AppDomain> peut contenir d’autres tâches en attente du même verrou.</span><span class="sxs-lookup"><span data-stu-id="d05f9-119">For example, if a task is holding a lock and receives an HRESULT that indicates failure upon making a memory allocation request, it is insufficient simply to abort that task to ensure the stability of the <xref:System.AppDomain>, because the <xref:System.AppDomain> might contain other tasks waiting for the same lock.</span></span> <span data-ttu-id="d05f9-120">L’abandon de la tâche en cours peut entraîner le blocage de ces autres tâches.</span><span class="sxs-lookup"><span data-stu-id="d05f9-120">To abandon the current task might cause those other tasks to stop responding.</span></span> <span data-ttu-id="d05f9-121">Dans ce cas, l’hôte a besoin de pouvoir décharger l’ensemble du <xref:System.AppDomain> plutôt que de risquer une instabilité potentielle.</span><span class="sxs-lookup"><span data-stu-id="d05f9-121">In such a case, the host needs the ability to unload the entire <xref:System.AppDomain> rather than risk potential instability.</span></span>  
  
 <span data-ttu-id="d05f9-122">Une *région de code non critique*, en revanche, est une région dans laquelle le CLR peut garantir qu’un abandon ou un échec affectera uniquement la tâche sur laquelle l’erreur se produit.</span><span class="sxs-lookup"><span data-stu-id="d05f9-122">A *non-critical region of code*, on the other hand, is a region where the CLR can guarantee that an abort or a failure will affect only the task upon which the error occurs.</span></span>  
  
 <span data-ttu-id="d05f9-123">Le CLR distingue également les abandons normaux et non normaux (brutal).</span><span class="sxs-lookup"><span data-stu-id="d05f9-123">The CLR also distinguishes between graceful and non-graceful (rude) aborts.</span></span> <span data-ttu-id="d05f9-124">En général, un abandon normal ou normal fait tout son possible pour exécuter des routines de gestion des exceptions et des finaliseurs avant d’abandonner une tâche, tandis qu’un abandon impropre n’apporte aucune garantie de ce type.</span><span class="sxs-lookup"><span data-stu-id="d05f9-124">In general, a normal or graceful abort makes every effort to run exception-handling routines and finalizers before aborting a task, while a rude abort makes no such guarantees.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d05f9-125">spécifications</span><span class="sxs-lookup"><span data-stu-id="d05f9-125">Requirements</span></span>  
 <span data-ttu-id="d05f9-126">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d05f9-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d05f9-127">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d05f9-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d05f9-128">**Bibliothèque :** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d05f9-128">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d05f9-129">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d05f9-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d05f9-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d05f9-130">See also</span></span>

- [<span data-ttu-id="d05f9-131">EClrFailure, énumération</span><span class="sxs-lookup"><span data-stu-id="d05f9-131">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="d05f9-132">EPolicyAction, énumération</span><span class="sxs-lookup"><span data-stu-id="d05f9-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="d05f9-133">ICLRPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="d05f9-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="d05f9-134">IHostPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="d05f9-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [<span data-ttu-id="d05f9-135">Énumérations d’hébergement</span><span class="sxs-lookup"><span data-stu-id="d05f9-135">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
