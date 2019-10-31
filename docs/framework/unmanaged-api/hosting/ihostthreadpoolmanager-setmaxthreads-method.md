---
title: IHostThreadPoolManager::SetMaxThreads, méthode
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.SetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::SetMaxThreads
helpviewer_keywords:
- IHostThreadPoolManager::SetMaxThreads method [.NET Framework hosting]
- SetMaxThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: 77cfd347-95c2-4425-b807-4ecc2a8d4578
topic_type:
- apiref
ms.openlocfilehash: 30c4ff93688396dd9a6a8086fbb53ad1c763ead0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141305"
---
# <a name="ihostthreadpoolmanagersetmaxthreads-method"></a><span data-ttu-id="848de-102">IHostThreadPoolManager::SetMaxThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="848de-102">IHostThreadPoolManager::SetMaxThreads Method</span></span>
<span data-ttu-id="848de-103">Définit le nombre maximal de threads que l’hôte peut conserver dans le pool de threads.</span><span class="sxs-lookup"><span data-stu-id="848de-103">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="848de-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="848de-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMaxThreads (  
    [in] DWORD MaxThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="848de-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="848de-105">Parameters</span></span>  
 `MaxThreads`  
 <span data-ttu-id="848de-106">Nombre maximal de threads de travail dans le pool de threads.</span><span class="sxs-lookup"><span data-stu-id="848de-106">The maximum number of worker threads in the thread pool.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="848de-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="848de-107">Return Value</span></span>  
  
|<span data-ttu-id="848de-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="848de-108">HRESULT</span></span>|<span data-ttu-id="848de-109">Description</span><span class="sxs-lookup"><span data-stu-id="848de-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="848de-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="848de-110">S_OK</span></span>|<span data-ttu-id="848de-111">`SetMaxThreads` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="848de-111">`SetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="848de-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="848de-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="848de-113">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="848de-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="848de-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="848de-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="848de-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="848de-115">The call timed out.</span></span>|  
|<span data-ttu-id="848de-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="848de-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="848de-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="848de-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="848de-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="848de-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="848de-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="848de-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="848de-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="848de-120">E_FAIL</span></span>|<span data-ttu-id="848de-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="848de-121">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="848de-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="848de-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="848de-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="848de-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="848de-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="848de-124">E_NOTIMPL</span></span>|<span data-ttu-id="848de-125">L’hôte ne fournit pas d’implémentation de `SetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="848de-125">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="848de-126">Notes</span><span class="sxs-lookup"><span data-stu-id="848de-126">Remarks</span></span>  
 <span data-ttu-id="848de-127">Aucun hôte n’est requis pour autoriser le CLR à configurer la taille du pool de threads.</span><span class="sxs-lookup"><span data-stu-id="848de-127">A host is not required to allow the CLR to configure the size of the thread pool.</span></span> <span data-ttu-id="848de-128">Certains hôtes peuvent souhaiter un contrôle exclusif sur le pool de threads, pour des raisons telles que l’implémentation, les performances ou l’évolutivité.</span><span class="sxs-lookup"><span data-stu-id="848de-128">Some hosts might want exclusive control over the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="848de-129">Dans ce cas, un hôte doit retourner une valeur HRESULT d’E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="848de-129">In this case, a host should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="848de-130">spécifications</span><span class="sxs-lookup"><span data-stu-id="848de-130">Requirements</span></span>  
 <span data-ttu-id="848de-131">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="848de-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="848de-132">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="848de-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="848de-133">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="848de-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="848de-134">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="848de-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="848de-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="848de-135">See also</span></span>

- <xref:System.Threading.ThreadPool.SetMaxThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="848de-136">GetMaxThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="848de-136">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)
- [<span data-ttu-id="848de-137">SetMinThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="848de-137">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)
- [<span data-ttu-id="848de-138">IHostThreadPoolManager, interface</span><span class="sxs-lookup"><span data-stu-id="848de-138">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
