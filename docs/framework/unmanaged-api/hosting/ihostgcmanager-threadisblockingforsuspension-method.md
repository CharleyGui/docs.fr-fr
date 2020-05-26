---
title: IHostGCManager::ThreadIsBlockingForSuspension, méthode
ms.date: 03/30/2017
api_name:
- IHostGCManager.ThreadIsBlockingForSuspension
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager::ThreadIsBlockingForSuspension
helpviewer_keywords:
- IHostGCManager::ThreadIsBlockingForSuspension method [.NET Framework hosting]
- ThreadIsBlockingForSuspension method [.NET Framework hosting]
ms.assetid: 2657d45d-26d2-4d0a-8473-32b652e3321d
topic_type:
- apiref
ms.openlocfilehash: 0417a4acc0f4f39d8254eb5d5df3b3e690921a8a
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804826"
---
# <a name="ihostgcmanagerthreadisblockingforsuspension-method"></a><span data-ttu-id="efdbe-102">IHostGCManager::ThreadIsBlockingForSuspension, méthode</span><span class="sxs-lookup"><span data-stu-id="efdbe-102">IHostGCManager::ThreadIsBlockingForSuspension Method</span></span>
<span data-ttu-id="efdbe-103">Avertit l’hôte que le thread à partir duquel l’appel de méthode a été effectué est sur le le bloc pour un garbage collection.</span><span class="sxs-lookup"><span data-stu-id="efdbe-103">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efdbe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="efdbe-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadIsBlockingForSuspension ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="efdbe-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="efdbe-105">Return Value</span></span>  
  
|<span data-ttu-id="efdbe-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="efdbe-106">HRESULT</span></span>|<span data-ttu-id="efdbe-107">Description</span><span class="sxs-lookup"><span data-stu-id="efdbe-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="efdbe-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="efdbe-108">S_OK</span></span>|<span data-ttu-id="efdbe-109">`ThreadIsBlockingForSuspension`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="efdbe-109">`ThreadIsBlockingForSuspension` returned successfully.</span></span>|  
|<span data-ttu-id="efdbe-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="efdbe-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="efdbe-111">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="efdbe-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="efdbe-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="efdbe-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="efdbe-113">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="efdbe-113">The call timed out.</span></span>|  
|<span data-ttu-id="efdbe-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="efdbe-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="efdbe-115">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="efdbe-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="efdbe-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="efdbe-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="efdbe-117">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="efdbe-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="efdbe-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="efdbe-118">E_FAIL</span></span>|<span data-ttu-id="efdbe-119">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="efdbe-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="efdbe-120">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="efdbe-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="efdbe-121">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="efdbe-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="efdbe-122">Notes</span><span class="sxs-lookup"><span data-stu-id="efdbe-122">Remarks</span></span>  
 <span data-ttu-id="efdbe-123">Le CLR appelle généralement la `ThreadIsBlockForSuspension` méthode en vue de la préparation d’un garbage collection, afin de permettre à l’hôte de replanifier le thread pour les tâches non managées.</span><span class="sxs-lookup"><span data-stu-id="efdbe-123">The CLR typically calls the `ThreadIsBlockForSuspension` method in preparation for a garbage collection, to give the host an opportunity to reschedule the thread for unmanaged tasks.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="efdbe-124">L’hôte peut replanifier des tâches uniquement après un appel à `ThreadIsBlockingForSuspension` .</span><span class="sxs-lookup"><span data-stu-id="efdbe-124">The host can reschedule tasks only after a call to `ThreadIsBlockingForSuspension`.</span></span> <span data-ttu-id="efdbe-125">Une fois que le runtime a appelé [SuspensionStarting](ihostgcmanager-suspensionstarting-method.md), l’hôte ne doit pas replanifier une tâche.</span><span class="sxs-lookup"><span data-stu-id="efdbe-125">After the runtime calls [SuspensionStarting](ihostgcmanager-suspensionstarting-method.md), the host must not reschedule a task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efdbe-126">Spécifications</span><span class="sxs-lookup"><span data-stu-id="efdbe-126">Requirements</span></span>  
 <span data-ttu-id="efdbe-127">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="efdbe-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efdbe-128">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="efdbe-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="efdbe-129">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="efdbe-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="efdbe-130">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="efdbe-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efdbe-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="efdbe-131">See also</span></span>

- [<span data-ttu-id="efdbe-132">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="efdbe-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="efdbe-133">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="efdbe-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="efdbe-134">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="efdbe-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="efdbe-135">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="efdbe-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="efdbe-136">IHostGCManager, interface</span><span class="sxs-lookup"><span data-stu-id="efdbe-136">IHostGCManager Interface</span></span>](ihostgcmanager-interface.md)
