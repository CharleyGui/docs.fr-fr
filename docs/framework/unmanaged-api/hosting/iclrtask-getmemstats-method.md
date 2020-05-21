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
ms.openlocfilehash: 0d2975d6247cd9ecdb07b564d77518151404c7d0
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762455"
---
# <a name="iclrtaskgetmemstats-method"></a><span data-ttu-id="10d47-102">ICLRTask::GetMemStats, méthode</span><span class="sxs-lookup"><span data-stu-id="10d47-102">ICLRTask::GetMemStats Method</span></span>
<span data-ttu-id="10d47-103">Obtient des informations sur l’utilisation de la mémoire statistique relatives à la tâche que l’instance d' [ICLRTask](iclrtask-interface.md) actuelle représente.</span><span class="sxs-lookup"><span data-stu-id="10d47-103">Gets statistical memory usage information related to the task that the current [ICLRTask](iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10d47-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="10d47-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMemStats (  
    [out] COR_GC_THREAD_STATS *pMemUsage  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="10d47-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="10d47-105">Parameters</span></span>  
 `pMemUsage`  
 <span data-ttu-id="10d47-106">à Pointeur vers une instance de [COR_GC_THREAD_STATS](cor-gc-thread-stats-structure.md) qui contient des détails sur l’utilisation de la mémoire de la tâche, y compris le nombre d’octets alloués.</span><span class="sxs-lookup"><span data-stu-id="10d47-106">[out] A pointer to a [COR_GC_THREAD_STATS](cor-gc-thread-stats-structure.md) instance that contains details about the memory usage of the task, including the number of bytes allocated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="10d47-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="10d47-107">Return Value</span></span>  
  
|<span data-ttu-id="10d47-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="10d47-108">HRESULT</span></span>|<span data-ttu-id="10d47-109">Description</span><span class="sxs-lookup"><span data-stu-id="10d47-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="10d47-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="10d47-110">S_OK</span></span>|<span data-ttu-id="10d47-111">`GetMemStats`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="10d47-111">`GetMemStats` returned successfully.</span></span>|  
|<span data-ttu-id="10d47-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="10d47-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="10d47-113">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="10d47-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="10d47-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="10d47-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="10d47-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="10d47-115">The call timed out.</span></span>|  
|<span data-ttu-id="10d47-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="10d47-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="10d47-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="10d47-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="10d47-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="10d47-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="10d47-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="10d47-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="10d47-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="10d47-120">E_FAIL</span></span>|<span data-ttu-id="10d47-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="10d47-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="10d47-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="10d47-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="10d47-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="10d47-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="10d47-124">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="10d47-124">Requirements</span></span>  
 <span data-ttu-id="10d47-125">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10d47-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10d47-126">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="10d47-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="10d47-127">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="10d47-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="10d47-128">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10d47-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10d47-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="10d47-129">See also</span></span>

- [<span data-ttu-id="10d47-130">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="10d47-130">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="10d47-131">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="10d47-131">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="10d47-132">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="10d47-132">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="10d47-133">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="10d47-133">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
