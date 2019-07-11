---
title: ICLRTask::GetMemStats, méthode
ms.date: 03/30/2017
api_name:
- ICLRTask.GetMemStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::GetMemStats
helpviewer_keywords:
- ICLRTask::GetMemStats method [.NET Framework hosting]
- GetMemStats method [.NET Framework hosting]
ms.assetid: c9e07657-1682-4c30-a336-f8658ff1a125
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ab388459df88e91093459658ced4d4b4eb023460
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758991"
---
# <a name="iclrtaskgetmemstats-method"></a><span data-ttu-id="179dd-102">ICLRTask::GetMemStats, méthode</span><span class="sxs-lookup"><span data-stu-id="179dd-102">ICLRTask::GetMemStats Method</span></span>
<span data-ttu-id="179dd-103">Obtient des informations sur l’utilisation de mémoire de statistiques relatives à la tâche qui en cours [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) représente l’instance.</span><span class="sxs-lookup"><span data-stu-id="179dd-103">Gets statistical memory usage information related to the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="179dd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="179dd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMemStats (  
    [out] COR_GC_THREAD_STATS *pMemUsage  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="179dd-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="179dd-105">Parameters</span></span>  
 `pMemUsage`  
 <span data-ttu-id="179dd-106">[out] Un pointeur vers un [COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) instance qui contient des détails sur l’utilisation de la mémoire de la tâche, y compris le nombre d’octets alloués.</span><span class="sxs-lookup"><span data-stu-id="179dd-106">[out] A pointer to a [COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) instance that contains details about the memory usage of the task, including the number of bytes allocated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="179dd-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="179dd-107">Return Value</span></span>  
  
|<span data-ttu-id="179dd-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="179dd-108">HRESULT</span></span>|<span data-ttu-id="179dd-109">Description</span><span class="sxs-lookup"><span data-stu-id="179dd-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="179dd-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="179dd-110">S_OK</span></span>|<span data-ttu-id="179dd-111">`GetMemStats` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="179dd-111">`GetMemStats` returned successfully.</span></span>|  
|<span data-ttu-id="179dd-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="179dd-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="179dd-113">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="179dd-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="179dd-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="179dd-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="179dd-115">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="179dd-115">The call timed out.</span></span>|  
|<span data-ttu-id="179dd-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="179dd-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="179dd-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="179dd-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="179dd-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="179dd-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="179dd-119">Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="179dd-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="179dd-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="179dd-120">E_FAIL</span></span>|<span data-ttu-id="179dd-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="179dd-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="179dd-122">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus.</span><span class="sxs-lookup"><span data-stu-id="179dd-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="179dd-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="179dd-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="179dd-124">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="179dd-124">Requirements</span></span>  
 <span data-ttu-id="179dd-125">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="179dd-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="179dd-126">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="179dd-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="179dd-127">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="179dd-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="179dd-128">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="179dd-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="179dd-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="179dd-129">See also</span></span>

- [<span data-ttu-id="179dd-130">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="179dd-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="179dd-131">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="179dd-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="179dd-132">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="179dd-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="179dd-133">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="179dd-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
