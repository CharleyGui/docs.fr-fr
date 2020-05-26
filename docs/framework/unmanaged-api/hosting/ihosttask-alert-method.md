---
title: IHostTask::Alert, méthode
ms.date: 03/30/2017
api_name:
- IHostTask.Alert
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::Alert
helpviewer_keywords:
- IHostTask::Alert method [.NET Framework hosting]
- Alert method, IHostTask interface [.NET Framework hosting]
ms.assetid: 5245d4b5-b6c3-48df-9cb9-8caf059f43fb
topic_type:
- apiref
ms.openlocfilehash: 7271fe8e28da0bb5fd878aae5d36ab703e64ebf0
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803020"
---
# <a name="ihosttaskalert-method"></a><span data-ttu-id="c980a-102">IHostTask::Alert, méthode</span><span class="sxs-lookup"><span data-stu-id="c980a-102">IHostTask::Alert Method</span></span>
<span data-ttu-id="c980a-103">Demande que l’hôte réactive la tâche représentée par l’instance [IHostTask](ihosttask-interface.md) actuelle, afin que la tâche puisse être abandonnée.</span><span class="sxs-lookup"><span data-stu-id="c980a-103">Requests that the host wake the task represented by the current [IHostTask](ihosttask-interface.md) instance, so the task can be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c980a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c980a-104">Syntax</span></span>  
  
```cpp  
HRESULT Alert ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="c980a-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c980a-105">Return Value</span></span>  
  
|<span data-ttu-id="c980a-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c980a-106">HRESULT</span></span>|<span data-ttu-id="c980a-107">Description</span><span class="sxs-lookup"><span data-stu-id="c980a-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c980a-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="c980a-108">S_OK</span></span>|<span data-ttu-id="c980a-109">Retour réussi de la méthode.</span><span class="sxs-lookup"><span data-stu-id="c980a-109">The method returned successfully.</span></span>|  
|<span data-ttu-id="c980a-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c980a-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c980a-111">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="c980a-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c980a-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c980a-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c980a-113">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="c980a-113">The call timed out.</span></span>|  
|<span data-ttu-id="c980a-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c980a-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c980a-115">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="c980a-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c980a-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c980a-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c980a-117">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="c980a-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c980a-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c980a-118">E_FAIL</span></span>|<span data-ttu-id="c980a-119">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="c980a-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c980a-120">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="c980a-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c980a-121">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c980a-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c980a-122">Notes</span><span class="sxs-lookup"><span data-stu-id="c980a-122">Remarks</span></span>  
 <span data-ttu-id="c980a-123">Le CLR appelle la `Alert` méthode quand <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> est appelé à partir du code utilisateur ou lorsque le <xref:System.AppDomain> associé à l’objet actuel <xref:System.Threading.Thread> s’arrête.</span><span class="sxs-lookup"><span data-stu-id="c980a-123">The CLR calls the `Alert` method when <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> is called from user code, or when the <xref:System.AppDomain> associated with the current <xref:System.Threading.Thread> shuts down.</span></span> <span data-ttu-id="c980a-124">L’hôte doit être retourné immédiatement, car l’appel est effectué de façon asynchrone.</span><span class="sxs-lookup"><span data-stu-id="c980a-124">The host must return immediately, because the call is made asynchronously.</span></span> <span data-ttu-id="c980a-125">Si l’hôte ne peut pas alerter la tâche immédiatement, il doit se réveiller la prochaine fois qu’il entre dans un État dans lequel il peut être alerté.</span><span class="sxs-lookup"><span data-stu-id="c980a-125">If the host cannot alert the task immediately, it must wake up the next time it enters a state in which it can be alerted.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c980a-126">`Alert`affecte uniquement les tâches auxquelles le runtime a passé une [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) valeur de WAIT_ALERTABLE à des méthodes telles que [join](ihosttask-join-method.md).</span><span class="sxs-lookup"><span data-stu-id="c980a-126">`Alert` affects only those tasks to which the runtime has passed a [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) value of WAIT_ALERTABLE to methods such as [Join](ihosttask-join-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c980a-127">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c980a-127">Requirements</span></span>  
 <span data-ttu-id="c980a-128">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c980a-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c980a-129">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c980a-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c980a-130">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c980a-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c980a-131">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c980a-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c980a-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c980a-132">See also</span></span>

- [<span data-ttu-id="c980a-133">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="c980a-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="c980a-134">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="c980a-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="c980a-135">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="c980a-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="c980a-136">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="c980a-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
