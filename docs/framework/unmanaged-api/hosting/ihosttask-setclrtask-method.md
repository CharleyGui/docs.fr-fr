---
title: IHostTask::SetCLRTask, méthode
ms.date: 03/30/2017
api_name:
- IHostTask.SetCLRTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::SetCLRTask
helpviewer_keywords:
- SetCLRTask method [.NET Framework hosting]
- IHostTask::SetCLRTask method [.NET Framework hosting]
ms.assetid: e9d39c80-41a1-49e7-bb5e-ea3433bfb5d7
topic_type:
- apiref
ms.openlocfilehash: e6b9a4015a6139d6c8d7101fa7811c7ad9134e4c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720462"
---
# <a name="ihosttasksetclrtask-method"></a><span data-ttu-id="d0669-102">IHostTask::SetCLRTask, méthode</span><span class="sxs-lookup"><span data-stu-id="d0669-102">IHostTask::SetCLRTask Method</span></span>

<span data-ttu-id="d0669-103">Associe une `ICLRTask` instance à l’instance de l’objet [IHostTask](ihosttask-interface.md) en cours.</span><span class="sxs-lookup"><span data-stu-id="d0669-103">Associates an `ICLRTask` instance with the current [IHostTask](ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0669-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d0669-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRTask (  
    [in] ICLRTask *pCLRTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0669-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d0669-105">Parameters</span></span>  

 `pCLRTask`  
 <span data-ttu-id="d0669-106">dans Pointeur d’interface vers l' `ICLRTask` instance à associer à l’instance actuelle `IHostTask` .</span><span class="sxs-lookup"><span data-stu-id="d0669-106">[in] An interface pointer to the `ICLRTask` instance to be associated with the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d0669-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="d0669-107">Return Value</span></span>  
  
|<span data-ttu-id="d0669-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d0669-108">HRESULT</span></span>|<span data-ttu-id="d0669-109">Description</span><span class="sxs-lookup"><span data-stu-id="d0669-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d0669-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d0669-110">S_OK</span></span>|<span data-ttu-id="d0669-111">`SetCLRTask` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="d0669-111">`SetCLRTask` returned successfully.</span></span>|  
|<span data-ttu-id="d0669-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d0669-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d0669-113">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="d0669-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d0669-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d0669-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d0669-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="d0669-115">The call timed out.</span></span>|  
|<span data-ttu-id="d0669-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d0669-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d0669-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="d0669-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d0669-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d0669-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d0669-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="d0669-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d0669-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d0669-120">E_FAIL</span></span>|<span data-ttu-id="d0669-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="d0669-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d0669-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="d0669-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d0669-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d0669-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0669-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="d0669-124">Remarks</span></span>  

 <span data-ttu-id="d0669-125">Le CLR appelle `SetCLRTask` pour associer une `ICLRTask` instance à l' `IHostTask` instance actuelle, qui a été créée par un appel à [IHostTaskManager :: CreateTask](ihosttaskmanager-createtask-method.md).</span><span class="sxs-lookup"><span data-stu-id="d0669-125">The CLR calls `SetCLRTask` to associate an `ICLRTask` instance with the current `IHostTask` instance, which was created by a call to [IHostTaskManager::CreateTask](ihosttaskmanager-createtask-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0669-126">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d0669-126">Requirements</span></span>  

 <span data-ttu-id="d0669-127">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0669-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0669-128">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d0669-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d0669-129">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d0669-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d0669-130">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0669-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0669-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d0669-131">See also</span></span>

- [<span data-ttu-id="d0669-132">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="d0669-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="d0669-133">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="d0669-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="d0669-134">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="d0669-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="d0669-135">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="d0669-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
