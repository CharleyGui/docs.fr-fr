---
title: ICLRTask2::BeginPreventAsyncAbort, méthode
ms.date: 03/30/2017
api_name:
- ICLRTask2.BeginPreventAsyncAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2::BeginPreventAsyncAbort
helpviewer_keywords:
- ICLRTask2::BeginPreventAsyncAbort method [.NET Framework hosting]
- BeginPreventAsyncAbort method [.NET Framework hosting]
ms.assetid: 75754c2f-38c7-4707-85fe-559db4542729
topic_type:
- apiref
ms.openlocfilehash: daf211fcc496f63ef71575abf6a28655004db264
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720241"
---
# <a name="iclrtask2beginpreventasyncabort-method"></a><span data-ttu-id="7c45a-102">ICLRTask2::BeginPreventAsyncAbort, méthode</span><span class="sxs-lookup"><span data-stu-id="7c45a-102">ICLRTask2::BeginPreventAsyncAbort Method</span></span>

<span data-ttu-id="7c45a-103">Retarde les nouvelles demandes d’abandon de thread à partir de qui entraînent des abandons de threads sur le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="7c45a-103">Delays new thread abort requests from resulting in thread aborts on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c45a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7c45a-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginPreventAsyncAbort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="7c45a-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="7c45a-105">Return Value</span></span>  

 <span data-ttu-id="7c45a-106">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="7c45a-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="7c45a-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7c45a-107">HRESULT</span></span>|<span data-ttu-id="7c45a-108">Description</span><span class="sxs-lookup"><span data-stu-id="7c45a-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7c45a-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="7c45a-109">S_OK</span></span>|<span data-ttu-id="7c45a-110">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="7c45a-110">The method completed successfully.</span></span>|  
|<span data-ttu-id="7c45a-111">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="7c45a-111">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="7c45a-112">La méthode a été appelée sur un thread qui n’est pas le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="7c45a-112">The method was called on a thread which is not the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c45a-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="7c45a-113">Remarks</span></span>  

 <span data-ttu-id="7c45a-114">L’appel de cette méthode incrémente de 1 le compteur Delay-thread-abort pour le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="7c45a-114">Calling this method increments the delay-thread-abort counter for the current thread by one.</span></span>  
  
 <span data-ttu-id="7c45a-115">Les appels à `BeginPreventAsyncAbort` et [ICLRTask2 :: EndPreventAsyncAbort,](iclrtask2-endpreventasyncabort-method.md) peuvent être imbriqués.</span><span class="sxs-lookup"><span data-stu-id="7c45a-115">Calls to `BeginPreventAsyncAbort` and [ICLRTask2::EndPreventAsyncAbort](iclrtask2-endpreventasyncabort-method.md) can be nested.</span></span> <span data-ttu-id="7c45a-116">Tant que le compteur est supérieur à zéro, les abandons de thread pour le thread actuel sont retardés.</span><span class="sxs-lookup"><span data-stu-id="7c45a-116">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span> <span data-ttu-id="7c45a-117">Si cet appel n’est pas associé à un appel à la `EndPreventAsyncAbort` méthode, il est possible d’atteindre un État dans lequel les abandons de thread ne peuvent pas être remis au thread actuel.</span><span class="sxs-lookup"><span data-stu-id="7c45a-117">If this call is not paired with a call to the `EndPreventAsyncAbort` method, it is possible to reach a state in which thread aborts cannot be delivered to the current thread.</span></span>  
  
 <span data-ttu-id="7c45a-118">Le délai n’est pas respecté pour un thread qui s’arrête lui-même.</span><span class="sxs-lookup"><span data-stu-id="7c45a-118">The delay is not honored for a thread that aborts itself.</span></span>  
  
 <span data-ttu-id="7c45a-119">La fonctionnalité exposée par cette fonctionnalité est utilisée en interne par la machine virtuelle.</span><span class="sxs-lookup"><span data-stu-id="7c45a-119">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="7c45a-120">Une utilisation incorrecte de ces méthodes peut entraîner un comportement non spécifié dans la machine virtuelle.</span><span class="sxs-lookup"><span data-stu-id="7c45a-120">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="7c45a-121">Par exemple, l’appel de `EndPreventAsyncAbort` sans tout d’abord appeler `BeginPreventAsyncAbort` peut affecter la valeur zéro au compteur lorsque la machine virtuelle l’a incrémentée précédemment.</span><span class="sxs-lookup"><span data-stu-id="7c45a-121">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="7c45a-122">De même, le compteur interne n’est pas vérifié pour le dépassement de capacité.</span><span class="sxs-lookup"><span data-stu-id="7c45a-122">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="7c45a-123">Si elle dépasse sa limite intégrale parce qu’elle est incrémentée par l’hôte et la machine virtuelle, le comportement résultant n’est pas spécifié.</span><span class="sxs-lookup"><span data-stu-id="7c45a-123">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c45a-124">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7c45a-124">Requirements</span></span>  

 <span data-ttu-id="7c45a-125">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c45a-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c45a-126">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7c45a-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7c45a-127">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7c45a-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7c45a-128">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c45a-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c45a-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7c45a-129">See also</span></span>

- [<span data-ttu-id="7c45a-130">BeginPreventAsyncAbort, méthode</span><span class="sxs-lookup"><span data-stu-id="7c45a-130">EndPreventAsyncAbort Method</span></span>](iclrtask2-endpreventasyncabort-method.md)
- [<span data-ttu-id="7c45a-131">ICLRTask2, interface</span><span class="sxs-lookup"><span data-stu-id="7c45a-131">ICLRTask2 Interface</span></span>](iclrtask2-interface.md)
- [<span data-ttu-id="7c45a-132">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="7c45a-132">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="7c45a-133">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="7c45a-133">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="7c45a-134">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="7c45a-134">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="7c45a-135">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="7c45a-135">Hosting Interfaces</span></span>](hosting-interfaces.md)
