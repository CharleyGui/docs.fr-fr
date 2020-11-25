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
ms.openlocfilehash: 22274759f931da614a234efe0a6f6eb3aade027c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729562"
---
# <a name="ihostcrstsetspincount-method"></a><span data-ttu-id="18569-102">IHostCrst::SetSpinCount, méthode</span><span class="sxs-lookup"><span data-stu-id="18569-102">IHostCrst::SetSpinCount Method</span></span>

<span data-ttu-id="18569-103">Définit le nombre de spins pour l’instance [IHostCrst](ihostcrst-interface.md) actuelle.</span><span class="sxs-lookup"><span data-stu-id="18569-103">Sets the spin count for the current [IHostCrst](ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18569-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="18569-104">Syntax</span></span>  
  
```cpp  
HRESULT SetSpinCount (  
    [in] DWORD dwSpinCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="18569-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="18569-105">Parameters</span></span>  

 `dwSpinCount`  
 <span data-ttu-id="18569-106">dans Nouveau nombre de spins pour l' `IHostCrst` instance actuelle.</span><span class="sxs-lookup"><span data-stu-id="18569-106">[in] The new spin count for the current `IHostCrst` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="18569-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="18569-107">Return Value</span></span>  
  
|<span data-ttu-id="18569-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="18569-108">HRESULT</span></span>|<span data-ttu-id="18569-109">Description</span><span class="sxs-lookup"><span data-stu-id="18569-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="18569-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="18569-110">S_OK</span></span>|<span data-ttu-id="18569-111">`SetSpinCount` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="18569-111">`SetSpinCount` returned successfully.</span></span>|  
|<span data-ttu-id="18569-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="18569-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="18569-113">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="18569-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="18569-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="18569-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="18569-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="18569-115">The call timed out.</span></span>|  
|<span data-ttu-id="18569-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="18569-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="18569-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="18569-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="18569-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="18569-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="18569-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="18569-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="18569-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="18569-120">E_FAIL</span></span>|<span data-ttu-id="18569-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="18569-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="18569-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="18569-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="18569-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="18569-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18569-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="18569-124">Remarks</span></span>  

 <span data-ttu-id="18569-125">Sur les systèmes multiprocesseurs, si la section critique représentée par l' `IHostCrst` instance actuelle n’est pas disponible, un thread appelant fait tourner les `dwSpinCount` heures avant d’appeler [IHostSemaphore :: wait](ihostsemaphore-wait-method.md) sur un sémaphore associé à la section critique.</span><span class="sxs-lookup"><span data-stu-id="18569-125">On multi-processor systems, if the critical section represented by the current `IHostCrst` instance is unavailable, a calling thread spins `dwSpinCount` times before calling [IHostSemaphore::Wait](ihostsemaphore-wait-method.md) on a semaphore associated with the critical section.</span></span> <span data-ttu-id="18569-126">Si la section critique devient libre pendant l’opération de rotation, le thread appelant évite l’opération d’attente.</span><span class="sxs-lookup"><span data-stu-id="18569-126">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span>  
  
 <span data-ttu-id="18569-127">L’utilisation de `dwSpinCount` est identique à l’utilisation du paramètre du même nom dans la `InitializeCriticalSectionAndSpinCount` fonction Win32.</span><span class="sxs-lookup"><span data-stu-id="18569-127">The usage of `dwSpinCount` is identical to the usage of the parameter of the same name in the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18569-128">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="18569-128">Requirements</span></span>  

 <span data-ttu-id="18569-129">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18569-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18569-130">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="18569-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="18569-131">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="18569-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="18569-132">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18569-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18569-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="18569-133">See also</span></span>

- [<span data-ttu-id="18569-134">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="18569-134">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="18569-135">IHostCrst, interface</span><span class="sxs-lookup"><span data-stu-id="18569-135">IHostCrst Interface</span></span>](ihostcrst-interface.md)
- [<span data-ttu-id="18569-136">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="18569-136">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
