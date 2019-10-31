---
title: ICLRTask::RudeAbort, méthode
ms.date: 03/30/2017
api_name:
- ICLRTask.RudeAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::RudeAbort
helpviewer_keywords:
- RudeAbort method, ICLRTask interface [.NET Framework hosting]
- ICLRTask::RudeAbort method [.NET Framework hosting]
ms.assetid: b5785468-fcd7-4cc3-8a5d-8796337b53fc
topic_type:
- apiref
ms.openlocfilehash: 69e3ecfc82985d52bd5b14e9faf2566e395b622b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124654"
---
# <a name="iclrtaskrudeabort-method"></a><span data-ttu-id="0209a-102">ICLRTask::RudeAbort, méthode</span><span class="sxs-lookup"><span data-stu-id="0209a-102">ICLRTask::RudeAbort Method</span></span>
<span data-ttu-id="0209a-103">Indique au common language runtime (CLR) d’abandonner immédiatement et sans condition la tâche représentée par l’instance d' [interface ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) actuelle.</span><span class="sxs-lookup"><span data-stu-id="0209a-103">Instructs the common language runtime (CLR) to abort the task represented by the current [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance immediately and unconditionally.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0209a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0209a-104">Syntax</span></span>  
  
```cpp  
HRESULT RudeAbort ();   
```  
  
## <a name="return-value"></a><span data-ttu-id="0209a-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="0209a-105">Return Value</span></span>  
  
|<span data-ttu-id="0209a-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0209a-106">HRESULT</span></span>|<span data-ttu-id="0209a-107">Description</span><span class="sxs-lookup"><span data-stu-id="0209a-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0209a-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="0209a-108">S_OK</span></span>|<span data-ttu-id="0209a-109">`RudeAbort` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="0209a-109">`RudeAbort` returned successfully.</span></span>|  
|<span data-ttu-id="0209a-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0209a-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0209a-111">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="0209a-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0209a-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0209a-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0209a-113">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="0209a-113">The call timed out.</span></span>|  
|<span data-ttu-id="0209a-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0209a-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0209a-115">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="0209a-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0209a-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0209a-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0209a-117">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="0209a-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0209a-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0209a-118">E_FAIL</span></span>|<span data-ttu-id="0209a-119">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="0209a-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0209a-120">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="0209a-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0209a-121">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0209a-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0209a-122">Notes</span><span class="sxs-lookup"><span data-stu-id="0209a-122">Remarks</span></span>  
 <span data-ttu-id="0209a-123">Un hôte appelle `RudeAbort` pour abandonner immédiatement une tâche.</span><span class="sxs-lookup"><span data-stu-id="0209a-123">A host calls `RudeAbort` to abort a task immediately.</span></span> <span data-ttu-id="0209a-124">Il n’est pas garanti que les finaliseurs et les routines de gestion des exceptions soient exécutées.</span><span class="sxs-lookup"><span data-stu-id="0209a-124">Finalizers and exception handling routines are not guaranteed to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0209a-125">spécifications</span><span class="sxs-lookup"><span data-stu-id="0209a-125">Requirements</span></span>  
 <span data-ttu-id="0209a-126">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0209a-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0209a-127">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0209a-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0209a-128">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0209a-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0209a-129">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0209a-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0209a-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0209a-130">See also</span></span>

- [<span data-ttu-id="0209a-131">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="0209a-131">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="0209a-132">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="0209a-132">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="0209a-133">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="0209a-133">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="0209a-134">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="0209a-134">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
