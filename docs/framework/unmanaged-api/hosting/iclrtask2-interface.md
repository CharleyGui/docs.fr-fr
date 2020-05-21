---
title: ICLRTask2, interface
ms.date: 03/30/2017
api_name:
- ICLRTask2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2
helpviewer_keywords:
- ICLRTask2 interface [.NET Framework hosting]
ms.assetid: b5a22ebc-0582-49de-91f9-97a3d9789290
topic_type:
- apiref
ms.openlocfilehash: b067ca72e030bce24a7efde5e3488a00024e9613
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762865"
---
# <a name="iclrtask2-interface"></a><span data-ttu-id="9dec3-102">ICLRTask2, interface</span><span class="sxs-lookup"><span data-stu-id="9dec3-102">ICLRTask2 Interface</span></span>
<span data-ttu-id="9dec3-103">Fournit toutes les fonctionnalités de l’interface [ICLRTask](iclrtask-interface.md) ; en outre, fournit des méthodes qui permettent de retarder les abandons de thread sur le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="9dec3-103">Provides all the functionality of the [ICLRTask](iclrtask-interface.md) interface; in addition, provides methods that allow thread aborts to be delayed on the current thread.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9dec3-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="9dec3-104">Methods</span></span>  
  
|<span data-ttu-id="9dec3-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="9dec3-105">Method</span></span>|<span data-ttu-id="9dec3-106">Description</span><span class="sxs-lookup"><span data-stu-id="9dec3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9dec3-107">BeginPreventAsyncAbort, méthode</span><span class="sxs-lookup"><span data-stu-id="9dec3-107">BeginPreventAsyncAbort Method</span></span>](iclrtask2-beginpreventasyncabort-method.md)|<span data-ttu-id="9dec3-108">Retarde les nouvelles demandes d’abandon de thread sur le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="9dec3-108">Delays new thread abort requests on the current thread.</span></span>|  
|[<span data-ttu-id="9dec3-109">BeginPreventAsyncAbort, méthode</span><span class="sxs-lookup"><span data-stu-id="9dec3-109">EndPreventAsyncAbort Method</span></span>](iclrtask2-endpreventasyncabort-method.md)|<span data-ttu-id="9dec3-110">Autorise les demandes d’abandon de thread nouvelles ou en attente pour entraîner des abandons de threads sur le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="9dec3-110">Allows new or pending thread abort requests to result in thread aborts on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9dec3-111">Notes</span><span class="sxs-lookup"><span data-stu-id="9dec3-111">Remarks</span></span>  
 <span data-ttu-id="9dec3-112">L' `ICLRTask2` interface hérite de l' `ICLRTask` interface et ajoute des méthodes qui permettent à l’hôte de retarder les abandons de thread, afin de protéger une région de code qui ne doit pas échouer.</span><span class="sxs-lookup"><span data-stu-id="9dec3-112">The `ICLRTask2` interface inherits the `ICLRTask` interface and adds methods that allow the host to delay thread aborts, to protect a region of code that must not fail.</span></span> <span data-ttu-id="9dec3-113">`BeginPreventAsyncAbort`L’appel de incrémente le compteur Delay-thread-abort pour le thread actuel, puis l’appelle `EndPreventAsyncAbort` décrémente.</span><span class="sxs-lookup"><span data-stu-id="9dec3-113">Calling `BeginPreventAsyncAbort` increments the delay-thread-abort counter for the current thread, and calling `EndPreventAsyncAbort` decrements it.</span></span> <span data-ttu-id="9dec3-114">Les appels à `BeginPreventAsyncAbort` et `EndPreventAsyncAbort` peuvent être imbriqués.</span><span class="sxs-lookup"><span data-stu-id="9dec3-114">Calls to `BeginPreventAsyncAbort` and `EndPreventAsyncAbort` can be nested.</span></span> <span data-ttu-id="9dec3-115">Tant que le compteur est supérieur à zéro, les abandons de thread pour le thread actuel sont retardés.</span><span class="sxs-lookup"><span data-stu-id="9dec3-115">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span>  
  
 <span data-ttu-id="9dec3-116">Si les appels à `BeginPreventAsyncAbort` et ne `EndPreventAsyncAbort` sont pas couplés, il est possible d’atteindre un État dans lequel les abandons de thread ne peuvent pas être remis au thread actuel.</span><span class="sxs-lookup"><span data-stu-id="9dec3-116">If calls to `BeginPreventAsyncAbort` and `EndPreventAsyncAbort` are not paired, it is possible to reach a state in which thread aborts cannot be delivered to the current thread.</span></span>  
  
 <span data-ttu-id="9dec3-117">Le délai n’est pas respecté pour un thread qui s’arrête lui-même.</span><span class="sxs-lookup"><span data-stu-id="9dec3-117">The delay is not honored for a thread that aborts itself.</span></span>  
  
 <span data-ttu-id="9dec3-118">La fonctionnalité exposée par cette fonctionnalité est utilisée en interne par la machine virtuelle.</span><span class="sxs-lookup"><span data-stu-id="9dec3-118">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="9dec3-119">Une utilisation incorrecte de ces méthodes peut entraîner un comportement non spécifié dans la machine virtuelle.</span><span class="sxs-lookup"><span data-stu-id="9dec3-119">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="9dec3-120">Par exemple, l’appel de `EndPreventAsyncAbort` sans tout d’abord appeler `BeginPreventAsyncAbort` peut affecter la valeur zéro au compteur lorsque la machine virtuelle l’a incrémentée précédemment.</span><span class="sxs-lookup"><span data-stu-id="9dec3-120">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="9dec3-121">De même, le compteur interne n’est pas vérifié pour le dépassement de capacité.</span><span class="sxs-lookup"><span data-stu-id="9dec3-121">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="9dec3-122">Si elle dépasse sa limite intégrale parce qu’elle est incrémentée par l’hôte et la machine virtuelle, le comportement résultant n’est pas spécifié.</span><span class="sxs-lookup"><span data-stu-id="9dec3-122">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
 <span data-ttu-id="9dec3-123">Pour plus d’informations sur les membres hérités de `ICLRTask` et sur les autres utilisations de cette interface, consultez l’interface [ICLRTask](iclrtask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="9dec3-123">For information about members inherited from `ICLRTask` and about the other uses of this interface, see the [ICLRTask](iclrtask-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9dec3-124">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="9dec3-124">Requirements</span></span>  
 <span data-ttu-id="9dec3-125">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9dec3-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9dec3-126">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9dec3-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9dec3-127">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9dec3-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9dec3-128">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9dec3-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dec3-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9dec3-129">See also</span></span>

- [<span data-ttu-id="9dec3-130">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="9dec3-130">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="9dec3-131">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="9dec3-131">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="9dec3-132">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="9dec3-132">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="9dec3-133">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="9dec3-133">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="9dec3-134">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="9dec3-134">Hosting Interfaces</span></span>](hosting-interfaces.md)
