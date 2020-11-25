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
ms.openlocfilehash: 6f6d57a52d960c975d468f370477b5d7e29c3aa2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727339"
---
# <a name="ihosttaskmanagerbeginthreadaffinity-method"></a><span data-ttu-id="bb28b-102">IHostTaskManager::BeginThreadAffinity, méthode</span><span class="sxs-lookup"><span data-stu-id="bb28b-102">IHostTaskManager::BeginThreadAffinity Method</span></span>

<span data-ttu-id="bb28b-103">Indique à l’hôte que le code managé entre dans une période dans laquelle la tâche actuelle ne doit pas être déplacée vers un autre thread de système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="bb28b-103">Notifies the host that managed code is entering a period in which the current task must not be moved to another operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb28b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb28b-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="bb28b-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="bb28b-105">Return Value</span></span>  
  
|<span data-ttu-id="bb28b-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bb28b-106">HRESULT</span></span>|<span data-ttu-id="bb28b-107">Description</span><span class="sxs-lookup"><span data-stu-id="bb28b-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bb28b-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="bb28b-108">S_OK</span></span>|<span data-ttu-id="bb28b-109">`BeginThreadAffinity` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="bb28b-109">`BeginThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="bb28b-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bb28b-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bb28b-111">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="bb28b-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bb28b-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bb28b-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bb28b-113">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="bb28b-113">The call timed out.</span></span>|  
|<span data-ttu-id="bb28b-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bb28b-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bb28b-115">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="bb28b-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bb28b-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bb28b-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bb28b-117">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="bb28b-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bb28b-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bb28b-118">E_FAIL</span></span>|<span data-ttu-id="bb28b-119">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="bb28b-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bb28b-120">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="bb28b-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bb28b-121">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="bb28b-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb28b-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="bb28b-122">Remarks</span></span>  

 <span data-ttu-id="bb28b-123">Le CLR appelle généralement `IHostTaskManager::BeginThreadAffinity` dans le contexte d’un appel à <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="bb28b-123">The CLR typically calls `IHostTaskManager::BeginThreadAffinity` in the context of a call to <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="bb28b-124">La tâche actuelle ne doit pas être replanifiée jusqu’à ce qu’un appel correspondant soit effectué à [IHostTaskManager :: EndThreadAffinity](ihosttaskmanager-endthreadaffinity-method.md).</span><span class="sxs-lookup"><span data-stu-id="bb28b-124">The current task must not be rescheduled until a corresponding call is made to [IHostTaskManager::EndThreadAffinity](ihosttaskmanager-endthreadaffinity-method.md).</span></span> <span data-ttu-id="bb28b-125">Les tâches peuvent être désactivées, mais lorsqu’elles sont réactivées, elles doivent être affectées au même thread de système d’exploitation à partir duquel elles ont été extraites. Les appels imbriqués à n' `BeginThreadAffinity` ont aucun effet, car l’appel fait référence à la tâche actuelle.</span><span class="sxs-lookup"><span data-stu-id="bb28b-125">Tasks can be switched out, but when they are switched back in, they must be assigned to the same operating system thread from which they were switched out. Nested calls to `BeginThreadAffinity` have no effect, because the call refers to the current task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb28b-126">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="bb28b-126">Requirements</span></span>  

 <span data-ttu-id="bb28b-127">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb28b-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb28b-128">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="bb28b-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bb28b-129">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bb28b-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bb28b-130">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb28b-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb28b-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bb28b-131">See also</span></span>

- [<span data-ttu-id="bb28b-132">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="bb28b-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="bb28b-133">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="bb28b-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="bb28b-134">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="bb28b-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="bb28b-135">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="bb28b-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
