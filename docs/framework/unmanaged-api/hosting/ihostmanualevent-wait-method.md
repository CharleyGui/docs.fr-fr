---
title: IHostManualEvent::Wait, méthode
ms.date: 03/30/2017
api_name:
- IHostManualEvent.Wait
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent::Wait
helpviewer_keywords:
- IHostManualEvent::Wait method [.NET Framework hosting]
- Wait method, IHostManualEvent interface [.NET Framework hosting]
ms.assetid: 1fbb7d8b-8a23-4c2b-8376-1a70cd2d6030
topic_type:
- apiref
ms.openlocfilehash: 6d0276764a07d5bb202d66b653fdf5cb96320c08
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804554"
---
# <a name="ihostmanualeventwait-method"></a><span data-ttu-id="2cebb-102">IHostManualEvent::Wait, méthode</span><span class="sxs-lookup"><span data-stu-id="2cebb-102">IHostManualEvent::Wait Method</span></span>
<span data-ttu-id="2cebb-103">Entraîne l’attente de l’instance [IHostManualEvent](ihostmanualevent-interface.md) actuelle jusqu’à ce qu’elle appartienne ou qu’un laps de temps spécifié se soit écoulé.</span><span class="sxs-lookup"><span data-stu-id="2cebb-103">Causes the current [IHostManualEvent](ihostmanualevent-interface.md) instance to wait until it is owned, or a specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cebb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2cebb-104">Syntax</span></span>  
  
```cpp  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2cebb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2cebb-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="2cebb-106">dans Nombre de millisecondes à attendre avant de retourner, si l’instance actuelle `IHostManualEvent` n’appartient pas.</span><span class="sxs-lookup"><span data-stu-id="2cebb-106">[in] The number of milliseconds to wait before returning, if the current `IHostManualEvent` instance is not owned.</span></span>  
  
 `option`  
 <span data-ttu-id="2cebb-107">dans L’une des valeurs [WAIT_OPTION](wait-option-enumeration.md) , indiquant l’action que l’hôte doit effectuer si cette opération bloque.</span><span class="sxs-lookup"><span data-stu-id="2cebb-107">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) values, indicating the action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2cebb-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="2cebb-108">Return Value</span></span>  
  
|<span data-ttu-id="2cebb-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2cebb-109">HRESULT</span></span>|<span data-ttu-id="2cebb-110">Description</span><span class="sxs-lookup"><span data-stu-id="2cebb-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2cebb-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="2cebb-111">S_OK</span></span>|<span data-ttu-id="2cebb-112">`Wait`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="2cebb-112">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="2cebb-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2cebb-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2cebb-114">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="2cebb-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2cebb-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2cebb-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2cebb-116">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="2cebb-116">The call timed out.</span></span>|  
|<span data-ttu-id="2cebb-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2cebb-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2cebb-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="2cebb-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2cebb-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2cebb-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2cebb-120">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="2cebb-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2cebb-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2cebb-121">E_FAIL</span></span>|<span data-ttu-id="2cebb-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="2cebb-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2cebb-123">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="2cebb-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2cebb-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2cebb-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2cebb-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="2cebb-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="2cebb-126">L’hôte a détecté un blocage pendant l’intervalle d’attente et a choisi l' `IHostManualEvent` instance actuelle comme victime du blocage.</span><span class="sxs-lookup"><span data-stu-id="2cebb-126">The host detected a deadlock during the wait interval, and chose the current `IHostManualEvent` instance as the deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2cebb-127">Spécifications</span><span class="sxs-lookup"><span data-stu-id="2cebb-127">Requirements</span></span>  
 <span data-ttu-id="2cebb-128">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2cebb-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2cebb-129">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2cebb-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2cebb-130">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2cebb-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2cebb-131">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2cebb-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cebb-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2cebb-132">See also</span></span>

- [<span data-ttu-id="2cebb-133">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="2cebb-133">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="2cebb-134">IHostAutoEvent, interface</span><span class="sxs-lookup"><span data-stu-id="2cebb-134">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="2cebb-135">IHostManualEvent, interface</span><span class="sxs-lookup"><span data-stu-id="2cebb-135">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="2cebb-136">IHostSemaphore, interface</span><span class="sxs-lookup"><span data-stu-id="2cebb-136">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="2cebb-137">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="2cebb-137">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
