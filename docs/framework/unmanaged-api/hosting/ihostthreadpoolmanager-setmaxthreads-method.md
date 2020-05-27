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
ms.openlocfilehash: 53d42afda6668acc6462c419fcefd6bc1435a34c
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842450"
---
# <a name="ihostthreadpoolmanagersetmaxthreads-method"></a><span data-ttu-id="86e70-102">IHostThreadPoolManager::SetMaxThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="86e70-102">IHostThreadPoolManager::SetMaxThreads Method</span></span>
<span data-ttu-id="86e70-103">Définit le nombre maximal de threads que l’hôte peut conserver dans le pool de threads.</span><span class="sxs-lookup"><span data-stu-id="86e70-103">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86e70-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="86e70-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMaxThreads (  
    [in] DWORD MaxThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86e70-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="86e70-105">Parameters</span></span>  
 `MaxThreads`  
 <span data-ttu-id="86e70-106">Nombre maximal de threads de travail dans le pool de threads.</span><span class="sxs-lookup"><span data-stu-id="86e70-106">The maximum number of worker threads in the thread pool.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="86e70-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="86e70-107">Return Value</span></span>  
  
|<span data-ttu-id="86e70-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="86e70-108">HRESULT</span></span>|<span data-ttu-id="86e70-109">Description</span><span class="sxs-lookup"><span data-stu-id="86e70-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="86e70-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="86e70-110">S_OK</span></span>|<span data-ttu-id="86e70-111">`SetMaxThreads`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="86e70-111">`SetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="86e70-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="86e70-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="86e70-113">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="86e70-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="86e70-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="86e70-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="86e70-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="86e70-115">The call timed out.</span></span>|  
|<span data-ttu-id="86e70-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="86e70-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="86e70-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="86e70-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="86e70-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="86e70-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="86e70-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="86e70-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="86e70-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="86e70-120">E_FAIL</span></span>|<span data-ttu-id="86e70-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="86e70-121">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="86e70-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="86e70-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="86e70-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="86e70-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="86e70-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="86e70-124">E_NOTIMPL</span></span>|<span data-ttu-id="86e70-125">L’hôte ne fournit pas d’implémentation de `SetMaxThreads` .</span><span class="sxs-lookup"><span data-stu-id="86e70-125">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86e70-126">Remarques</span><span class="sxs-lookup"><span data-stu-id="86e70-126">Remarks</span></span>  
 <span data-ttu-id="86e70-127">Aucun hôte n’est requis pour autoriser le CLR à configurer la taille du pool de threads.</span><span class="sxs-lookup"><span data-stu-id="86e70-127">A host is not required to allow the CLR to configure the size of the thread pool.</span></span> <span data-ttu-id="86e70-128">Certains hôtes peuvent souhaiter un contrôle exclusif sur le pool de threads, pour des raisons telles que l’implémentation, les performances ou l’évolutivité.</span><span class="sxs-lookup"><span data-stu-id="86e70-128">Some hosts might want exclusive control over the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="86e70-129">Dans ce cas, un hôte doit retourner une valeur HRESULT de E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="86e70-129">In this case, a host should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86e70-130">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="86e70-130">Requirements</span></span>  
 <span data-ttu-id="86e70-131">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86e70-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86e70-132">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="86e70-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="86e70-133">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="86e70-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="86e70-134">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86e70-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86e70-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="86e70-135">See also</span></span>

- <xref:System.Threading.ThreadPool.SetMaxThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="86e70-136">GetMaxThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="86e70-136">GetMaxThreads Method</span></span>](ihostthreadpoolmanager-getmaxthreads-method.md)
- [<span data-ttu-id="86e70-137">SetMinThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="86e70-137">SetMinThreads Method</span></span>](ihostthreadpoolmanager-setminthreads-method.md)
- [<span data-ttu-id="86e70-138">IHostThreadPoolManager, interface</span><span class="sxs-lookup"><span data-stu-id="86e70-138">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
