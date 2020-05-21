---
title: ICLRTask2::EndPreventAsyncAbort, méthode
ms.date: 03/30/2017
api_name:
- ICLRTask2.EndPreventAsyncAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2::EndPreventAsyncAbort
helpviewer_keywords:
- EndPreventAsyncAbort method [.NET Framework hosting]
- ICLRTask2::EndPreventAsyncAbort method [.NET Framework hosting]
ms.assetid: d8013659-e3df-44b3-814f-a6b534ce62f8
topic_type:
- apiref
ms.openlocfilehash: 3ea36c56ef9ccf5886ba96191627e5283da186f7
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762850"
---
# <a name="iclrtask2endpreventasyncabort-method"></a><span data-ttu-id="af756-102">ICLRTask2::EndPreventAsyncAbort, méthode</span><span class="sxs-lookup"><span data-stu-id="af756-102">ICLRTask2::EndPreventAsyncAbort Method</span></span>
<span data-ttu-id="af756-103">Autorise les demandes d’abandon de thread nouvelles ou en attente pour entraîner des abandons de threads sur le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="af756-103">Allows new or pending thread abort requests to result in thread aborts on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af756-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af756-104">Syntax</span></span>  
  
```cpp  
HRESULT EndPreventAsyncAbort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="af756-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="af756-105">Return Value</span></span>  
 <span data-ttu-id="af756-106">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="af756-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="af756-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="af756-107">HRESULT</span></span>|<span data-ttu-id="af756-108">Description</span><span class="sxs-lookup"><span data-stu-id="af756-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="af756-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="af756-109">S_OK</span></span>|<span data-ttu-id="af756-110">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="af756-110">The method completed successfully.</span></span>|  
|<span data-ttu-id="af756-111">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="af756-111">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="af756-112">La méthode a été appelée sur un thread qui n’est pas le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="af756-112">The method was called on a thread which is not the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af756-113">Notes</span><span class="sxs-lookup"><span data-stu-id="af756-113">Remarks</span></span>  
 <span data-ttu-id="af756-114">L’appel de cette méthode décrémente d’une unité le compteur de temporisation de thread-abandon du thread actuel.</span><span class="sxs-lookup"><span data-stu-id="af756-114">Calling this method decrements the delay-thread-abort counter for the current thread by one.</span></span>  
  
 <span data-ttu-id="af756-115">Les appels à [ICLRTask2 :: BeginPreventAsyncAbort,](iclrtask2-beginpreventasyncabort-method.md) et `EndPreventAsyncAbort` peuvent être imbriqués.</span><span class="sxs-lookup"><span data-stu-id="af756-115">Calls to [ICLRTask2::BeginPreventAsyncAbort](iclrtask2-beginpreventasyncabort-method.md) and `EndPreventAsyncAbort` can be nested.</span></span> <span data-ttu-id="af756-116">Tant que le compteur est supérieur à zéro, les abandons de thread pour le thread actuel sont retardés.</span><span class="sxs-lookup"><span data-stu-id="af756-116">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span>  
  
 <span data-ttu-id="af756-117">La fonctionnalité exposée par cette fonctionnalité est utilisée en interne par la machine virtuelle.</span><span class="sxs-lookup"><span data-stu-id="af756-117">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="af756-118">Une utilisation incorrecte de ces méthodes peut entraîner un comportement non spécifié dans la machine virtuelle.</span><span class="sxs-lookup"><span data-stu-id="af756-118">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="af756-119">Par exemple, l’appel de `EndPreventAsyncAbort` sans tout d’abord appeler `BeginPreventAsyncAbort` peut affecter la valeur zéro au compteur lorsque la machine virtuelle l’a incrémentée précédemment.</span><span class="sxs-lookup"><span data-stu-id="af756-119">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="af756-120">De même, le compteur interne n’est pas vérifié pour le dépassement de capacité.</span><span class="sxs-lookup"><span data-stu-id="af756-120">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="af756-121">Si elle dépasse sa limite intégrale parce qu’elle est incrémentée par l’hôte et la machine virtuelle, le comportement résultant n’est pas spécifié.</span><span class="sxs-lookup"><span data-stu-id="af756-121">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af756-122">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="af756-122">Requirements</span></span>  
 <span data-ttu-id="af756-123">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af756-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af756-124">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="af756-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="af756-125">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="af756-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="af756-126">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af756-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af756-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="af756-127">See also</span></span>

- [<span data-ttu-id="af756-128">BeginPreventAsyncAbort, méthode</span><span class="sxs-lookup"><span data-stu-id="af756-128">BeginPreventAsyncAbort Method</span></span>](iclrtask2-beginpreventasyncabort-method.md)
- [<span data-ttu-id="af756-129">ICLRTask2, interface</span><span class="sxs-lookup"><span data-stu-id="af756-129">ICLRTask2 Interface</span></span>](iclrtask2-interface.md)
- [<span data-ttu-id="af756-130">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="af756-130">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="af756-131">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="af756-131">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="af756-132">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="af756-132">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="af756-133">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="af756-133">Hosting Interfaces</span></span>](hosting-interfaces.md)
