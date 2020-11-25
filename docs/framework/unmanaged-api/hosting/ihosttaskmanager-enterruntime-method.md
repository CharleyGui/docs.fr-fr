---
title: IHostTaskManager::EnterRuntime, méthode
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EnterRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EnterRuntime
helpviewer_keywords:
- IHostTaskManager::EnterRuntime method [.NET Framework hosting]
- EnterRuntime method [.NET Framework hosting]
ms.assetid: 1aa7a4b1-636a-4f5e-b834-b406d72f7120
topic_type:
- apiref
ms.openlocfilehash: 11515bbb5717222a0030c1953b4eab4eb1b83bb2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731642"
---
# <a name="ihosttaskmanagerenterruntime-method"></a><span data-ttu-id="f5790-102">IHostTaskManager::EnterRuntime, méthode</span><span class="sxs-lookup"><span data-stu-id="f5790-102">IHostTaskManager::EnterRuntime Method</span></span>

<span data-ttu-id="f5790-103">Avertit l’hôte qu’un appel à une méthode non managée, tel qu’une méthode d’appel de code non managé, retourne le contrôle d’exécution au common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="f5790-103">Notifies the host that a call to an unmanaged method, such as a platform invoke method, is returning execution control to the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5790-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f5790-104">Syntax</span></span>  
  
```cpp  
HRESULT EnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="f5790-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f5790-105">Return Value</span></span>  
  
|<span data-ttu-id="f5790-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f5790-106">HRESULT</span></span>|<span data-ttu-id="f5790-107">Description</span><span class="sxs-lookup"><span data-stu-id="f5790-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f5790-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="f5790-108">S_OK</span></span>|<span data-ttu-id="f5790-109">`EnterRuntime` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="f5790-109">`EnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="f5790-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f5790-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f5790-111">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="f5790-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f5790-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f5790-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f5790-113">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="f5790-113">The call timed out.</span></span>|  
|<span data-ttu-id="f5790-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f5790-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f5790-115">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="f5790-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f5790-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f5790-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f5790-117">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="f5790-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f5790-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f5790-118">E_FAIL</span></span>|<span data-ttu-id="f5790-119">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="f5790-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f5790-120">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="f5790-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f5790-121">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f5790-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f5790-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="f5790-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="f5790-123">Mémoire disponible insuffisante pour terminer l’allocation demandée.</span><span class="sxs-lookup"><span data-stu-id="f5790-123">Not enough memory was available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5790-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="f5790-124">Remarks</span></span>  

 <span data-ttu-id="f5790-125">`EnterRuntime` est appelé pour notifier l’hôte qu’une fonction non managée, pour laquelle un appel antérieur à la méthode [LeaveRuntime](ihosttaskmanager-leaveruntime-method.md) a été effectuée, a fini de s’exécuter, et retourne le contrôle d’exécution au Runtime.</span><span class="sxs-lookup"><span data-stu-id="f5790-125">`EnterRuntime` is called to notify the host that an unmanaged function, for which an earlier call to the [LeaveRuntime](ihosttaskmanager-leaveruntime-method.md) method was made, has finished executing, and is returning execution control to the runtime.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f5790-126">[ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md) est appelé pour notifier l’hôte qu’une fonction non managée, pour laquelle un appel antérieur à `LeaveRuntime` a été effectué, effectue un appel dans du code managé.</span><span class="sxs-lookup"><span data-stu-id="f5790-126">[ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md) is called to notify the host that an unmanaged function, for which an earlier call to `LeaveRuntime` was made, is making a call into managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5790-127">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f5790-127">Requirements</span></span>  

 <span data-ttu-id="f5790-128">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5790-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5790-129">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f5790-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f5790-130">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f5790-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f5790-131">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5790-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5790-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f5790-132">See also</span></span>

- <span data-ttu-id="f5790-133">[Interopérabilité COM avancée](/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f5790-133">[Advanced COM Interoperability](/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span></span>
- [<span data-ttu-id="f5790-134">Comment : appeler des DLL natives à partir de code managé à l’aide de PInvoke</span><span class="sxs-lookup"><span data-stu-id="f5790-134">How to: Call Native DLLs from Managed Code Using PInvoke</span></span>](/cpp/dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke)
- [<span data-ttu-id="f5790-135">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="f5790-135">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="f5790-136">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="f5790-136">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="f5790-137">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="f5790-137">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="f5790-138">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="f5790-138">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="f5790-139">LeaveRuntime, méthode</span><span class="sxs-lookup"><span data-stu-id="f5790-139">LeaveRuntime Method</span></span>](ihosttaskmanager-leaveruntime-method.md)
