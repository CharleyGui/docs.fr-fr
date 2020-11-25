---
title: ICLRTask::SwitchOut, méthode
ms.date: 03/30/2017
api_name:
- ICLRTask.SwitchOut
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::SwitchOut
helpviewer_keywords:
- ICLRTask::SwitchOut method [.NET Framework hosting]
- SwitchOut method [.NET Framework hosting]
ms.assetid: b6fb168c-b24b-4ecf-a390-2b5ba3317ae6
topic_type:
- apiref
ms.openlocfilehash: 1b27983b3f10eba225442dcd2f5df02062e53ed4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720267"
---
# <a name="iclrtaskswitchout-method"></a><span data-ttu-id="c6f1a-102">ICLRTask::SwitchOut, méthode</span><span class="sxs-lookup"><span data-stu-id="c6f1a-102">ICLRTask::SwitchOut Method</span></span>

<span data-ttu-id="c6f1a-103">Avertit le common language runtime (CLR) que la tâche représentée par l’instance d' [ICLRTask](iclrtask-interface.md) actuelle n’est plus dans un état opérationnel.</span><span class="sxs-lookup"><span data-stu-id="c6f1a-103">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](iclrtask-interface.md) instance is no longer in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6f1a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c6f1a-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchOut ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="c6f1a-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c6f1a-105">Return Value</span></span>  
  
|<span data-ttu-id="c6f1a-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c6f1a-106">HRESULT</span></span>|<span data-ttu-id="c6f1a-107">Description</span><span class="sxs-lookup"><span data-stu-id="c6f1a-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c6f1a-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="c6f1a-108">S_OK</span></span>|<span data-ttu-id="c6f1a-109">`SwitchOut` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="c6f1a-109">`SwitchOut` returned successfully.</span></span>|  
|<span data-ttu-id="c6f1a-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c6f1a-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c6f1a-111">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="c6f1a-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c6f1a-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c6f1a-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c6f1a-113">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="c6f1a-113">The call timed out.</span></span>|  
|<span data-ttu-id="c6f1a-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c6f1a-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c6f1a-115">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="c6f1a-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c6f1a-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c6f1a-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c6f1a-117">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="c6f1a-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c6f1a-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c6f1a-118">E_FAIL</span></span>|<span data-ttu-id="c6f1a-119">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="c6f1a-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c6f1a-120">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="c6f1a-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c6f1a-121">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c6f1a-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6f1a-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="c6f1a-122">Remarks</span></span>  

 <span data-ttu-id="c6f1a-123">Un hôte appelle `SwitchOut` pour informer le CLR qu’il a temporairement cessé d’exécuter la tâche que l' `ICLRTask` instance actuelle représente, et replanifie la tâche.</span><span class="sxs-lookup"><span data-stu-id="c6f1a-123">A host calls `SwitchOut` to inform the CLR that it has temporarily stopped executing the task that the current `ICLRTask` instance represents, and will reschedule the task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6f1a-124">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c6f1a-124">Requirements</span></span>  

 <span data-ttu-id="c6f1a-125">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6f1a-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6f1a-126">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c6f1a-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c6f1a-127">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c6f1a-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c6f1a-128">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6f1a-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6f1a-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c6f1a-129">See also</span></span>

- [<span data-ttu-id="c6f1a-130">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="c6f1a-130">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="c6f1a-131">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="c6f1a-131">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="c6f1a-132">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="c6f1a-132">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="c6f1a-133">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="c6f1a-133">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
