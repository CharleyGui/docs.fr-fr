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
ms.openlocfilehash: 3a3c42e2877957e3bbf5031e6ba650e4c9e0364e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195947"
---
# <a name="iclrtasklocksheld-method"></a><span data-ttu-id="fd9dc-102">ICLRTask::LocksHeld, méthode</span><span class="sxs-lookup"><span data-stu-id="fd9dc-102">ICLRTask::LocksHeld Method</span></span>
<span data-ttu-id="fd9dc-103">Obtient le nombre de verrous actuellement détenus sur la tâche.</span><span class="sxs-lookup"><span data-stu-id="fd9dc-103">Gets the number of locks currently held on the task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd9dc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fd9dc-104">Syntax</span></span>  
  
```cpp  
HRESULT LocksHeld (  
    [out] SIZE_T *pLockCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd9dc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fd9dc-105">Parameters</span></span>  
 `pLockCount`  
 <span data-ttu-id="fd9dc-106">à Nombre de verrous maintenus sur la tâche au moment de l’appel de la méthode.</span><span class="sxs-lookup"><span data-stu-id="fd9dc-106">[out] The number of locks held on the task at the time of the method call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fd9dc-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="fd9dc-107">Return Value</span></span>  
  
|<span data-ttu-id="fd9dc-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fd9dc-108">HRESULT</span></span>|<span data-ttu-id="fd9dc-109">Description</span><span class="sxs-lookup"><span data-stu-id="fd9dc-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fd9dc-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="fd9dc-110">S_OK</span></span>|<span data-ttu-id="fd9dc-111">`LocksHeld` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="fd9dc-111">`LocksHeld` returned successfully.</span></span>|  
|<span data-ttu-id="fd9dc-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fd9dc-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fd9dc-113">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="fd9dc-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fd9dc-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fd9dc-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fd9dc-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="fd9dc-115">The call timed out.</span></span>|  
|<span data-ttu-id="fd9dc-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fd9dc-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fd9dc-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="fd9dc-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fd9dc-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fd9dc-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fd9dc-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="fd9dc-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fd9dc-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fd9dc-120">E_FAIL</span></span>|<span data-ttu-id="fd9dc-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="fd9dc-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fd9dc-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="fd9dc-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fd9dc-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fd9dc-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fd9dc-124">spécifications</span><span class="sxs-lookup"><span data-stu-id="fd9dc-124">Requirements</span></span>  
 <span data-ttu-id="fd9dc-125">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd9dc-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd9dc-126">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fd9dc-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fd9dc-127">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="fd9dc-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fd9dc-128">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd9dc-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd9dc-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fd9dc-129">See also</span></span>

- [<span data-ttu-id="fd9dc-130">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="fd9dc-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="fd9dc-131">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="fd9dc-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="fd9dc-132">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="fd9dc-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="fd9dc-133">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="fd9dc-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
