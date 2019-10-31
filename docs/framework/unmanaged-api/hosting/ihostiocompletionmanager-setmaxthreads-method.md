---
title: IHostIoCompletionManager::SetMaxThreads, méthode
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.SetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::SetMaxThreads
helpviewer_keywords:
- IHostIoCompletionManager::SetMaxThreads method [.NET Framework hosting]
- SetMaxThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: ebad4f40-d9f1-4dc6-9b27-a89c9eb3926f
topic_type:
- apiref
ms.openlocfilehash: 7a16c141d9d07af82bd984955e06199e66ce3bbf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133761"
---
# <a name="ihostiocompletionmanagersetmaxthreads-method"></a><span data-ttu-id="1b452-102">IHostIoCompletionManager::SetMaxThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="1b452-102">IHostIoCompletionManager::SetMaxThreads Method</span></span>
<span data-ttu-id="1b452-103">Définit le nombre maximal de threads que l’hôte alloue aux demandes d’e/s de service.</span><span class="sxs-lookup"><span data-stu-id="1b452-103">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b452-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1b452-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMaxThreads (  
    [in] DWORD dwMaxIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b452-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1b452-105">Parameters</span></span>  
 `dwMaxIoCompletionThreads`  
 <span data-ttu-id="1b452-106">dans Nombre maximal de threads à allouer pour les demandes d’e/s.</span><span class="sxs-lookup"><span data-stu-id="1b452-106">[in] The maximum number of threads to allot for I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1b452-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="1b452-107">Return Value</span></span>  
  
|<span data-ttu-id="1b452-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1b452-108">HRESULT</span></span>|<span data-ttu-id="1b452-109">Description</span><span class="sxs-lookup"><span data-stu-id="1b452-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1b452-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1b452-110">S_OK</span></span>|<span data-ttu-id="1b452-111">`SetMaxThreads` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="1b452-111">`SetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="1b452-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1b452-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1b452-113">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="1b452-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1b452-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1b452-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1b452-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="1b452-115">The call timed out.</span></span>|  
|<span data-ttu-id="1b452-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1b452-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1b452-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="1b452-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1b452-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1b452-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1b452-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="1b452-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1b452-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1b452-120">E_FAIL</span></span>|<span data-ttu-id="1b452-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="1b452-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1b452-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="1b452-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1b452-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1b452-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1b452-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="1b452-124">E_NOTIMPL</span></span>|<span data-ttu-id="1b452-125">L’hôte ne fournit pas d’implémentation de `SetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="1b452-125">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b452-126">Notes</span><span class="sxs-lookup"><span data-stu-id="1b452-126">Remarks</span></span>  
 <span data-ttu-id="1b452-127">`SetMaxThreads` fournit au CLR la possibilité de définir le nombre maximal de threads disponibles pour les demandes de service sur les ports d’e/s.</span><span class="sxs-lookup"><span data-stu-id="1b452-127">`SetMaxThreads` provides the CLR with an opportunity to set the maximum number of threads that are available to service requests on I/O ports.</span></span> <span data-ttu-id="1b452-128">Un hôte peut avoir besoin d’un contrôle exclusif sur la taille du pool de threads, pour des raisons telles que l’implémentation, les performances ou l’évolutivité.</span><span class="sxs-lookup"><span data-stu-id="1b452-128">A host might need exclusive control over the size of the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="1b452-129">Pour cette raison, l’hôte n’est pas tenu d’implémenter `SetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="1b452-129">For this reason, the host is not required to implement `SetMaxThreads`.</span></span> <span data-ttu-id="1b452-130">Dans ce cas, un hôte doit retourner E_NOTIMPL à partir de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="1b452-130">In this case, a host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b452-131">spécifications</span><span class="sxs-lookup"><span data-stu-id="1b452-131">Requirements</span></span>  
 <span data-ttu-id="1b452-132">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b452-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b452-133">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1b452-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1b452-134">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1b452-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1b452-135">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b452-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b452-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1b452-136">See also</span></span>

- [<span data-ttu-id="1b452-137">ICLRIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="1b452-137">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="1b452-138">IHostIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="1b452-138">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
