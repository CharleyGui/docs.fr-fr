---
title: IHostAutoEvent::Wait, méthode
ms.date: 03/30/2017
api_name:
- IHostAutoEvent.Wait
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAutoEvent::Wait
helpviewer_keywords:
- Wait method, IHostAutoEvent interface [.NET Framework hosting]
- IHostAutoEvent::Wait method [.NET Framework hosting]
ms.assetid: 535d51c5-9112-401b-8c36-85f35d7ee609
topic_type:
- apiref
ms.openlocfilehash: 7baabafc61e14d127ff3f0cdb7453be6f1a2abeb
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804970"
---
# <a name="ihostautoeventwait-method"></a><span data-ttu-id="2fd4c-102">IHostAutoEvent::Wait, méthode</span><span class="sxs-lookup"><span data-stu-id="2fd4c-102">IHostAutoEvent::Wait Method</span></span>
<span data-ttu-id="2fd4c-103">Entraîne l’attente de l’instance [IHostAutoEvent](ihostautoevent-interface.md) actuelle jusqu’à ce qu’elle appartienne ou qu’un laps de temps spécifié se soit écoulé.</span><span class="sxs-lookup"><span data-stu-id="2fd4c-103">Causes the current [IHostAutoEvent](ihostautoevent-interface.md) instance to wait until it is owned or a specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fd4c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2fd4c-104">Syntax</span></span>  
  
```cpp  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2fd4c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2fd4c-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="2fd4c-106">dans Nombre de millisecondes pendant lesquelles l' `IHostAutoEvent` instance actuelle doit attendre avant de retourner, si aucun thread ou aucune fibre ne prend possession de la propriété.</span><span class="sxs-lookup"><span data-stu-id="2fd4c-106">[in] The number of milliseconds the current `IHostAutoEvent` instance should wait before returning, if no thread or fiber takes ownership.</span></span>  
  
 `option`  
 <span data-ttu-id="2fd4c-107">dans L’une des valeurs [WAIT_OPTION](wait-option-enumeration.md) , en spécifiant l’action que l’hôte doit effectuer si cette opération bloque.</span><span class="sxs-lookup"><span data-stu-id="2fd4c-107">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) values, specifying the action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2fd4c-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="2fd4c-108">Return Value</span></span>  
  
|<span data-ttu-id="2fd4c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2fd4c-109">HRESULT</span></span>|<span data-ttu-id="2fd4c-110">Description</span><span class="sxs-lookup"><span data-stu-id="2fd4c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2fd4c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="2fd4c-111">S_OK</span></span>|<span data-ttu-id="2fd4c-112">`Wait`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="2fd4c-112">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="2fd4c-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2fd4c-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2fd4c-114">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="2fd4c-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2fd4c-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2fd4c-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2fd4c-116">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="2fd4c-116">The call timed out.</span></span>|  
|<span data-ttu-id="2fd4c-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2fd4c-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2fd4c-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="2fd4c-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2fd4c-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2fd4c-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2fd4c-120">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="2fd4c-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2fd4c-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2fd4c-121">E_FAIL</span></span>|<span data-ttu-id="2fd4c-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="2fd4c-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2fd4c-123">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="2fd4c-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2fd4c-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2fd4c-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2fd4c-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="2fd4c-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="2fd4c-126">L’hôte a détecté un blocage pendant l’intervalle d’attente et a choisi l’événement représenté par l' `IHostAutoEvent` instance actuelle comme victime du blocage.</span><span class="sxs-lookup"><span data-stu-id="2fd4c-126">The host detected a deadlock during the wait interval, and chose the event represented by the current `IHostAutoEvent` instance as the deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2fd4c-127">Spécifications</span><span class="sxs-lookup"><span data-stu-id="2fd4c-127">Requirements</span></span>  
 <span data-ttu-id="2fd4c-128">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2fd4c-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2fd4c-129">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2fd4c-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2fd4c-130">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2fd4c-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2fd4c-131">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2fd4c-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fd4c-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2fd4c-132">See also</span></span>

- [<span data-ttu-id="2fd4c-133">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="2fd4c-133">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="2fd4c-134">IHostAutoEvent, interface</span><span class="sxs-lookup"><span data-stu-id="2fd4c-134">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="2fd4c-135">IHostManualEvent, interface</span><span class="sxs-lookup"><span data-stu-id="2fd4c-135">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="2fd4c-136">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="2fd4c-136">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
