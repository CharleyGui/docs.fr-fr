---
title: EPolicyAction, énumération
ms.date: 03/30/2017
api_name:
- EPolicyAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EPolicyAction
helpviewer_keywords:
- EPolicyAction enumeration [.NET Framework hosting]
ms.assetid: 72dd76ba-239e-45ac-9ded-318fb07d6c6d
topic_type:
- apiref
ms.openlocfilehash: 72b371d72b2f055f2840da5595d9022ffd7e2507
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674731"
---
# <a name="epolicyaction-enumeration"></a><span data-ttu-id="90c03-102">EPolicyAction, énumération</span><span class="sxs-lookup"><span data-stu-id="90c03-102">EPolicyAction Enumeration</span></span>

<span data-ttu-id="90c03-103">Décrit les actions de stratégie que l’hôte peut définir pour les opérations décrites par [EClrOperation](eclroperation-enumeration.md) et les échecs décrits par [EClrFailure](eclrfailure-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="90c03-103">Describes the policy actions the host can set for operations described by [EClrOperation](eclroperation-enumeration.md) and failures described by [EClrFailure](eclrfailure-enumeration.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90c03-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90c03-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eNoAction,  
    eThrowException,  
    eAbortThread,  
    eRudeAbortThread,  
    eUnloadAppDomain,  
    eRudeUnloadAppDomain,  
    eExitProcess,  
    eFastExitProcess,  
    eRudeExitProcess,  
    eDisableRuntime  
} EPolicyAction;  
```  
  
## <a name="members"></a><span data-ttu-id="90c03-105">Membres</span><span class="sxs-lookup"><span data-stu-id="90c03-105">Members</span></span>  
  
|<span data-ttu-id="90c03-106">Membre</span><span class="sxs-lookup"><span data-stu-id="90c03-106">Member</span></span>|<span data-ttu-id="90c03-107">Description</span><span class="sxs-lookup"><span data-stu-id="90c03-107">Description</span></span>|  
|------------|-----------------|  
|`eAbortThread`|<span data-ttu-id="90c03-108">Spécifie que le common language runtime (CLR) doit abandonner le thread normalement.</span><span class="sxs-lookup"><span data-stu-id="90c03-108">Specifies that the common language runtime (CLR) should abort the thread gracefully.</span></span> <span data-ttu-id="90c03-109">Une annulation appropriée comprend les tentatives d’exécution de tous les `finally` blocs, tous les `catch` blocs liés aux abandons de thread et les finaliseurs.</span><span class="sxs-lookup"><span data-stu-id="90c03-109">A graceful abort includes attempts to run all `finally` blocks, any `catch` blocks related to thread aborts, and finalizers.</span></span>|  
|`eDisableRuntime`|<span data-ttu-id="90c03-110">Spécifie que le CLR doit entrer dans un état désactivé.</span><span class="sxs-lookup"><span data-stu-id="90c03-110">Specifies that the CLR should enter a disabled state.</span></span> <span data-ttu-id="90c03-111">Aucun code managé supplémentaire ne peut être exécuté dans le processus affecté, et les threads ne peuvent pas accéder au CLR.</span><span class="sxs-lookup"><span data-stu-id="90c03-111">No further managed code can be executed in the affected process, and threads are blocked from entering the CLR.</span></span>|  
|`eExitProcess`|<span data-ttu-id="90c03-112">Spécifie que le CLR doit tenter une sortie normale du processus, y compris l’exécution des finaliseurs et l’exécution des opérations de nettoyage et de journalisation.</span><span class="sxs-lookup"><span data-stu-id="90c03-112">Specifies that the CLR should attempt a graceful exit of the process, including running finalizers and performing cleanup and logging operations.</span></span>|  
|`eFastExitProcess`|<span data-ttu-id="90c03-113">Spécifie que le CLR doit quitter le processus immédiatement, sans exécuter de finaliseurs ou effectuer des opérations de nettoyage et de journalisation.</span><span class="sxs-lookup"><span data-stu-id="90c03-113">Specifies that the CLR should exit the process immediately, without running finalizers or performing cleanup and logging operations.</span></span> <span data-ttu-id="90c03-114">Toutefois, la notification est envoyée au débogueur.</span><span class="sxs-lookup"><span data-stu-id="90c03-114">However, notification is sent to the debugger.</span></span>|  
|`eNoAction`|<span data-ttu-id="90c03-115">Spécifie qu’aucune action ne doit être effectuée.</span><span class="sxs-lookup"><span data-stu-id="90c03-115">Specifies that no action should be taken.</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="90c03-116">Spécifie que le CLR doit effectuer une interruption de thread impropre.</span><span class="sxs-lookup"><span data-stu-id="90c03-116">Specifies that the CLR should perform a rude thread abort.</span></span> <span data-ttu-id="90c03-117">Seuls les `catch` `finally` blocs et marqués avec <xref:System.EnterpriseServices.MustRunInClientContextAttribute> sont exécutés.</span><span class="sxs-lookup"><span data-stu-id="90c03-117">Only those `catch` and `finally` blocks marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span>|  
|`eRudeExitProcess`|<span data-ttu-id="90c03-118">Spécifie que le CLR doit quitter le processus sans exécuter de finaliseurs ni d’opérations de journalisation.</span><span class="sxs-lookup"><span data-stu-id="90c03-118">Specifies that the CLR should exit the process without running finalizers or logging operations.</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="90c03-119">Spécifie que le CLR doit effectuer un déchargement impropre de <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="90c03-119">Specifies that the CLR should perform a rude unload of the <xref:System.AppDomain>.</span></span> <span data-ttu-id="90c03-120">Seuls les finaliseurs marqués avec <xref:System.EnterpriseServices.MustRunInClientContextAttribute> sont exécutés.</span><span class="sxs-lookup"><span data-stu-id="90c03-120">Only finalizers marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span> <span data-ttu-id="90c03-121">De même, tous les threads avec ce <xref:System.AppDomain> dans leur pile reçoivent un `ThreadAbortException` , mais seuls ceux `catch` et les `finally` blocs marqués avec <xref:System.EnterpriseServices.MustRunInClientContextAttribute> sont exécutés.</span><span class="sxs-lookup"><span data-stu-id="90c03-121">Similarly, all threads with this <xref:System.AppDomain> in their stack receive a `ThreadAbortException`, but only those `catch` and `finally` blocks marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span>|  
|`eThrowException`|<span data-ttu-id="90c03-122">Spécifie qu’une exception appropriée à la condition, telle que la mémoire insuffisante, le dépassement de capacité de la mémoire tampon, etc., doit être levée.</span><span class="sxs-lookup"><span data-stu-id="90c03-122">Specifies that an exception appropriate to the condition, such as out-of-memory, buffer overflow, and so forth, should be thrown.</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="90c03-123">Spécifie que <xref:System.AppDomain> doit être déchargé.</span><span class="sxs-lookup"><span data-stu-id="90c03-123">Specifies that the <xref:System.AppDomain> should be unloaded.</span></span> <span data-ttu-id="90c03-124">Le CLR tente d’exécuter des finaliseurs.</span><span class="sxs-lookup"><span data-stu-id="90c03-124">The CLR attempts to run finalizers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90c03-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="90c03-125">Remarks</span></span>  

 <span data-ttu-id="90c03-126">L’hôte définit des actions de stratégie en appelant des méthodes de l’interface [ICLRPolicyManager](iclrpolicymanager-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="90c03-126">The host sets policy actions by calling methods of the [ICLRPolicyManager](iclrpolicymanager-interface.md) interface.</span></span> <span data-ttu-id="90c03-127">Pour plus d’informations sur les abandons brutaux et normaux, consultez l’énumération [EClrOperation](eclroperation-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="90c03-127">For information about rude and graceful aborts, see the [EClrOperation](eclroperation-enumeration.md) enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90c03-128">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="90c03-128">Requirements</span></span>  

 <span data-ttu-id="90c03-129">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90c03-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90c03-130">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="90c03-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="90c03-131">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="90c03-131">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="90c03-132">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90c03-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90c03-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="90c03-133">See also</span></span>

- [<span data-ttu-id="90c03-134">EClrFailure, énumération</span><span class="sxs-lookup"><span data-stu-id="90c03-134">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="90c03-135">ICLRPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="90c03-135">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="90c03-136">IHostPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="90c03-136">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
- [<span data-ttu-id="90c03-137">Énumérations d'hébergement</span><span class="sxs-lookup"><span data-stu-id="90c03-137">Hosting Enumerations</span></span>](hosting-enumerations.md)
