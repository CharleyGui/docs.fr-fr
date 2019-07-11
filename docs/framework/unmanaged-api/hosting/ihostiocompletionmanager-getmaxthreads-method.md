---
title: IHostIoCompletionManager::GetMaxThreads, méthode
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetMaxThreads
helpviewer_keywords:
- IHostIoCompletionManager::GetMaxThreads method [.NET Framework hosting]
- GetMaxThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: e7a6cadc-2433-4472-a701-58891abcde45
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5fcd66914448fa63c892f7285b8cd364d4cacc5f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779211"
---
# <a name="ihostiocompletionmanagergetmaxthreads-method"></a><span data-ttu-id="9e34a-102">IHostIoCompletionManager::GetMaxThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="9e34a-102">IHostIoCompletionManager::GetMaxThreads Method</span></span>
<span data-ttu-id="9e34a-103">Obtient le nombre maximal de threads que l’hôte peut allouer pour traiter les demandes d’e/s.</span><span class="sxs-lookup"><span data-stu-id="9e34a-103">Gets the maximum number of threads that the host can allot to service I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e34a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9e34a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMaxThreads (  
    [out] DWORD *pdwMaxIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e34a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9e34a-105">Parameters</span></span>  
 `pdwMaxIoCompletionThreads`  
 <span data-ttu-id="9e34a-106">[out] Pointeur vers le nombre maximal de threads du pool de threads que l’hôte peut allouer pour traiter les demandes d’e/s.</span><span class="sxs-lookup"><span data-stu-id="9e34a-106">[out] A pointer to the maximum number of threads in the thread pool that the host can allot to service I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9e34a-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="9e34a-107">Return Value</span></span>  
  
|<span data-ttu-id="9e34a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9e34a-108">HRESULT</span></span>|<span data-ttu-id="9e34a-109">Description</span><span class="sxs-lookup"><span data-stu-id="9e34a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9e34a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9e34a-110">S_OK</span></span>|<span data-ttu-id="9e34a-111">`GetMaxThreads` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="9e34a-111">`GetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="9e34a-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9e34a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9e34a-113">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="9e34a-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9e34a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9e34a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9e34a-115">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="9e34a-115">The call timed out.</span></span>|  
|<span data-ttu-id="9e34a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9e34a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9e34a-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="9e34a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9e34a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9e34a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9e34a-119">Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="9e34a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9e34a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9e34a-120">E_FAIL</span></span>|<span data-ttu-id="9e34a-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="9e34a-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9e34a-122">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus.</span><span class="sxs-lookup"><span data-stu-id="9e34a-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9e34a-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9e34a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9e34a-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="9e34a-124">E_NOTIMPL</span></span>|<span data-ttu-id="9e34a-125">L’hôte ne fournit pas une implémentation de `GetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="9e34a-125">The host does not provide an implementation of `GetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e34a-126">Notes</span><span class="sxs-lookup"><span data-stu-id="9e34a-126">Remarks</span></span>  
 <span data-ttu-id="9e34a-127">Un hôte peut souhaiter le contrôle exclusif sur le nombre de threads pouvant être alloués pour traiter les demandes d’e/s, pour des raisons telles que l’implémentation, de performances ou d’évolutivité.</span><span class="sxs-lookup"><span data-stu-id="9e34a-127">A host might want exclusive control over the number of threads that can be allotted to process I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="9e34a-128">Pour cette raison, l’hôte n’est pas nécessaire d’implémenter `GetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="9e34a-128">For this reason, the host is not required to implement `GetMaxThreads`.</span></span> <span data-ttu-id="9e34a-129">Dans ce cas, l’hôte doit retourner E_NOTIMPL à partir de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="9e34a-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e34a-130">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9e34a-130">Requirements</span></span>  
 <span data-ttu-id="9e34a-131">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e34a-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e34a-132">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9e34a-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9e34a-133">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9e34a-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9e34a-134">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e34a-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e34a-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9e34a-135">See also</span></span>

- [<span data-ttu-id="9e34a-136">ICLRIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="9e34a-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="9e34a-137">IHostIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="9e34a-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
