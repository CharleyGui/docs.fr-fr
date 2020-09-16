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
ms.openlocfilehash: 1591a055200618f3e4951b5f6cf860dd3e71b44b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554356"
---
# <a name="ihosttaskmanagerenterruntime-method"></a><span data-ttu-id="32255-102">IHostTaskManager::EnterRuntime, méthode</span><span class="sxs-lookup"><span data-stu-id="32255-102">IHostTaskManager::EnterRuntime Method</span></span>
<span data-ttu-id="32255-103">Avertit l’hôte qu’un appel à une méthode non managée, tel qu’une méthode d’appel de code non managé, retourne le contrôle d’exécution au common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="32255-103">Notifies the host that a call to an unmanaged method, such as a platform invoke method, is returning execution control to the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32255-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="32255-104">Syntax</span></span>  
  
```cpp  
HRESULT EnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="32255-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="32255-105">Return Value</span></span>  
  
|<span data-ttu-id="32255-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="32255-106">HRESULT</span></span>|<span data-ttu-id="32255-107">Description</span><span class="sxs-lookup"><span data-stu-id="32255-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="32255-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="32255-108">S_OK</span></span>|<span data-ttu-id="32255-109">`EnterRuntime` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="32255-109">`EnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="32255-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="32255-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="32255-111">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="32255-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="32255-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="32255-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="32255-113">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="32255-113">The call timed out.</span></span>|  
|<span data-ttu-id="32255-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="32255-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="32255-115">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="32255-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="32255-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="32255-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="32255-117">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="32255-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="32255-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="32255-118">E_FAIL</span></span>|<span data-ttu-id="32255-119">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="32255-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="32255-120">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="32255-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="32255-121">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="32255-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="32255-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="32255-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="32255-123">Mémoire disponible insuffisante pour terminer l’allocation demandée.</span><span class="sxs-lookup"><span data-stu-id="32255-123">Not enough memory was available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="32255-124">Notes</span><span class="sxs-lookup"><span data-stu-id="32255-124">Remarks</span></span>  
 <span data-ttu-id="32255-125">`EnterRuntime` est appelé pour notifier l’hôte qu’une fonction non managée, pour laquelle un appel antérieur à la méthode [LeaveRuntime](ihosttaskmanager-leaveruntime-method.md) a été effectuée, a fini de s’exécuter, et retourne le contrôle d’exécution au Runtime.</span><span class="sxs-lookup"><span data-stu-id="32255-125">`EnterRuntime` is called to notify the host that an unmanaged function, for which an earlier call to the [LeaveRuntime](ihosttaskmanager-leaveruntime-method.md) method was made, has finished executing, and is returning execution control to the runtime.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="32255-126">[ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md) est appelé pour notifier l’hôte qu’une fonction non managée, pour laquelle un appel antérieur à `LeaveRuntime` a été effectué, effectue un appel dans du code managé.</span><span class="sxs-lookup"><span data-stu-id="32255-126">[ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md) is called to notify the host that an unmanaged function, for which an earlier call to `LeaveRuntime` was made, is making a call into managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32255-127">Spécifications</span><span class="sxs-lookup"><span data-stu-id="32255-127">Requirements</span></span>  
 <span data-ttu-id="32255-128">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32255-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32255-129">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="32255-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="32255-130">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="32255-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="32255-131">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32255-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32255-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="32255-132">See also</span></span>

- <span data-ttu-id="32255-133">[Interopérabilité COM avancée](/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="32255-133">[Advanced COM Interoperability](/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span></span>
- [<span data-ttu-id="32255-134">Comment : appeler des DLL natives à partir de code managé à l’aide de PInvoke</span><span class="sxs-lookup"><span data-stu-id="32255-134">How to: Call Native DLLs from Managed Code Using PInvoke</span></span>](/cpp/dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke)
- [<span data-ttu-id="32255-135">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="32255-135">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="32255-136">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="32255-136">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="32255-137">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="32255-137">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="32255-138">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="32255-138">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="32255-139">LeaveRuntime, méthode</span><span class="sxs-lookup"><span data-stu-id="32255-139">LeaveRuntime Method</span></span>](ihosttaskmanager-leaveruntime-method.md)
