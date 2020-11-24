---
title: IHostIoCompletionManager::GetMinThreads, méthode
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetMinThreads
helpviewer_keywords:
- GetMinThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::GetMinThreads method [.NET Framework hosting]
ms.assetid: d7a7f733-677d-481c-b3d5-444fcc502b8e
topic_type:
- apiref
ms.openlocfilehash: d321ce08edf4780fc5f26ac627849b9129c2f283
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673213"
---
# <a name="ihostiocompletionmanagergetminthreads-method"></a><span data-ttu-id="65d7d-102">IHostIoCompletionManager::GetMinThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="65d7d-102">IHostIoCompletionManager::GetMinThreads Method</span></span>

<span data-ttu-id="65d7d-103">Obtient le nombre minimal de threads que l’hôte fournit pour traiter les demandes d’e/s.</span><span class="sxs-lookup"><span data-stu-id="65d7d-103">Gets the minimum number of threads that the host provides for processing I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65d7d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="65d7d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMinThreads (  
    [out] DWORD *pdwMinIOCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65d7d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="65d7d-105">Parameters</span></span>  

 `pdwMinIOCompletionThreads`  
 <span data-ttu-id="65d7d-106">à Pointeur vers le nombre minimal de threads que l’hôte fournit pour traiter les demandes d’e/s.</span><span class="sxs-lookup"><span data-stu-id="65d7d-106">[out] A pointer to the minimum number of threads that the host provides to process I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="65d7d-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="65d7d-107">Return Value</span></span>  
  
|<span data-ttu-id="65d7d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="65d7d-108">HRESULT</span></span>|<span data-ttu-id="65d7d-109">Description</span><span class="sxs-lookup"><span data-stu-id="65d7d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="65d7d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="65d7d-110">S_OK</span></span>|<span data-ttu-id="65d7d-111">`GetMinThreads` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="65d7d-111">`GetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="65d7d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="65d7d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="65d7d-113">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="65d7d-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="65d7d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="65d7d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="65d7d-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="65d7d-115">The call timed out.</span></span>|  
|<span data-ttu-id="65d7d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="65d7d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="65d7d-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="65d7d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="65d7d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="65d7d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="65d7d-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="65d7d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="65d7d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="65d7d-120">E_FAIL</span></span>|<span data-ttu-id="65d7d-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="65d7d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="65d7d-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="65d7d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="65d7d-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="65d7d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="65d7d-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="65d7d-124">E_NOTIMPL</span></span>|<span data-ttu-id="65d7d-125">L’hôte ne fournit pas d’implémentation de `GetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="65d7d-125">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="65d7d-126">Remarques</span><span class="sxs-lookup"><span data-stu-id="65d7d-126">Remarks</span></span>  

 <span data-ttu-id="65d7d-127">Un hôte peut souhaiter exercer un contrôle exclusif sur le nombre de threads alloués aux demandes d’e/s de service, pour des raisons telles que l’implémentation, les performances ou l’évolutivité.</span><span class="sxs-lookup"><span data-stu-id="65d7d-127">A host might want exclusive control over the number of threads allotted to service I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="65d7d-128">Pour cette raison, l’hôte n’est pas tenu d’implémenter `GetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="65d7d-128">For this reason, the host is not required to implement `GetMinThreads`.</span></span> <span data-ttu-id="65d7d-129">Dans ce cas, l’hôte doit retourner E_NOTIMPL à partir de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="65d7d-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65d7d-130">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="65d7d-130">Requirements</span></span>  

 <span data-ttu-id="65d7d-131">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65d7d-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65d7d-132">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="65d7d-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="65d7d-133">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="65d7d-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="65d7d-134">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65d7d-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65d7d-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="65d7d-135">See also</span></span>

- [<span data-ttu-id="65d7d-136">ICLRIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="65d7d-136">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="65d7d-137">IHostIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="65d7d-137">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
