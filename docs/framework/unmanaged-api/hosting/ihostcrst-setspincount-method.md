---
title: IHostCrst::SetSpinCount, méthode
ms.date: 03/30/2017
api_name:
- IHostCrst.SetSpinCount
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::SetSpinCount
helpviewer_keywords:
- IHostCrst::SetSpinCount method [.NET Framework hosting]
- SetSpinCount method [.NET Framework hosting]
ms.assetid: 863fc8ce-9b8a-477e-8dd8-75c8544bb43a
topic_type:
- apiref
ms.openlocfilehash: a8642235cda359b849c49a35ab565397402c37d2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130513"
---
# <a name="ihostcrstsetspincount-method"></a><span data-ttu-id="3808d-102">IHostCrst::SetSpinCount, méthode</span><span class="sxs-lookup"><span data-stu-id="3808d-102">IHostCrst::SetSpinCount Method</span></span>
<span data-ttu-id="3808d-103">Définit le nombre de spins pour l’instance [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) actuelle.</span><span class="sxs-lookup"><span data-stu-id="3808d-103">Sets the spin count for the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3808d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3808d-104">Syntax</span></span>  
  
```cpp  
HRESULT SetSpinCount (  
    [in] DWORD dwSpinCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3808d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3808d-105">Parameters</span></span>  
 `dwSpinCount`  
 <span data-ttu-id="3808d-106">dans Nouveau nombre de spins pour l’instance de `IHostCrst` actuelle.</span><span class="sxs-lookup"><span data-stu-id="3808d-106">[in] The new spin count for the current `IHostCrst` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3808d-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="3808d-107">Return Value</span></span>  
  
|<span data-ttu-id="3808d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3808d-108">HRESULT</span></span>|<span data-ttu-id="3808d-109">Description</span><span class="sxs-lookup"><span data-stu-id="3808d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3808d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3808d-110">S_OK</span></span>|<span data-ttu-id="3808d-111">`SetSpinCount` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="3808d-111">`SetSpinCount` returned successfully.</span></span>|  
|<span data-ttu-id="3808d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3808d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3808d-113">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="3808d-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3808d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3808d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3808d-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="3808d-115">The call timed out.</span></span>|  
|<span data-ttu-id="3808d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3808d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3808d-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="3808d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3808d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3808d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3808d-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="3808d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3808d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3808d-120">E_FAIL</span></span>|<span data-ttu-id="3808d-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="3808d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3808d-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="3808d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3808d-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3808d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3808d-124">Notes</span><span class="sxs-lookup"><span data-stu-id="3808d-124">Remarks</span></span>  
 <span data-ttu-id="3808d-125">Sur les systèmes multiprocesseurs, si la section critique représentée par l’instance actuelle de `IHostCrst` n’est pas disponible, un thread appelant tourne `dwSpinCount` fois avant d’appeler [IHostSemaphore :: wait](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md) sur un sémaphore associé à la section critique.</span><span class="sxs-lookup"><span data-stu-id="3808d-125">On multi-processor systems, if the critical section represented by the current `IHostCrst` instance is unavailable, a calling thread spins `dwSpinCount` times before calling [IHostSemaphore::Wait](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md) on a semaphore associated with the critical section.</span></span> <span data-ttu-id="3808d-126">Si la section critique devient libre pendant l’opération de rotation, le thread appelant évite l’opération d’attente.</span><span class="sxs-lookup"><span data-stu-id="3808d-126">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span>  
  
 <span data-ttu-id="3808d-127">L’utilisation de `dwSpinCount` est identique à l’utilisation du paramètre du même nom dans la fonction Win32 `InitializeCriticalSectionAndSpinCount`.</span><span class="sxs-lookup"><span data-stu-id="3808d-127">The usage of `dwSpinCount` is identical to the usage of the parameter of the same name in the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3808d-128">spécifications</span><span class="sxs-lookup"><span data-stu-id="3808d-128">Requirements</span></span>  
 <span data-ttu-id="3808d-129">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3808d-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3808d-130">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3808d-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3808d-131">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3808d-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3808d-132">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3808d-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3808d-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3808d-133">See also</span></span>

- [<span data-ttu-id="3808d-134">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="3808d-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="3808d-135">IHostCrst, interface</span><span class="sxs-lookup"><span data-stu-id="3808d-135">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="3808d-136">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="3808d-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
