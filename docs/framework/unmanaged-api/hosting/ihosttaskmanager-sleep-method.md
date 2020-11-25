---
title: IHostTaskManager::Sleep, méthode
ms.date: 03/30/2017
api_name:
- IHostTaskManager.Sleep
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::Sleep
helpviewer_keywords:
- IHostTaskManager::Sleep method [.NET Framework hosting]
- Sleep method, IHostTaskManager interface [.NET Framework hosting]
ms.assetid: f67d25f3-9199-4c5f-b1e8-1c819243cfd5
topic_type:
- apiref
ms.openlocfilehash: 372b15a565f8a7484c1c42c387098a38f7bbf428
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702054"
---
# <a name="ihosttaskmanagersleep-method"></a><span data-ttu-id="59ce6-102">IHostTaskManager::Sleep, méthode</span><span class="sxs-lookup"><span data-stu-id="59ce6-102">IHostTaskManager::Sleep Method</span></span>

<span data-ttu-id="59ce6-103">Indique à l’hôte que la tâche en cours va se mettre en veille.</span><span class="sxs-lookup"><span data-stu-id="59ce6-103">Notifies the host that the current task is going to sleep.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59ce6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59ce6-104">Syntax</span></span>  
  
```cpp  
HRESULT Sleep (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="59ce6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="59ce6-105">Parameters</span></span>  

 `dwMilliseconds`  
 <span data-ttu-id="59ce6-106">dans Intervalle de temps, en millisecondes, pendant lequel le thread est mis en veille.</span><span class="sxs-lookup"><span data-stu-id="59ce6-106">[in] The time interval, in milliseconds, that the thread will sleep.</span></span>  
  
 `option`  
 <span data-ttu-id="59ce6-107">dans L’une des [WAIT_OPTION](wait-option-enumeration.md) valeurs d’énumération, indiquant quelle mesure l’hôte doit prendre si cette action bloque.</span><span class="sxs-lookup"><span data-stu-id="59ce6-107">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) enumeration values, indicating what action the host should take if this action blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="59ce6-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="59ce6-108">Return Value</span></span>  
  
|<span data-ttu-id="59ce6-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="59ce6-109">HRESULT</span></span>|<span data-ttu-id="59ce6-110">Description</span><span class="sxs-lookup"><span data-stu-id="59ce6-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="59ce6-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="59ce6-111">S_OK</span></span>|<span data-ttu-id="59ce6-112">`Sleep` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="59ce6-112">`Sleep` returned successfully.</span></span>|  
|<span data-ttu-id="59ce6-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="59ce6-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="59ce6-114">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="59ce6-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="59ce6-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="59ce6-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="59ce6-116">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="59ce6-116">The call timed out.</span></span>|  
|<span data-ttu-id="59ce6-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="59ce6-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="59ce6-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="59ce6-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="59ce6-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="59ce6-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="59ce6-120">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="59ce6-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="59ce6-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="59ce6-121">E_FAIL</span></span>|<span data-ttu-id="59ce6-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="59ce6-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="59ce6-123">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="59ce6-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="59ce6-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="59ce6-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59ce6-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="59ce6-125">Remarks</span></span>  

 <span data-ttu-id="59ce6-126">Le CLR appelle généralement `IHostTaskManager::Sleep` lorsque <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> est appelé à partir du code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="59ce6-126">The CLR typically calls `IHostTaskManager::Sleep` when <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> is called from user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59ce6-127">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="59ce6-127">Requirements</span></span>  

 <span data-ttu-id="59ce6-128">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59ce6-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59ce6-129">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="59ce6-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="59ce6-130">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="59ce6-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="59ce6-131">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59ce6-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59ce6-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59ce6-132">See also</span></span>

- [<span data-ttu-id="59ce6-133">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="59ce6-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="59ce6-134">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="59ce6-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="59ce6-135">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="59ce6-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="59ce6-136">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="59ce6-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
