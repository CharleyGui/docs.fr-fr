---
title: IHostTaskManager::LeaveRuntime, méthode
ms.date: 03/30/2017
api_name:
- IHostTaskManager.LeaveRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::LeaveRuntime
helpviewer_keywords:
- IHostTaskManager::LeaveRuntime method [.NET Framework hosting]
- LeaveRuntime method [.NET Framework hosting]
ms.assetid: 43689cc4-e48e-46e5-a22d-bafd768b8759
topic_type:
- apiref
ms.openlocfilehash: 855f8a5d3582bbad59301a344d8a51198c40a051
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673044"
---
# <a name="ihosttaskmanagerleaveruntime-method"></a><span data-ttu-id="eeccf-102">IHostTaskManager::LeaveRuntime, méthode</span><span class="sxs-lookup"><span data-stu-id="eeccf-102">IHostTaskManager::LeaveRuntime Method</span></span>

<span data-ttu-id="eeccf-103">Indique à l’hôte que la tâche en cours d’exécution est sur le point de sortir du common language runtime (CLR) et d’entrer du code non managé.</span><span class="sxs-lookup"><span data-stu-id="eeccf-103">Notifies the host that the currently executing task is about to leave the common language runtime (CLR) and enter unmanaged code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="eeccf-104">Un appel correspondant à [IHostTaskManager :: EnterRuntime](ihosttaskmanager-enterruntime-method.md) avertit l’hôte que la tâche en cours d’exécution est en cours d’entrée dans le code managé.</span><span class="sxs-lookup"><span data-stu-id="eeccf-104">A corresponding call to [IHostTaskManager::EnterRuntime](ihosttaskmanager-enterruntime-method.md) notifies the host that the currently executing task is reentering managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eeccf-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eeccf-105">Syntax</span></span>  
  
```cpp  
HRESULT LeaveRuntime (  
    [in] SIZE_T target  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eeccf-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="eeccf-106">Parameters</span></span>  

 `target`  
 <span data-ttu-id="eeccf-107">dans Adresse dans le fichier exécutable portable mappé de la fonction non managée à appeler.</span><span class="sxs-lookup"><span data-stu-id="eeccf-107">[in] The address within the mapped portable executable file of the unmanaged function to be called.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eeccf-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="eeccf-108">Return Value</span></span>  
  
|<span data-ttu-id="eeccf-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="eeccf-109">HRESULT</span></span>|<span data-ttu-id="eeccf-110">Description</span><span class="sxs-lookup"><span data-stu-id="eeccf-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="eeccf-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="eeccf-111">S_OK</span></span>|<span data-ttu-id="eeccf-112">`LeaveRuntime` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="eeccf-112">`LeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="eeccf-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="eeccf-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="eeccf-114">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="eeccf-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="eeccf-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="eeccf-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="eeccf-116">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="eeccf-116">The call timed out.</span></span>|  
|<span data-ttu-id="eeccf-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="eeccf-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="eeccf-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="eeccf-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="eeccf-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="eeccf-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="eeccf-120">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="eeccf-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="eeccf-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="eeccf-121">E_FAIL</span></span>|<span data-ttu-id="eeccf-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="eeccf-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="eeccf-123">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="eeccf-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="eeccf-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="eeccf-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="eeccf-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="eeccf-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="eeccf-126">La mémoire disponible est insuffisante pour terminer l’allocation demandée.</span><span class="sxs-lookup"><span data-stu-id="eeccf-126">Not enough memory is available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eeccf-127">Remarques</span><span class="sxs-lookup"><span data-stu-id="eeccf-127">Remarks</span></span>  

 <span data-ttu-id="eeccf-128">Les séquences d’appel vers et depuis du code non managé peuvent être imbriquées.</span><span class="sxs-lookup"><span data-stu-id="eeccf-128">Call sequences to and from unmanaged code can be nested.</span></span> <span data-ttu-id="eeccf-129">Par exemple, la liste ci-dessous décrit une situation hypothétique dans laquelle la séquence d’appels à `LeaveRuntime` , [IHostTaskManager :: ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md), [IHostTaskManager :: ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md), et `IHostTaskManager::EnterRuntime` permet à l’hôte d’identifier les couches imbriquées.</span><span class="sxs-lookup"><span data-stu-id="eeccf-129">For example, the list below describes a hypothetical situation in which the sequence of calls to `LeaveRuntime`, [IHostTaskManager::ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md), [IHostTaskManager::ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md), and `IHostTaskManager::EnterRuntime` allows the host to identify the nested layers.</span></span>  
  
|<span data-ttu-id="eeccf-130">Action</span><span class="sxs-lookup"><span data-stu-id="eeccf-130">Action</span></span>|<span data-ttu-id="eeccf-131">Appel de méthode correspondant</span><span class="sxs-lookup"><span data-stu-id="eeccf-131">Corresponding Method Call</span></span>|  
|------------|-------------------------------|  
|<span data-ttu-id="eeccf-132">Un exécutable Visual Basic managé appelle une fonction non managée écrite en C à l’aide de l’appel de code non managé.</span><span class="sxs-lookup"><span data-stu-id="eeccf-132">A managed Visual Basic executable calls an unmanaged function written in C by using platform invoke.</span></span>|`IHostTaskManager::LeaveRuntime`|  
|<span data-ttu-id="eeccf-133">La fonction C non managée appelle une méthode dans une DLL managée écrite en C#.</span><span class="sxs-lookup"><span data-stu-id="eeccf-133">The unmanaged C function calls a method in a managed DLL written in C#.</span></span>|`IHostTaskManager::ReverseEnterRuntime`|  
|<span data-ttu-id="eeccf-134">La fonction C# managée appelle une autre fonction non managée écrite en C, en utilisant également l’appel de code non managé.</span><span class="sxs-lookup"><span data-stu-id="eeccf-134">The managed C# function calls another unmanaged function written in C, also using platform invoke.</span></span>|`IHostTaskManager::LeaveRuntime`|  
|<span data-ttu-id="eeccf-135">La deuxième fonction non managée retourne l’exécution à la fonction C#.</span><span class="sxs-lookup"><span data-stu-id="eeccf-135">The second unmanaged function returns execution to the C# function.</span></span>|`IHostTaskManager::EnterRuntime`|  
|<span data-ttu-id="eeccf-136">La fonction C# retourne l’exécution à la première fonction non managée.</span><span class="sxs-lookup"><span data-stu-id="eeccf-136">The C# function returns execution to the first unmanaged function.</span></span>|`IHostTaskManager::ReverseLeaveRuntime`|  
|<span data-ttu-id="eeccf-137">La première fonction non managée retourne l’exécution au programme Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="eeccf-137">The first unmanaged function returns execution to the Visual Basic program.</span></span>|`IHostTaskManager::EnterRuntime`|  
  
## <a name="requirements"></a><span data-ttu-id="eeccf-138">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="eeccf-138">Requirements</span></span>  

 <span data-ttu-id="eeccf-139">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eeccf-139">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eeccf-140">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="eeccf-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="eeccf-141">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="eeccf-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eeccf-142">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eeccf-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eeccf-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eeccf-143">See also</span></span>

- [<span data-ttu-id="eeccf-144">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="eeccf-144">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="eeccf-145">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="eeccf-145">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="eeccf-146">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="eeccf-146">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="eeccf-147">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="eeccf-147">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
