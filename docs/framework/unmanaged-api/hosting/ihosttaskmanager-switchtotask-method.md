---
title: IHostTaskManager::SwitchToTask, méthode
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SwitchToTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SwitchToTask
helpviewer_keywords:
- IHostTaskManager::SwitchToTask method [.NET Framework hosting]
- SwitchToTask method [.NET Framework hosting]
ms.assetid: 35d0c27e-4b14-49ce-810d-7ab2120177e8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4af3d73a4c45654d1d40ef2fbf44a0e2b3e1bf32
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913711"
---
# <a name="ihosttaskmanagerswitchtotask-method"></a><span data-ttu-id="a05a5-102">IHostTaskManager::SwitchToTask, méthode</span><span class="sxs-lookup"><span data-stu-id="a05a5-102">IHostTaskManager::SwitchToTask Method</span></span>
<span data-ttu-id="a05a5-103">Indique à l’hôte qu’il doit extraire la tâche actuelle.</span><span class="sxs-lookup"><span data-stu-id="a05a5-103">Notifies the host that it should switch out the current task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a05a5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a05a5-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchToTask (  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a05a5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a05a5-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="a05a5-106">dans L’une des valeurs d’énumération [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) , indiquant l’action que l’hôte doit effectuer si l’opération demandée est bloquée.</span><span class="sxs-lookup"><span data-stu-id="a05a5-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) enumeration values, indicating the action the host should take if the requested operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a05a5-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="a05a5-107">Return Value</span></span>  
  
|<span data-ttu-id="a05a5-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a05a5-108">HRESULT</span></span>|<span data-ttu-id="a05a5-109">Description</span><span class="sxs-lookup"><span data-stu-id="a05a5-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a05a5-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a05a5-110">S_OK</span></span>|<span data-ttu-id="a05a5-111">`SwitchToTask`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="a05a5-111">`SwitchToTask` returned successfully.</span></span>|  
|<span data-ttu-id="a05a5-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a05a5-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a05a5-113">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="a05a5-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a05a5-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a05a5-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a05a5-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="a05a5-115">The call timed out.</span></span>|  
|<span data-ttu-id="a05a5-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a05a5-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a05a5-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="a05a5-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a05a5-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a05a5-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a05a5-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="a05a5-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a05a5-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a05a5-120">E_FAIL</span></span>|<span data-ttu-id="a05a5-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="a05a5-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a05a5-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="a05a5-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a05a5-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a05a5-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a05a5-124">Notes</span><span class="sxs-lookup"><span data-stu-id="a05a5-124">Remarks</span></span>  
 <span data-ttu-id="a05a5-125">L’hôte peut basculer vers une autre tâche comme souhaité ou nécessaire.</span><span class="sxs-lookup"><span data-stu-id="a05a5-125">The host can switch in another task as desired or needed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a05a5-126">`SwitchToTask`ne spécifie pas la tâche vers laquelle l’hôte doit basculer; Il spécifie uniquement la tâche à partir de laquelle il doit basculer.</span><span class="sxs-lookup"><span data-stu-id="a05a5-126">`SwitchToTask` does not specify which task the host should switch to; it specifies only the task that it should switch from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a05a5-127">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a05a5-127">Requirements</span></span>  
 <span data-ttu-id="a05a5-128">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a05a5-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a05a5-129">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a05a5-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a05a5-130">**Bibliothèque** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a05a5-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a05a5-131">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a05a5-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a05a5-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a05a5-132">See also</span></span>

- [<span data-ttu-id="a05a5-133">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="a05a5-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="a05a5-134">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="a05a5-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="a05a5-135">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="a05a5-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="a05a5-136">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="a05a5-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
