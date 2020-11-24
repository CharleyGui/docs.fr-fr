---
title: ICLRTask::Abort, méthode
ms.date: 03/30/2017
api_name:
- ICLRTask.Abort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::Abort
helpviewer_keywords:
- ICLRTask::Abort method [.NET Framework hosting]
- Abort method, ICLRTask interface [.NET Framework hosting]
ms.assetid: b3594b5f-2e41-4e36-9096-3586276a138c
topic_type:
- apiref
ms.openlocfilehash: aadbbb5fc6abd3829f14670e42149174f6ef238d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690848"
---
# <a name="iclrtaskabort-method"></a><span data-ttu-id="8f40d-102">ICLRTask::Abort, méthode</span><span class="sxs-lookup"><span data-stu-id="8f40d-102">ICLRTask::Abort Method</span></span>

<span data-ttu-id="8f40d-103">Demande que le common language runtime (CLR) abandonne la tâche représentée par l’instance d' [ICLRTask](iclrtask-interface.md) actuelle.</span><span class="sxs-lookup"><span data-stu-id="8f40d-103">Requests that the common language runtime (CLR) abort the task that the current [ICLRTask](iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f40d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8f40d-104">Syntax</span></span>  
  
```cpp  
HRESULT Abort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="8f40d-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="8f40d-105">Return Value</span></span>  
  
|<span data-ttu-id="8f40d-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8f40d-106">HRESULT</span></span>|<span data-ttu-id="8f40d-107">Description</span><span class="sxs-lookup"><span data-stu-id="8f40d-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8f40d-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="8f40d-108">S_OK</span></span>|<span data-ttu-id="8f40d-109">`Abort` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="8f40d-109">`Abort` returned successfully.</span></span>|  
|<span data-ttu-id="8f40d-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8f40d-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8f40d-111">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="8f40d-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8f40d-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8f40d-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8f40d-113">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="8f40d-113">The call timed out.</span></span>|  
|<span data-ttu-id="8f40d-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8f40d-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8f40d-115">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="8f40d-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8f40d-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8f40d-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8f40d-117">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="8f40d-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8f40d-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8f40d-118">E_FAIL</span></span>|<span data-ttu-id="8f40d-119">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="8f40d-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8f40d-120">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="8f40d-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8f40d-121">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8f40d-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f40d-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="8f40d-122">Remarks</span></span>  

 <span data-ttu-id="8f40d-123">Le CLR déclenche une <xref:System.Threading.ThreadAbortException> lorsque l’hôte appelle `Abort` .</span><span class="sxs-lookup"><span data-stu-id="8f40d-123">The CLR raises a <xref:System.Threading.ThreadAbortException> when the host calls `Abort`.</span></span> <span data-ttu-id="8f40d-124">Elle est retournée immédiatement après l’initialisation des informations sur l’exception, sans attendre que le code utilisateur, tel que les finaliseurs ou les mécanismes de gestion des exceptions, s’exécute.</span><span class="sxs-lookup"><span data-stu-id="8f40d-124">It returns immediately after the exception information is initialized, without waiting for user code, such as finalizers or exception handling mechanisms, to execute.</span></span> <span data-ttu-id="8f40d-125">Les appels à `Abort` renvoient donc rapidement.</span><span class="sxs-lookup"><span data-stu-id="8f40d-125">Calls to `Abort` thus return quickly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f40d-126">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8f40d-126">Requirements</span></span>  

 <span data-ttu-id="8f40d-127">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f40d-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f40d-128">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8f40d-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8f40d-129">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8f40d-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8f40d-130">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f40d-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f40d-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8f40d-131">See also</span></span>

- [<span data-ttu-id="8f40d-132">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="8f40d-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="8f40d-133">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="8f40d-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="8f40d-134">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="8f40d-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="8f40d-135">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="8f40d-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
