---
title: IHostTaskManager::BeginThreadAffinity, méthode
ms.date: 03/30/2017
api_name:
- IHostTaskManager.BeginThreadAffinity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::BeginThreadAffinity
helpviewer_keywords:
- IHostTaskManager::BeginThreadAffinity method [.NET Framework hosting]
- BeginThreadAffinity method [.NET Framework hosting]
ms.assetid: fea3ab88-ce41-4c5a-847b-bb78cd748da6
topic_type:
- apiref
ms.openlocfilehash: 7c157cf27d2fe86288024a6c35e6dcbea3c46347
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133110"
---
# <a name="ihosttaskmanagerbeginthreadaffinity-method"></a><span data-ttu-id="48721-102">IHostTaskManager::BeginThreadAffinity, méthode</span><span class="sxs-lookup"><span data-stu-id="48721-102">IHostTaskManager::BeginThreadAffinity Method</span></span>
<span data-ttu-id="48721-103">Indique à l’hôte que le code managé entre dans une période dans laquelle la tâche actuelle ne doit pas être déplacée vers un autre thread de système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="48721-103">Notifies the host that managed code is entering a period in which the current task must not be moved to another operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48721-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="48721-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="48721-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="48721-105">Return Value</span></span>  
  
|<span data-ttu-id="48721-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="48721-106">HRESULT</span></span>|<span data-ttu-id="48721-107">Description</span><span class="sxs-lookup"><span data-stu-id="48721-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="48721-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="48721-108">S_OK</span></span>|<span data-ttu-id="48721-109">`BeginThreadAffinity` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="48721-109">`BeginThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="48721-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="48721-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="48721-111">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="48721-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="48721-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="48721-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="48721-113">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="48721-113">The call timed out.</span></span>|  
|<span data-ttu-id="48721-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="48721-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="48721-115">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="48721-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="48721-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="48721-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="48721-117">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="48721-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="48721-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="48721-118">E_FAIL</span></span>|<span data-ttu-id="48721-119">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="48721-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="48721-120">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="48721-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="48721-121">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="48721-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48721-122">Notes</span><span class="sxs-lookup"><span data-stu-id="48721-122">Remarks</span></span>  
 <span data-ttu-id="48721-123">Le CLR appelle généralement `IHostTaskManager::BeginThreadAffinity` dans le contexte d’un appel à <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="48721-123">The CLR typically calls `IHostTaskManager::BeginThreadAffinity` in the context of a call to <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="48721-124">La tâche actuelle ne doit pas être replanifiée jusqu’à ce qu’un appel correspondant soit effectué à [IHostTaskManager :: EndThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md).</span><span class="sxs-lookup"><span data-stu-id="48721-124">The current task must not be rescheduled until a corresponding call is made to [IHostTaskManager::EndThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md).</span></span> <span data-ttu-id="48721-125">Les tâches peuvent être désactivées, mais lorsqu’elles sont réactivées, elles doivent être affectées au même thread de système d’exploitation à partir duquel elles ont été extraites. Les appels imbriqués à `BeginThreadAffinity` n’ont aucun effet, car l’appel fait référence à la tâche actuelle.</span><span class="sxs-lookup"><span data-stu-id="48721-125">Tasks can be switched out, but when they are switched back in, they must be assigned to the same operating system thread from which they were switched out. Nested calls to `BeginThreadAffinity` have no effect, because the call refers to the current task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48721-126">spécifications</span><span class="sxs-lookup"><span data-stu-id="48721-126">Requirements</span></span>  
 <span data-ttu-id="48721-127">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48721-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48721-128">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="48721-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="48721-129">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="48721-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="48721-130">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48721-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48721-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="48721-131">See also</span></span>

- [<span data-ttu-id="48721-132">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="48721-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="48721-133">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="48721-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="48721-134">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="48721-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="48721-135">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="48721-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
