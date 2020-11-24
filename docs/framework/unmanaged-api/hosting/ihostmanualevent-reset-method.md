---
title: IHostManualEvent::Reset, méthode
ms.date: 03/30/2017
api_name:
- IHostManualEvent.Reset
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent::Reset
helpviewer_keywords:
- Reset method, IHostManualEvent interface [.NET Framework hosting]
- IHostManualEvent::Reset method [.NET Framework hosting]
ms.assetid: 0d101168-b5e3-49ce-90c7-85cf2db83c4c
topic_type:
- apiref
ms.openlocfilehash: 5653f874ef7a681f6667b3508b82ac493234cc4e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673135"
---
# <a name="ihostmanualeventreset-method"></a><span data-ttu-id="d2d9b-102">IHostManualEvent::Reset, méthode</span><span class="sxs-lookup"><span data-stu-id="d2d9b-102">IHostManualEvent::Reset Method</span></span>

<span data-ttu-id="d2d9b-103">Réinitialise l’instance [IHostManualEvent](ihostmanualevent-interface.md) actuelle à un État non signalé.</span><span class="sxs-lookup"><span data-stu-id="d2d9b-103">Resets the current [IHostManualEvent](ihostmanualevent-interface.md) instance to a non-signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2d9b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d2d9b-104">Syntax</span></span>  
  
```cpp  
HRESULT Reset ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="d2d9b-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d2d9b-105">Return Value</span></span>  
  
|<span data-ttu-id="d2d9b-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d2d9b-106">HRESULT</span></span>|<span data-ttu-id="d2d9b-107">Description</span><span class="sxs-lookup"><span data-stu-id="d2d9b-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d2d9b-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="d2d9b-108">S_OK</span></span>|<span data-ttu-id="d2d9b-109">`Reset` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="d2d9b-109">`Reset` returned successfully.</span></span>|  
|<span data-ttu-id="d2d9b-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d2d9b-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d2d9b-111">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="d2d9b-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d2d9b-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d2d9b-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d2d9b-113">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="d2d9b-113">The call timed out.</span></span>|  
|<span data-ttu-id="d2d9b-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d2d9b-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d2d9b-115">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="d2d9b-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d2d9b-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d2d9b-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d2d9b-117">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="d2d9b-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d2d9b-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d2d9b-118">E_FAIL</span></span>|<span data-ttu-id="d2d9b-119">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="d2d9b-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d2d9b-120">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="d2d9b-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d2d9b-121">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d2d9b-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d2d9b-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d2d9b-122">Requirements</span></span>  

 <span data-ttu-id="d2d9b-123">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2d9b-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2d9b-124">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d2d9b-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d2d9b-125">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d2d9b-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d2d9b-126">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2d9b-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2d9b-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d2d9b-127">See also</span></span>

- [<span data-ttu-id="d2d9b-128">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="d2d9b-128">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="d2d9b-129">IHostAutoEvent, interface</span><span class="sxs-lookup"><span data-stu-id="d2d9b-129">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="d2d9b-130">IHostManualEvent, interface</span><span class="sxs-lookup"><span data-stu-id="d2d9b-130">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="d2d9b-131">IHostSemaphore, interface</span><span class="sxs-lookup"><span data-stu-id="d2d9b-131">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="d2d9b-132">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="d2d9b-132">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
