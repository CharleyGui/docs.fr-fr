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
ms.openlocfilehash: 55727903a7f3c798e7472de6de5249de98af7ae7
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804674"
---
# <a name="ihostiocompletionmanagersetmaxthreads-method"></a><span data-ttu-id="e4a6a-102">IHostIoCompletionManager::SetMaxThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="e4a6a-102">IHostIoCompletionManager::SetMaxThreads Method</span></span>
<span data-ttu-id="e4a6a-103">Définit le nombre maximal de threads que l’hôte alloue aux demandes d’e/s de service.</span><span class="sxs-lookup"><span data-stu-id="e4a6a-103">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4a6a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4a6a-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMaxThreads (  
    [in] DWORD dwMaxIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4a6a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e4a6a-105">Parameters</span></span>  
 `dwMaxIoCompletionThreads`  
 <span data-ttu-id="e4a6a-106">dans Nombre maximal de threads à allouer pour les demandes d’e/s.</span><span class="sxs-lookup"><span data-stu-id="e4a6a-106">[in] The maximum number of threads to allot for I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e4a6a-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e4a6a-107">Return Value</span></span>  
  
|<span data-ttu-id="e4a6a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e4a6a-108">HRESULT</span></span>|<span data-ttu-id="e4a6a-109">Description</span><span class="sxs-lookup"><span data-stu-id="e4a6a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e4a6a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e4a6a-110">S_OK</span></span>|<span data-ttu-id="e4a6a-111">`SetMaxThreads`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="e4a6a-111">`SetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="e4a6a-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e4a6a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e4a6a-113">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="e4a6a-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e4a6a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e4a6a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e4a6a-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="e4a6a-115">The call timed out.</span></span>|  
|<span data-ttu-id="e4a6a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e4a6a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e4a6a-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="e4a6a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e4a6a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e4a6a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e4a6a-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="e4a6a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e4a6a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e4a6a-120">E_FAIL</span></span>|<span data-ttu-id="e4a6a-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="e4a6a-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e4a6a-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="e4a6a-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e4a6a-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e4a6a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e4a6a-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="e4a6a-124">E_NOTIMPL</span></span>|<span data-ttu-id="e4a6a-125">L’hôte ne fournit pas d’implémentation de `SetMaxThreads` .</span><span class="sxs-lookup"><span data-stu-id="e4a6a-125">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4a6a-126">Notes</span><span class="sxs-lookup"><span data-stu-id="e4a6a-126">Remarks</span></span>  
 <span data-ttu-id="e4a6a-127">`SetMaxThreads`fournit au CLR la possibilité de définir le nombre maximal de threads disponibles pour les demandes de service sur les ports d’e/s.</span><span class="sxs-lookup"><span data-stu-id="e4a6a-127">`SetMaxThreads` provides the CLR with an opportunity to set the maximum number of threads that are available to service requests on I/O ports.</span></span> <span data-ttu-id="e4a6a-128">Un hôte peut avoir besoin d’un contrôle exclusif sur la taille du pool de threads, pour des raisons telles que l’implémentation, les performances ou l’évolutivité.</span><span class="sxs-lookup"><span data-stu-id="e4a6a-128">A host might need exclusive control over the size of the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="e4a6a-129">Pour cette raison, l’hôte n’est pas tenu d’implémenter `SetMaxThreads` .</span><span class="sxs-lookup"><span data-stu-id="e4a6a-129">For this reason, the host is not required to implement `SetMaxThreads`.</span></span> <span data-ttu-id="e4a6a-130">Dans ce cas, un hôte doit retourner E_NOTIMPL à partir de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="e4a6a-130">In this case, a host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4a6a-131">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e4a6a-131">Requirements</span></span>  
 <span data-ttu-id="e4a6a-132">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4a6a-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4a6a-133">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e4a6a-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e4a6a-134">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e4a6a-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e4a6a-135">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4a6a-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4a6a-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e4a6a-136">See also</span></span>

- [<span data-ttu-id="e4a6a-137">ICLRIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="e4a6a-137">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="e4a6a-138">IHostIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="e4a6a-138">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
