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
ms.openlocfilehash: aacf9de36dc39b63ed36b672e31f40704413d608
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176329"
---
# <a name="iclrtaskrudeabort-method"></a><span data-ttu-id="0edac-102">ICLRTask::RudeAbort, méthode</span><span class="sxs-lookup"><span data-stu-id="0edac-102">ICLRTask::RudeAbort Method</span></span>
<span data-ttu-id="0edac-103">Demande au temps d’exécution de langue commune (CLR) d’interrompre la tâche représentée par l’instance actuelle [d’interface ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) immédiatement et sans condition.</span><span class="sxs-lookup"><span data-stu-id="0edac-103">Instructs the common language runtime (CLR) to abort the task represented by the current [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance immediately and unconditionally.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0edac-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0edac-104">Syntax</span></span>  
  
```cpp  
HRESULT RudeAbort ();
```  
  
## <a name="return-value"></a><span data-ttu-id="0edac-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="0edac-105">Return Value</span></span>  
  
|<span data-ttu-id="0edac-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0edac-106">HRESULT</span></span>|<span data-ttu-id="0edac-107">Description</span><span class="sxs-lookup"><span data-stu-id="0edac-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0edac-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="0edac-108">S_OK</span></span>|<span data-ttu-id="0edac-109">`RudeAbort`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="0edac-109">`RudeAbort` returned successfully.</span></span>|  
|<span data-ttu-id="0edac-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0edac-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0edac-111">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un état dans lequel il ne peut pas exécuter le code géré ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="0edac-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0edac-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0edac-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0edac-113">L’appel s’est fait chronométrer.</span><span class="sxs-lookup"><span data-stu-id="0edac-113">The call timed out.</span></span>|  
|<span data-ttu-id="0edac-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0edac-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0edac-115">L’appelant n’est pas propriétaire de la serrure.</span><span class="sxs-lookup"><span data-stu-id="0edac-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0edac-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0edac-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0edac-117">Un événement a été annulé alors qu’un fil bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="0edac-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0edac-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0edac-118">E_FAIL</span></span>|<span data-ttu-id="0edac-119">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="0edac-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0edac-120">Lorsqu’une méthode revient E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="0edac-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0edac-121">Les appels ultérieurs aux méthodes d’hébergement reviennent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0edac-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0edac-122">Notes </span><span class="sxs-lookup"><span data-stu-id="0edac-122">Remarks</span></span>  
 <span data-ttu-id="0edac-123">Un hôte `RudeAbort` appelle à interrompre immédiatement une tâche.</span><span class="sxs-lookup"><span data-stu-id="0edac-123">A host calls `RudeAbort` to abort a task immediately.</span></span> <span data-ttu-id="0edac-124">Les finalisateurs et les routines de manutention d’exception ne sont pas garantis pour être exécutés.</span><span class="sxs-lookup"><span data-stu-id="0edac-124">Finalizers and exception handling routines are not guaranteed to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0edac-125">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0edac-125">Requirements</span></span>  
 <span data-ttu-id="0edac-126">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0edac-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0edac-127">**En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor</span><span class="sxs-lookup"><span data-stu-id="0edac-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0edac-128">**Bibliothèque:** Inclus comme une ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0edac-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0edac-129">**.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0edac-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0edac-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0edac-130">See also</span></span>

- [<span data-ttu-id="0edac-131">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="0edac-131">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="0edac-132">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="0edac-132">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="0edac-133">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="0edac-133">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="0edac-134">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="0edac-134">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
