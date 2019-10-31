---
title: IHostThreadPoolManager::SetMinThreads, méthode
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.SetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::SetMinThreads
helpviewer_keywords:
- SetMinThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
- IHostThreadPoolManager::SetMinThreads method [.NET Framework hosting]
ms.assetid: 10409db9-9fd2-4e4d-b8cd-cf6fec0afaa2
topic_type:
- apiref
ms.openlocfilehash: f2d2665382559596563d9b155d2afa4d99c91ee7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141261"
---
# <a name="ihostthreadpoolmanagersetminthreads-method"></a><span data-ttu-id="814a3-102">IHostThreadPoolManager::SetMinThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="814a3-102">IHostThreadPoolManager::SetMinThreads Method</span></span>
<span data-ttu-id="814a3-103">Définit le nombre minimal de threads inactifs que l’hôte doit gérer en prévision des demandes.</span><span class="sxs-lookup"><span data-stu-id="814a3-103">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="814a3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="814a3-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMinThreads (  
    [in] DWORD MinThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="814a3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="814a3-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="814a3-106">dans Nouveau nombre minimal de threads que l’hôte doit conserver.</span><span class="sxs-lookup"><span data-stu-id="814a3-106">[in] The new minimum number of threads that the host must maintain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="814a3-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="814a3-107">Return Value</span></span>  
  
|<span data-ttu-id="814a3-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="814a3-108">HRESULT</span></span>|<span data-ttu-id="814a3-109">Description</span><span class="sxs-lookup"><span data-stu-id="814a3-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="814a3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="814a3-110">S_OK</span></span>|<span data-ttu-id="814a3-111">`SetMinThreads` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="814a3-111">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="814a3-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="814a3-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="814a3-113">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="814a3-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="814a3-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="814a3-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="814a3-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="814a3-115">The call timed out.</span></span>|  
|<span data-ttu-id="814a3-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="814a3-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="814a3-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="814a3-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="814a3-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="814a3-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="814a3-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="814a3-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="814a3-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="814a3-120">E_FAIL</span></span>|<span data-ttu-id="814a3-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="814a3-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="814a3-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="814a3-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="814a3-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="814a3-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="814a3-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="814a3-124">E_NOTIMPL</span></span>|<span data-ttu-id="814a3-125">L’hôte ne fournit pas d’implémentation de `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="814a3-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="814a3-126">Notes</span><span class="sxs-lookup"><span data-stu-id="814a3-126">Remarks</span></span>  
 <span data-ttu-id="814a3-127">Un hôte n’est pas requis pour fournir une implémentation de `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="814a3-127">A host is not required to provide an implementation of `SetMinThreads`.</span></span> <span data-ttu-id="814a3-128">Dans ce cas, elle doit retourner une valeur HRESULT d’E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="814a3-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="814a3-129">spécifications</span><span class="sxs-lookup"><span data-stu-id="814a3-129">Requirements</span></span>  
 <span data-ttu-id="814a3-130">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="814a3-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="814a3-131">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="814a3-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="814a3-132">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="814a3-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="814a3-133">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="814a3-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="814a3-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="814a3-134">See also</span></span>

- <xref:System.Threading.ThreadPool.SetMinThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="814a3-135">GetMinThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="814a3-135">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)
- [<span data-ttu-id="814a3-136">SetMaxThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="814a3-136">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)
- [<span data-ttu-id="814a3-137">IHostThreadPoolManager, interface</span><span class="sxs-lookup"><span data-stu-id="814a3-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
