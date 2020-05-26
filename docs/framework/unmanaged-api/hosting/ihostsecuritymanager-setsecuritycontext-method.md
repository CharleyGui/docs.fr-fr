---
title: IHostSecurityManager::SetSecurityContext, méthode
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.SetSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::SetSecurityContext
helpviewer_keywords:
- SetSecurityContext method [.NET Framework hosting]
- IHostSecurityManager::SetSecurityContext method [.NET Framework hosting]
ms.assetid: e4372384-ee69-48d7-97e0-8fab7866597a
topic_type:
- apiref
ms.openlocfilehash: 79ef08ef70ad1132ceacc3e2b997651e57032b9a
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803810"
---
# <a name="ihostsecuritymanagersetsecuritycontext-method"></a><span data-ttu-id="1277c-102">IHostSecurityManager::SetSecurityContext, méthode</span><span class="sxs-lookup"><span data-stu-id="1277c-102">IHostSecurityManager::SetSecurityContext Method</span></span>
<span data-ttu-id="1277c-103">Définit le contexte de sécurité du thread en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="1277c-103">Sets the security context of the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1277c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1277c-104">Syntax</span></span>  
  
```cpp  
HRESULT SetSecurityContext (  
    [in]  EContextType eContextType,  
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1277c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1277c-105">Parameters</span></span>  
 `eContextType`  
 <span data-ttu-id="1277c-106">dans L’une des valeurs [EContextType,](econtexttype-enumeration.md) , indiquant le type de contexte que le Common Language Runtime (CLR) place sur l’hôte.</span><span class="sxs-lookup"><span data-stu-id="1277c-106">[in] One of the [EContextType](econtexttype-enumeration.md) values, indicating what type of context the common language runtime (CLR) is placing on the host.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="1277c-107">à Pointeur vers l’adresse d’un nouvel objet [IHostSecurityContext](ihostsecuritycontext-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="1277c-107">[out] A pointer to the address of a new [IHostSecurityContext](ihostsecuritycontext-interface.md) object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1277c-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="1277c-108">Return Value</span></span>  
  
|<span data-ttu-id="1277c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1277c-109">HRESULT</span></span>|<span data-ttu-id="1277c-110">Description</span><span class="sxs-lookup"><span data-stu-id="1277c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1277c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="1277c-111">S_OK</span></span>|<span data-ttu-id="1277c-112">`SetSecurityContext`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="1277c-112">`SetSecurityContext` returned successfully.</span></span>|  
|<span data-ttu-id="1277c-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1277c-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1277c-114">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="1277c-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1277c-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1277c-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1277c-116">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="1277c-116">The call timed out.</span></span>|  
|<span data-ttu-id="1277c-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1277c-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1277c-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="1277c-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1277c-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1277c-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1277c-120">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="1277c-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1277c-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1277c-121">E_FAIL</span></span>|<span data-ttu-id="1277c-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="1277c-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1277c-123">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="1277c-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1277c-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1277c-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1277c-125">Notes</span><span class="sxs-lookup"><span data-stu-id="1277c-125">Remarks</span></span>  
 <span data-ttu-id="1277c-126">Le CLR appelle `SetSecurityContext` dans plusieurs scénarios.</span><span class="sxs-lookup"><span data-stu-id="1277c-126">The CLR calls `SetSecurityContext` in several scenarios.</span></span> <span data-ttu-id="1277c-127">Avant d’exécuter des constructeurs et des finaliseurs de classe et de module, le CLR appelle `SetSecurityContext` pour protéger l’hôte des échecs d’exécution.</span><span class="sxs-lookup"><span data-stu-id="1277c-127">Before it executes class and module constructors and finalizers, the CLR calls `SetSecurityContext` to protect the host from execution failures.</span></span> <span data-ttu-id="1277c-128">Il réinitialise ensuite le contexte de sécurité à son état d’origine après l’exécution du constructeur ou du finaliseur, en utilisant un autre appel à `SetSecurityContext` .</span><span class="sxs-lookup"><span data-stu-id="1277c-128">It then resets the security context to its original state after execution of the constructor or finalizer, by using another call to `SetSecurityContext`.</span></span> <span data-ttu-id="1277c-129">Un modèle similaire se produit avec l’exécution d’e/s.</span><span class="sxs-lookup"><span data-stu-id="1277c-129">A similar pattern occurs with I/O completion.</span></span> <span data-ttu-id="1277c-130">Si l’hôte implémente [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md), le CLR appelle `SetSecurityContext` après que l’hôte a appelé [ICLRIoCompletionManager :: OnComplete](iclriocompletionmanager-oncomplete-method.md).</span><span class="sxs-lookup"><span data-stu-id="1277c-130">If the host implements [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md), the CLR calls `SetSecurityContext` after the host calls [ICLRIoCompletionManager::OnComplete](iclriocompletionmanager-oncomplete-method.md).</span></span>  
  
 <span data-ttu-id="1277c-131">À des points asynchrones dans les threads de travail, le CLR appelle `SetSecurityContext` dans <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> ou dans [IHostThreadPoolManager :: QueueUserWorkItem](ihostthreadpoolmanager-queueuserworkitem-method.md), selon que l’hôte ou le CLR implémente le pool de threads.</span><span class="sxs-lookup"><span data-stu-id="1277c-131">At asynchronous points in worker threads, the CLR calls `SetSecurityContext` within <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> or within [IHostThreadPoolManager::QueueUserWorkItem](ihostthreadpoolmanager-queueuserworkitem-method.md), depending on whether the host or the CLR is implementing the thread pool.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1277c-132">Spécifications</span><span class="sxs-lookup"><span data-stu-id="1277c-132">Requirements</span></span>  
 <span data-ttu-id="1277c-133">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1277c-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1277c-134">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1277c-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1277c-135">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1277c-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1277c-136">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1277c-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1277c-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1277c-137">See also</span></span>

- <xref:System.Threading.ThreadPool?displayProperty=nameWithType>
- [<span data-ttu-id="1277c-138">EContextType, énumération</span><span class="sxs-lookup"><span data-stu-id="1277c-138">EContextType Enumeration</span></span>](econtexttype-enumeration.md)
- [<span data-ttu-id="1277c-139">ICLRIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="1277c-139">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="1277c-140">IHostIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="1277c-140">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="1277c-141">IHostSecurityContext, interface</span><span class="sxs-lookup"><span data-stu-id="1277c-141">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="1277c-142">IHostSecurityManager, interface</span><span class="sxs-lookup"><span data-stu-id="1277c-142">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="1277c-143">IHostThreadPoolManager, interface</span><span class="sxs-lookup"><span data-stu-id="1277c-143">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
