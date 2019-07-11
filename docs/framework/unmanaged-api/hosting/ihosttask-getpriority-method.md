---
title: IHostTask::GetPriority, méthode
ms.date: 03/30/2017
api_name:
- IHostTask.GetPriority
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::GetPriority
helpviewer_keywords:
- GetPriority method [.NET Framework hosting]
- IHostTask::GetPriority method [.NET Framework hosting]
ms.assetid: 4b463cd6-77c1-4f9a-8518-346ad8fc4b70
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b722963290ec9713d4dc991cc4135473da96b42e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764520"
---
# <a name="ihosttaskgetpriority-method"></a><span data-ttu-id="38e09-102">IHostTask::GetPriority, méthode</span><span class="sxs-lookup"><span data-stu-id="38e09-102">IHostTask::GetPriority Method</span></span>
<span data-ttu-id="38e09-103">Obtient le niveau de priorité de thread de la tâche représentée par l’actuel [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span><span class="sxs-lookup"><span data-stu-id="38e09-103">Gets the thread priority level of the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38e09-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38e09-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPriority (  
    [out] int *pPriority  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38e09-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="38e09-105">Parameters</span></span>  
 `pPriority`  
 <span data-ttu-id="38e09-106">[out] Un pointeur vers un entier qui indique le niveau de priorité de thread de la tâche représentée par l’actuel `IHostTask` instance.</span><span class="sxs-lookup"><span data-stu-id="38e09-106">[out] A pointer to an integer that indicates the thread priority level of the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="38e09-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="38e09-107">Return Value</span></span>  
  
|<span data-ttu-id="38e09-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="38e09-108">HRESULT</span></span>|<span data-ttu-id="38e09-109">Description</span><span class="sxs-lookup"><span data-stu-id="38e09-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="38e09-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="38e09-110">S_OK</span></span>|<span data-ttu-id="38e09-111">`GetPriority` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="38e09-111">`GetPriority` returned successfully.</span></span>|  
|<span data-ttu-id="38e09-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="38e09-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="38e09-113">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="38e09-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="38e09-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="38e09-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="38e09-115">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="38e09-115">The call timed out.</span></span>|  
|<span data-ttu-id="38e09-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="38e09-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="38e09-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="38e09-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="38e09-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="38e09-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="38e09-119">Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="38e09-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="38e09-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="38e09-120">E_FAIL</span></span>|<span data-ttu-id="38e09-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="38e09-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="38e09-122">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus.</span><span class="sxs-lookup"><span data-stu-id="38e09-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="38e09-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="38e09-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38e09-124">Notes</span><span class="sxs-lookup"><span data-stu-id="38e09-124">Remarks</span></span>  
 <span data-ttu-id="38e09-125">Les valeurs de niveau de priorité de thread sont définies par Win32 `SetThreadPriority` (fonction).</span><span class="sxs-lookup"><span data-stu-id="38e09-125">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38e09-126">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="38e09-126">Requirements</span></span>  
 <span data-ttu-id="38e09-127">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38e09-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38e09-128">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="38e09-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="38e09-129">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="38e09-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="38e09-130">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38e09-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38e09-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38e09-131">See also</span></span>

- [<span data-ttu-id="38e09-132">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="38e09-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="38e09-133">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="38e09-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="38e09-134">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="38e09-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="38e09-135">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="38e09-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
