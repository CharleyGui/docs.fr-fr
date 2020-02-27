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
ms.openlocfilehash: 94ad0073678e88e15d4b083793dca1423130f7e9
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628070"
---
# <a name="ihosttaskmanagerenterruntime-method"></a><span data-ttu-id="18b2b-102">IHostTaskManager::EnterRuntime, méthode</span><span class="sxs-lookup"><span data-stu-id="18b2b-102">IHostTaskManager::EnterRuntime Method</span></span>
<span data-ttu-id="18b2b-103">Avertit l’hôte qu’un appel à une méthode non managée, tel qu’une méthode d’appel de code non managé, retourne le contrôle d’exécution au common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="18b2b-103">Notifies the host that a call to an unmanaged method, such as a platform invoke method, is returning execution control to the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18b2b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="18b2b-104">Syntax</span></span>  
  
```cpp  
HRESULT EnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="18b2b-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="18b2b-105">Return Value</span></span>  
  
|<span data-ttu-id="18b2b-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="18b2b-106">HRESULT</span></span>|<span data-ttu-id="18b2b-107">Description</span><span class="sxs-lookup"><span data-stu-id="18b2b-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="18b2b-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="18b2b-108">S_OK</span></span>|<span data-ttu-id="18b2b-109">`EnterRuntime` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="18b2b-109">`EnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="18b2b-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="18b2b-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="18b2b-111">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="18b2b-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="18b2b-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="18b2b-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="18b2b-113">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="18b2b-113">The call timed out.</span></span>|  
|<span data-ttu-id="18b2b-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="18b2b-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="18b2b-115">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="18b2b-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="18b2b-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="18b2b-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="18b2b-117">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="18b2b-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="18b2b-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="18b2b-118">E_FAIL</span></span>|<span data-ttu-id="18b2b-119">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="18b2b-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="18b2b-120">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="18b2b-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="18b2b-121">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="18b2b-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="18b2b-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="18b2b-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="18b2b-123">Mémoire disponible insuffisante pour terminer l’allocation demandée.</span><span class="sxs-lookup"><span data-stu-id="18b2b-123">Not enough memory was available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18b2b-124">Notes</span><span class="sxs-lookup"><span data-stu-id="18b2b-124">Remarks</span></span>  
 <span data-ttu-id="18b2b-125">`EnterRuntime` est appelée pour notifier l’hôte qu’une fonction non managée, pour laquelle un appel antérieur à la méthode [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md) a été effectuée, a fini de s’exécuter, et retourne le contrôle d’exécution au Runtime.</span><span class="sxs-lookup"><span data-stu-id="18b2b-125">`EnterRuntime` is called to notify the host that an unmanaged function, for which an earlier call to the [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md) method was made, has finished executing, and is returning execution control to the runtime.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="18b2b-126">[ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md) est appelé pour notifier l’hôte qu’une fonction non managée, pour laquelle un appel antérieur à `LeaveRuntime` a été effectué, effectue un appel dans du code managé.</span><span class="sxs-lookup"><span data-stu-id="18b2b-126">[ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md) is called to notify the host that an unmanaged function, for which an earlier call to `LeaveRuntime` was made, is making a call into managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18b2b-127">Spécifications</span><span class="sxs-lookup"><span data-stu-id="18b2b-127">Requirements</span></span>  
 <span data-ttu-id="18b2b-128">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18b2b-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18b2b-129">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="18b2b-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="18b2b-130">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="18b2b-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="18b2b-131">**Versions de .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18b2b-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18b2b-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="18b2b-132">See also</span></span>

- <span data-ttu-id="18b2b-133">[Interopérabilité COM avancée](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="18b2b-133">[Advanced COM Interoperability](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span></span>
- [<span data-ttu-id="18b2b-134">Guide pratique pour appeler des DLL natives à partir du code managé à l’aide de PInvoke</span><span class="sxs-lookup"><span data-stu-id="18b2b-134">How to: Call Native DLLs from Managed Code Using PInvoke</span></span>](/cpp/dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke)
- [<span data-ttu-id="18b2b-135">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="18b2b-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="18b2b-136">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="18b2b-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="18b2b-137">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="18b2b-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="18b2b-138">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="18b2b-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="18b2b-139">LeaveRuntime, méthode</span><span class="sxs-lookup"><span data-stu-id="18b2b-139">LeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)
