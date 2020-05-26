---
title: IHostIoCompletionManager::GetAvailableThreads, méthode
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetAvailableThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetAvailableThreads
helpviewer_keywords:
- GetAvailableThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::GetAvailableThreads method [.NET Framework hosting]
ms.assetid: bab363d1-b859-47a4-9884-5661c611cce7
topic_type:
- apiref
ms.openlocfilehash: 7ea7395bb1f185ba59940d76def562ab5440e560
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804766"
---
# <a name="ihostiocompletionmanagergetavailablethreads-method"></a><span data-ttu-id="f8f4c-102">IHostIoCompletionManager::GetAvailableThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="f8f4c-102">IHostIoCompletionManager::GetAvailableThreads Method</span></span>
<span data-ttu-id="f8f4c-103">Obtient le nombre de threads de terminaison d’e/s, du nombre total de threads gérés par l’hôte, qui ne traitent pas actuellement les demandes.</span><span class="sxs-lookup"><span data-stu-id="f8f4c-103">Gets the number of I/O completion threads, of the total number of threads managed by the host, that are not currently servicing requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8f4c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8f4c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f8f4c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f8f4c-105">Parameters</span></span>  
 `pdwAvailableIoCompletionThreads`  
 <span data-ttu-id="f8f4c-106">à Pointeur vers le nombre de threads de terminaison d’e/s gérés par l’hôte actuellement disponibles pour les demandes de service.</span><span class="sxs-lookup"><span data-stu-id="f8f4c-106">[out] A pointer to the number of I/O completion threads managed by the host that are currently available to service requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f8f4c-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f8f4c-107">Return Value</span></span>  
  
|<span data-ttu-id="f8f4c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f8f4c-108">HRESULT</span></span>|<span data-ttu-id="f8f4c-109">Description</span><span class="sxs-lookup"><span data-stu-id="f8f4c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f8f4c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f8f4c-110">S_OK</span></span>|<span data-ttu-id="f8f4c-111">`GetAvailableThreads`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="f8f4c-111">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="f8f4c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f8f4c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f8f4c-113">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="f8f4c-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f8f4c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f8f4c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f8f4c-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="f8f4c-115">The call timed out.</span></span>|  
|<span data-ttu-id="f8f4c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f8f4c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f8f4c-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="f8f4c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f8f4c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f8f4c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f8f4c-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="f8f4c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f8f4c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f8f4c-120">E_FAIL</span></span>|<span data-ttu-id="f8f4c-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="f8f4c-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f8f4c-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="f8f4c-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f8f4c-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f8f4c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f8f4c-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="f8f4c-124">E_NOTIMPL</span></span>|<span data-ttu-id="f8f4c-125">L’hôte ne fournit pas d’implémentation de `GetAvailableThreads` .</span><span class="sxs-lookup"><span data-stu-id="f8f4c-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8f4c-126">Notes</span><span class="sxs-lookup"><span data-stu-id="f8f4c-126">Remarks</span></span>  
 <span data-ttu-id="f8f4c-127">Un hôte peut souhaiter un contrôle exclusif sur la taille du pool de threads de terminaison d’e/s, pour des raisons telles que l’implémentation, les performances ou l’évolutivité.</span><span class="sxs-lookup"><span data-stu-id="f8f4c-127">A host might want exclusive control over the size of the I/O completion thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="f8f4c-128">Par conséquent, l’hôte n’est pas tenu d’implémenter `GetAvailableThreads` .</span><span class="sxs-lookup"><span data-stu-id="f8f4c-128">Therefore, the host is not required to implement `GetAvailableThreads`.</span></span> <span data-ttu-id="f8f4c-129">Dans ce cas, l’hôte doit retourner E_NOTIMPL à partir de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="f8f4c-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8f4c-130">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f8f4c-130">Requirements</span></span>  
 <span data-ttu-id="f8f4c-131">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8f4c-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8f4c-132">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f8f4c-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f8f4c-133">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f8f4c-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f8f4c-134">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8f4c-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8f4c-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8f4c-135">See also</span></span>

- [<span data-ttu-id="f8f4c-136">ICLRIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="f8f4c-136">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="f8f4c-137">IHostIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="f8f4c-137">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
