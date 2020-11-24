---
title: IHostIoCompletionManager::SetMinThreads, méthode
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.SetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::SetMinThreads
helpviewer_keywords:
- SetMinThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::SetMinThreads method [.NET Framework hosting]
ms.assetid: dea34b81-8d2b-4cc3-8696-0ad4291d8a92
topic_type:
- apiref
ms.openlocfilehash: 64ea9fdd477ec005b089f451101b742278ab4266
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672407"
---
# <a name="ihostiocompletionmanagersetminthreads-method"></a><span data-ttu-id="f0e16-102">IHostIoCompletionManager::SetMinThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="f0e16-102">IHostIoCompletionManager::SetMinThreads Method</span></span>

<span data-ttu-id="f0e16-103">Définit le nombre minimal de threads que l’hôte doit allouer à l’achèvement d’e/s.</span><span class="sxs-lookup"><span data-stu-id="f0e16-103">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0e16-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f0e16-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMinThreads (  
    [in] DWORD dwMinIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0e16-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f0e16-105">Parameters</span></span>  

 `dwMinIoCompletionThreads`  
 <span data-ttu-id="f0e16-106">dans Nombre minimal de threads de terminaison d’e/s que l’hôte doit créer.</span><span class="sxs-lookup"><span data-stu-id="f0e16-106">[in] The minimum number of I/O completion threads that the host should create.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f0e16-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="f0e16-107">Return Value</span></span>  
  
|<span data-ttu-id="f0e16-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f0e16-108">HRESULT</span></span>|<span data-ttu-id="f0e16-109">Description</span><span class="sxs-lookup"><span data-stu-id="f0e16-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f0e16-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f0e16-110">S_OK</span></span>|<span data-ttu-id="f0e16-111">`SetMinThreads` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="f0e16-111">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="f0e16-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f0e16-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f0e16-113">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="f0e16-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f0e16-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f0e16-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f0e16-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="f0e16-115">The call timed out.</span></span>|  
|<span data-ttu-id="f0e16-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f0e16-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f0e16-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="f0e16-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f0e16-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f0e16-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f0e16-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="f0e16-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f0e16-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f0e16-120">E_FAIL</span></span>|<span data-ttu-id="f0e16-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="f0e16-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f0e16-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="f0e16-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f0e16-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f0e16-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f0e16-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="f0e16-124">E_NOTIMPL</span></span>|<span data-ttu-id="f0e16-125">L’hôte ne fournit pas d’implémentation de `SetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="f0e16-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0e16-126">Remarques</span><span class="sxs-lookup"><span data-stu-id="f0e16-126">Remarks</span></span>  

 <span data-ttu-id="f0e16-127">Un hôte peut souhaiter exercer un contrôle exclusif sur le nombre de threads pouvant être alloués pour traiter les demandes d’e/s, pour des raisons telles que l’implémentation, les performances ou l’évolutivité.</span><span class="sxs-lookup"><span data-stu-id="f0e16-127">A host might want exclusive control over the number of threads that can be allotted to process I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="f0e16-128">Pour cette raison, l’hôte n’est pas tenu d’implémenter `SetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="f0e16-128">For this reason, the host is not required to implement `SetMinThreads`.</span></span> <span data-ttu-id="f0e16-129">Dans ce cas, l’hôte doit retourner E_NOTIMPL à partir de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="f0e16-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0e16-130">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f0e16-130">Requirements</span></span>  

 <span data-ttu-id="f0e16-131">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0e16-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0e16-132">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f0e16-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f0e16-133">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f0e16-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f0e16-134">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0e16-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0e16-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f0e16-135">See also</span></span>

- [<span data-ttu-id="f0e16-136">ICLRIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="f0e16-136">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="f0e16-137">SetMaxThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="f0e16-137">SetMaxThreads Method</span></span>](ihostiocompletionmanager-setmaxthreads-method.md)
- [<span data-ttu-id="f0e16-138">IHostIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="f0e16-138">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
