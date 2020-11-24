---
title: IHostManualEvent::Set, méthode
ms.date: 03/30/2017
api_name:
- IHostManualEvent.Set
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent::Set
helpviewer_keywords:
- Set method, IHostManualEvent interface [.NET Framework hosting]
- IHostManualEvent::Set method [.NET Framework hosting]
ms.assetid: e930c174-f71d-4faa-bb59-f0fb3df4d77b
topic_type:
- apiref
ms.openlocfilehash: bc2b178c6c26a6de62982c35d5aeb9ea5359c2bf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679128"
---
# <a name="ihostmanualeventset-method"></a><span data-ttu-id="df7be-102">IHostManualEvent::Set, méthode</span><span class="sxs-lookup"><span data-stu-id="df7be-102">IHostManualEvent::Set Method</span></span>

<span data-ttu-id="df7be-103">Définit l’instance [IHostManualEvent](ihostmanualevent-interface.md) actuelle à un état signalé.</span><span class="sxs-lookup"><span data-stu-id="df7be-103">Sets the current [IHostManualEvent](ihostmanualevent-interface.md) instance to a signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df7be-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="df7be-104">Syntax</span></span>  
  
```cpp  
HRESULT Set ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="df7be-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="df7be-105">Return Value</span></span>  
  
|<span data-ttu-id="df7be-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="df7be-106">HRESULT</span></span>|<span data-ttu-id="df7be-107">Description</span><span class="sxs-lookup"><span data-stu-id="df7be-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="df7be-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="df7be-108">S_OK</span></span>|<span data-ttu-id="df7be-109">`Set` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="df7be-109">`Set` returned successfully.</span></span>|  
|<span data-ttu-id="df7be-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="df7be-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="df7be-111">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="df7be-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="df7be-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="df7be-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="df7be-113">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="df7be-113">The call timed out.</span></span>|  
|<span data-ttu-id="df7be-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="df7be-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="df7be-115">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="df7be-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="df7be-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="df7be-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="df7be-117">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="df7be-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="df7be-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="df7be-118">E_FAIL</span></span>|<span data-ttu-id="df7be-119">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="df7be-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="df7be-120">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="df7be-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="df7be-121">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="df7be-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="df7be-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="df7be-122">Requirements</span></span>  

 <span data-ttu-id="df7be-123">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df7be-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df7be-124">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="df7be-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="df7be-125">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="df7be-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="df7be-126">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df7be-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df7be-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="df7be-127">See also</span></span>

- [<span data-ttu-id="df7be-128">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="df7be-128">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="df7be-129">IHostAutoEvent, interface</span><span class="sxs-lookup"><span data-stu-id="df7be-129">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="df7be-130">IHostManualEvent, interface</span><span class="sxs-lookup"><span data-stu-id="df7be-130">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="df7be-131">IHostSemaphore, interface</span><span class="sxs-lookup"><span data-stu-id="df7be-131">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="df7be-132">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="df7be-132">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
