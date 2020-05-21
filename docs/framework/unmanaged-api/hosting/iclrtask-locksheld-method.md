---
title: ICLRTask::LocksHeld, méthode
ms.date: 03/30/2017
api_name:
- ICLRTask.LocksHeld
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::LocksHeld
helpviewer_keywords:
- LocksHeld method [.NET Framework hosting]
- ICLRTask::LocksHeld method [.NET Framework hosting]
ms.assetid: e88a4dc3-02cc-4703-a474-292b71c40657
topic_type:
- apiref
ms.openlocfilehash: c67f00acd61d6e0cdf3adfa0d3d0fda2a06a6f31
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762979"
---
# <a name="iclrtasklocksheld-method"></a><span data-ttu-id="07cf3-102">ICLRTask::LocksHeld, méthode</span><span class="sxs-lookup"><span data-stu-id="07cf3-102">ICLRTask::LocksHeld Method</span></span>
<span data-ttu-id="07cf3-103">Obtient le nombre de verrous actuellement détenus sur la tâche.</span><span class="sxs-lookup"><span data-stu-id="07cf3-103">Gets the number of locks currently held on the task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07cf3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="07cf3-104">Syntax</span></span>  
  
```cpp  
HRESULT LocksHeld (  
    [out] SIZE_T *pLockCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07cf3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="07cf3-105">Parameters</span></span>  
 `pLockCount`  
 <span data-ttu-id="07cf3-106">à Nombre de verrous maintenus sur la tâche au moment de l’appel de la méthode.</span><span class="sxs-lookup"><span data-stu-id="07cf3-106">[out] The number of locks held on the task at the time of the method call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="07cf3-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="07cf3-107">Return Value</span></span>  
  
|<span data-ttu-id="07cf3-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="07cf3-108">HRESULT</span></span>|<span data-ttu-id="07cf3-109">Description</span><span class="sxs-lookup"><span data-stu-id="07cf3-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="07cf3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="07cf3-110">S_OK</span></span>|<span data-ttu-id="07cf3-111">`LocksHeld`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="07cf3-111">`LocksHeld` returned successfully.</span></span>|  
|<span data-ttu-id="07cf3-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="07cf3-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="07cf3-113">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="07cf3-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="07cf3-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="07cf3-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="07cf3-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="07cf3-115">The call timed out.</span></span>|  
|<span data-ttu-id="07cf3-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="07cf3-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="07cf3-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="07cf3-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="07cf3-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="07cf3-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="07cf3-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="07cf3-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="07cf3-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="07cf3-120">E_FAIL</span></span>|<span data-ttu-id="07cf3-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="07cf3-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="07cf3-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="07cf3-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="07cf3-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="07cf3-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="07cf3-124">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="07cf3-124">Requirements</span></span>  
 <span data-ttu-id="07cf3-125">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07cf3-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07cf3-126">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="07cf3-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="07cf3-127">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="07cf3-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="07cf3-128">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07cf3-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07cf3-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="07cf3-129">See also</span></span>

- [<span data-ttu-id="07cf3-130">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="07cf3-130">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="07cf3-131">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="07cf3-131">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="07cf3-132">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="07cf3-132">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="07cf3-133">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="07cf3-133">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
