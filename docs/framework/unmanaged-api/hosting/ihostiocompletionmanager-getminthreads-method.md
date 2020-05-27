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
ms.openlocfilehash: e748a731f2c6934f58a1cd838cc40ce4fd0e4652
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804722"
---
# <a name="ihostiocompletionmanagergetminthreads-method"></a><span data-ttu-id="e37b8-102">IHostIoCompletionManager::GetMinThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="e37b8-102">IHostIoCompletionManager::GetMinThreads Method</span></span>
<span data-ttu-id="e37b8-103">Obtient le nombre minimal de threads que l’hôte fournit pour traiter les demandes d’e/s.</span><span class="sxs-lookup"><span data-stu-id="e37b8-103">Gets the minimum number of threads that the host provides for processing I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e37b8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e37b8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMinThreads (  
    [out] DWORD *pdwMinIOCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e37b8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e37b8-105">Parameters</span></span>  
 `pdwMinIOCompletionThreads`  
 <span data-ttu-id="e37b8-106">à Pointeur vers le nombre minimal de threads que l’hôte fournit pour traiter les demandes d’e/s.</span><span class="sxs-lookup"><span data-stu-id="e37b8-106">[out] A pointer to the minimum number of threads that the host provides to process I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e37b8-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e37b8-107">Return Value</span></span>  
  
|<span data-ttu-id="e37b8-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e37b8-108">HRESULT</span></span>|<span data-ttu-id="e37b8-109">Description</span><span class="sxs-lookup"><span data-stu-id="e37b8-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e37b8-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e37b8-110">S_OK</span></span>|<span data-ttu-id="e37b8-111">`GetMinThreads`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="e37b8-111">`GetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="e37b8-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e37b8-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e37b8-113">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="e37b8-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e37b8-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e37b8-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e37b8-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="e37b8-115">The call timed out.</span></span>|  
|<span data-ttu-id="e37b8-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e37b8-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e37b8-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="e37b8-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e37b8-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e37b8-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e37b8-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="e37b8-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e37b8-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e37b8-120">E_FAIL</span></span>|<span data-ttu-id="e37b8-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="e37b8-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e37b8-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="e37b8-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e37b8-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e37b8-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e37b8-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="e37b8-124">E_NOTIMPL</span></span>|<span data-ttu-id="e37b8-125">L’hôte ne fournit pas d’implémentation de `GetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="e37b8-125">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e37b8-126">Notes</span><span class="sxs-lookup"><span data-stu-id="e37b8-126">Remarks</span></span>  
 <span data-ttu-id="e37b8-127">Un hôte peut souhaiter exercer un contrôle exclusif sur le nombre de threads alloués aux demandes d’e/s de service, pour des raisons telles que l’implémentation, les performances ou l’évolutivité.</span><span class="sxs-lookup"><span data-stu-id="e37b8-127">A host might want exclusive control over the number of threads allotted to service I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="e37b8-128">Pour cette raison, l’hôte n’est pas tenu d’implémenter `GetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="e37b8-128">For this reason, the host is not required to implement `GetMinThreads`.</span></span> <span data-ttu-id="e37b8-129">Dans ce cas, l’hôte doit retourner E_NOTIMPL à partir de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="e37b8-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e37b8-130">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e37b8-130">Requirements</span></span>  
 <span data-ttu-id="e37b8-131">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e37b8-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e37b8-132">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e37b8-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e37b8-133">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e37b8-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e37b8-134">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e37b8-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e37b8-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e37b8-135">See also</span></span>

- [<span data-ttu-id="e37b8-136">ICLRIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="e37b8-136">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="e37b8-137">IHostIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="e37b8-137">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
