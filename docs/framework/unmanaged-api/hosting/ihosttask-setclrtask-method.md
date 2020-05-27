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
ms.openlocfilehash: b6eac134a4ffb1813cdc6957632ce5fb9b1a5fff
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842268"
---
# <a name="ihosttasksetclrtask-method"></a><span data-ttu-id="eabad-102">IHostTask::SetCLRTask, méthode</span><span class="sxs-lookup"><span data-stu-id="eabad-102">IHostTask::SetCLRTask Method</span></span>
<span data-ttu-id="eabad-103">Associe une `ICLRTask` instance à l’instance de l’objet [IHostTask](ihosttask-interface.md) en cours.</span><span class="sxs-lookup"><span data-stu-id="eabad-103">Associates an `ICLRTask` instance with the current [IHostTask](ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eabad-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eabad-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRTask (  
    [in] ICLRTask *pCLRTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eabad-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="eabad-105">Parameters</span></span>  
 `pCLRTask`  
 <span data-ttu-id="eabad-106">dans Pointeur d’interface vers l' `ICLRTask` instance à associer à l’instance actuelle `IHostTask` .</span><span class="sxs-lookup"><span data-stu-id="eabad-106">[in] An interface pointer to the `ICLRTask` instance to be associated with the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eabad-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="eabad-107">Return Value</span></span>  
  
|<span data-ttu-id="eabad-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="eabad-108">HRESULT</span></span>|<span data-ttu-id="eabad-109">Description</span><span class="sxs-lookup"><span data-stu-id="eabad-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="eabad-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="eabad-110">S_OK</span></span>|<span data-ttu-id="eabad-111">`SetCLRTask`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="eabad-111">`SetCLRTask` returned successfully.</span></span>|  
|<span data-ttu-id="eabad-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="eabad-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="eabad-113">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="eabad-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="eabad-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="eabad-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="eabad-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="eabad-115">The call timed out.</span></span>|  
|<span data-ttu-id="eabad-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="eabad-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="eabad-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="eabad-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="eabad-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="eabad-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="eabad-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="eabad-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="eabad-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="eabad-120">E_FAIL</span></span>|<span data-ttu-id="eabad-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="eabad-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="eabad-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="eabad-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="eabad-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="eabad-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eabad-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="eabad-124">Remarks</span></span>  
 <span data-ttu-id="eabad-125">Le CLR appelle `SetCLRTask` pour associer une `ICLRTask` instance à l' `IHostTask` instance actuelle, qui a été créée par un appel à [IHostTaskManager :: CreateTask](ihosttaskmanager-createtask-method.md).</span><span class="sxs-lookup"><span data-stu-id="eabad-125">The CLR calls `SetCLRTask` to associate an `ICLRTask` instance with the current `IHostTask` instance, which was created by a call to [IHostTaskManager::CreateTask](ihosttaskmanager-createtask-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eabad-126">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="eabad-126">Requirements</span></span>  
 <span data-ttu-id="eabad-127">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eabad-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eabad-128">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="eabad-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="eabad-129">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="eabad-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eabad-130">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eabad-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eabad-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eabad-131">See also</span></span>

- [<span data-ttu-id="eabad-132">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="eabad-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="eabad-133">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="eabad-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="eabad-134">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="eabad-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="eabad-135">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="eabad-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
