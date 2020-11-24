---
title: IHostAutoEvent::Set, méthode
ms.date: 03/30/2017
api_name:
- IHostAutoEvent.Set
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAutoEvent::Set
helpviewer_keywords:
- Set method, IHostAutoEvent interface [.NET Framework hosting]
- IHostAutoEvent::Set method [.NET Framework hosting]
ms.assetid: 46becf3e-bc0e-4338-85c0-9ab0df76a1d0
topic_type:
- apiref
ms.openlocfilehash: facfbb85645f444b010cb1fe1c34bbe94011ac50
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680824"
---
# <a name="ihostautoeventset-method"></a><span data-ttu-id="dcd59-102">IHostAutoEvent::Set, méthode</span><span class="sxs-lookup"><span data-stu-id="dcd59-102">IHostAutoEvent::Set Method</span></span>

<span data-ttu-id="dcd59-103">Définit l’instance [IHostAutoEvent](ihostautoevent-interface.md) actuelle sur un état signalé.</span><span class="sxs-lookup"><span data-stu-id="dcd59-103">Sets the current [IHostAutoEvent](ihostautoevent-interface.md) instance to a signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcd59-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dcd59-104">Syntax</span></span>  
  
```cpp  
HRESULT Set ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="dcd59-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="dcd59-105">Return Value</span></span>  
  
|<span data-ttu-id="dcd59-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dcd59-106">HRESULT</span></span>|<span data-ttu-id="dcd59-107">Description</span><span class="sxs-lookup"><span data-stu-id="dcd59-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dcd59-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="dcd59-108">S_OK</span></span>|<span data-ttu-id="dcd59-109">`Set` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="dcd59-109">`Set` returned successfully.</span></span>|  
|<span data-ttu-id="dcd59-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dcd59-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dcd59-111">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="dcd59-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dcd59-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dcd59-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dcd59-113">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="dcd59-113">The call timed out.</span></span>|  
|<span data-ttu-id="dcd59-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dcd59-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dcd59-115">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="dcd59-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dcd59-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dcd59-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dcd59-117">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="dcd59-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dcd59-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dcd59-118">E_FAIL</span></span>|<span data-ttu-id="dcd59-119">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="dcd59-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dcd59-120">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="dcd59-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dcd59-121">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="dcd59-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dcd59-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="dcd59-122">Requirements</span></span>  

 <span data-ttu-id="dcd59-123">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dcd59-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcd59-124">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="dcd59-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dcd59-125">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dcd59-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dcd59-126">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcd59-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcd59-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dcd59-127">See also</span></span>

- [<span data-ttu-id="dcd59-128">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="dcd59-128">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="dcd59-129">IHostAutoEvent, interface</span><span class="sxs-lookup"><span data-stu-id="dcd59-129">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="dcd59-130">IHostManualEvent, interface</span><span class="sxs-lookup"><span data-stu-id="dcd59-130">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="dcd59-131">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="dcd59-131">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
