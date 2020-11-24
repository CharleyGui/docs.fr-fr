---
title: ICLRSyncManager::GetMonitorOwner, méthode
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.GetMonitorOwner
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::GetMonitorOwner
helpviewer_keywords:
- ICLRSyncManager::GetMonitorOwner method [.NET Framework hosting]
- GetMonitorOwner method [.NET Framework hosting]
ms.assetid: 840983a4-396d-47b4-86a0-d35f9b437cdb
topic_type:
- apiref
ms.openlocfilehash: a2cb82d8071518af4d4bc3276871f3846a5a5693
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687079"
---
# <a name="iclrsyncmanagergetmonitorowner-method"></a><span data-ttu-id="0f070-102">ICLRSyncManager::GetMonitorOwner, méthode</span><span class="sxs-lookup"><span data-stu-id="0f070-102">ICLRSyncManager::GetMonitorOwner Method</span></span>

<span data-ttu-id="0f070-103">Obtient l’instance [IHostTask](ihosttask-interface.md) qui possède le moniteur identifié par le cookie spécifié.</span><span class="sxs-lookup"><span data-stu-id="0f070-103">Gets the [IHostTask](ihosttask-interface.md) instance that owns the monitor identified by the specified cookie.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f070-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0f070-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMonitorOwner (  
    [in]  SIZE_T     cookie,  
    [out] IHostTask *ppOwnerHostTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f070-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0f070-105">Parameters</span></span>  

 `cookie`  
 <span data-ttu-id="0f070-106">dans Cookie associé à l’analyse.</span><span class="sxs-lookup"><span data-stu-id="0f070-106">[in] The cookie associated with the monitor.</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="0f070-107">à Pointeur vers `IHostTask` qui possède actuellement le moniteur, ou null si aucune tâche n’est propriétaire.</span><span class="sxs-lookup"><span data-stu-id="0f070-107">[out] A pointer to the `IHostTask` that currently owns the monitor, or null if no task has ownership.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0f070-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="0f070-108">Return Value</span></span>  
  
|<span data-ttu-id="0f070-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0f070-109">HRESULT</span></span>|<span data-ttu-id="0f070-110">Description</span><span class="sxs-lookup"><span data-stu-id="0f070-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0f070-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="0f070-111">S_OK</span></span>|<span data-ttu-id="0f070-112">`GetMonitorOwner` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="0f070-112">`GetMonitorOwner` returned successfully.</span></span>|  
|<span data-ttu-id="0f070-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0f070-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0f070-114">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="0f070-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0f070-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0f070-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0f070-116">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="0f070-116">The call timed out.</span></span>|  
|<span data-ttu-id="0f070-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0f070-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0f070-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="0f070-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0f070-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0f070-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0f070-120">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="0f070-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0f070-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0f070-121">E_FAIL</span></span>|<span data-ttu-id="0f070-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="0f070-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0f070-123">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="0f070-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0f070-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0f070-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f070-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="0f070-125">Remarks</span></span>  

 <span data-ttu-id="0f070-126">L’hôte appelle généralement dans le cadre `GetMonitorOwner` d’un mécanisme de détection des verrous mortels.</span><span class="sxs-lookup"><span data-stu-id="0f070-126">The host typically calls `GetMonitorOwner` as part of a deadlock-detection mechanism.</span></span> <span data-ttu-id="0f070-127">Le cookie est associé à une analyse lorsqu’il est créé à l’aide d’un appel à [IHostSyncManager :: CreateMonitorEvent](ihostsyncmanager-createmonitorevent-method.md).</span><span class="sxs-lookup"><span data-stu-id="0f070-127">The cookie is associated with a monitor when it is created by using a call to [IHostSyncManager::CreateMonitorEvent](ihostsyncmanager-createmonitorevent-method.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0f070-128">Un appel pour libérer l’événement sous-jacent du moniteur peut se bloquer, mais n’interbloquera pas, si un appel à cette méthode est actuellement en vigueur sur le cookie associé à cette analyse.</span><span class="sxs-lookup"><span data-stu-id="0f070-128">A call to release the event underlying the monitor might block—but will not deadlock—if a call to this method is currently in effect on the cookie associated with that monitor.</span></span> <span data-ttu-id="0f070-129">D’autres tâches peuvent également se bloquer si elles essaient d’acquérir ce moniteur.</span><span class="sxs-lookup"><span data-stu-id="0f070-129">Other tasks might also block if they attempt to acquire this monitor.</span></span>  
  
 <span data-ttu-id="0f070-130">`GetMonitorOwner` retourne toujours immédiatement et peut être appelé à tout moment après un appel à `CreateMonitorEvent` .</span><span class="sxs-lookup"><span data-stu-id="0f070-130">`GetMonitorOwner` always returns immediately and can be called any time after a call to `CreateMonitorEvent`.</span></span> <span data-ttu-id="0f070-131">L’hôte n’a pas besoin d’attendre qu’une tâche attende l’événement.</span><span class="sxs-lookup"><span data-stu-id="0f070-131">The host does not need to wait until a task is waiting on the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f070-132">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0f070-132">Requirements</span></span>  

 <span data-ttu-id="0f070-133">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f070-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f070-134">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0f070-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0f070-135">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0f070-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0f070-136">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f070-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f070-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0f070-137">See also</span></span>

- [<span data-ttu-id="0f070-138">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="0f070-138">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="0f070-139">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="0f070-139">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
