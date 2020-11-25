---
title: IHostSyncManager::CreateManualEvent, méthode
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateManualEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateManualEvent
helpviewer_keywords:
- CreateManualEvent method [.NET Framework hosting]
- IHostSyncManager::CreateManualEvent method [.NET Framework hosting]
ms.assetid: 68661fbd-09cf-46dc-890b-e694f8a3880a
topic_type:
- apiref
ms.openlocfilehash: 67af8f125b2be39138bac5d51148215f3a3acf86
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723868"
---
# <a name="ihostsyncmanagercreatemanualevent-method"></a><span data-ttu-id="9792c-102">IHostSyncManager::CreateManualEvent, méthode</span><span class="sxs-lookup"><span data-stu-id="9792c-102">IHostSyncManager::CreateManualEvent Method</span></span>

<span data-ttu-id="9792c-103">Crée un objet d’événement de réinitialisation manuelle.</span><span class="sxs-lookup"><span data-stu-id="9792c-103">Creates a manual-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9792c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9792c-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateManualEvent (  
    [in]  BOOL bInitialState,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9792c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9792c-105">Parameters</span></span>  

 `bInitialState`  
 <span data-ttu-id="9792c-106">[in] `true` , si l’objet est signalé ; sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="9792c-106">[in] `true`, if the object is signaled; otherwise, `false`.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="9792c-107">à Pointeur vers l’adresse d’une instance [IHostManualEvent](ihostmanualevent-interface.md) , ou null si l’événement n’a pas pu être créé.</span><span class="sxs-lookup"><span data-stu-id="9792c-107">[out] A pointer to the address of an [IHostManualEvent](ihostmanualevent-interface.md) instance, or null if the event could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9792c-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="9792c-108">Return Value</span></span>  
  
|<span data-ttu-id="9792c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9792c-109">HRESULT</span></span>|<span data-ttu-id="9792c-110">Description</span><span class="sxs-lookup"><span data-stu-id="9792c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9792c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="9792c-111">S_OK</span></span>|<span data-ttu-id="9792c-112">`CreateManualEvent` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="9792c-112">`CreateManualEvent` returned successfully.</span></span>|  
|<span data-ttu-id="9792c-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9792c-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9792c-114">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="9792c-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9792c-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9792c-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9792c-116">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="9792c-116">The call timed out.</span></span>|  
|<span data-ttu-id="9792c-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9792c-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9792c-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="9792c-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9792c-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9792c-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9792c-120">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="9792c-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9792c-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9792c-121">E_FAIL</span></span>|<span data-ttu-id="9792c-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="9792c-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9792c-123">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="9792c-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9792c-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9792c-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9792c-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="9792c-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="9792c-126">Mémoire disponible insuffisante pour créer l’objet d’événement demandé.</span><span class="sxs-lookup"><span data-stu-id="9792c-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9792c-127">Remarques</span><span class="sxs-lookup"><span data-stu-id="9792c-127">Remarks</span></span>  

 <span data-ttu-id="9792c-128">`CreateManualEvent` crée un `IHostManualEvent` , un objet d’événement de réinitialisation manuelle qui requiert un appel à la méthode [IHostManualEvent :: Reset](ihostmanualevent-reset-method.md) pour lui affecter un État non signalé.</span><span class="sxs-lookup"><span data-stu-id="9792c-128">`CreateManualEvent` creates an `IHostManualEvent`, a manual-reset event object that requires a call to the [IHostManualEvent::Reset](ihostmanualevent-reset-method.md) method to set it to a non-signaled state.</span></span> <span data-ttu-id="9792c-129">`CreateManualEvent` reflète la `CreateEvent` fonction Win32 avec la valeur `true` spécifiée pour le `bManualReset` paramètre.</span><span class="sxs-lookup"><span data-stu-id="9792c-129">`CreateManualEvent` mirrors the Win32 `CreateEvent` function with a value of `true` specified for the `bManualReset` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9792c-130">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9792c-130">Requirements</span></span>  

 <span data-ttu-id="9792c-131">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9792c-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9792c-132">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9792c-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9792c-133">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9792c-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9792c-134">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9792c-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9792c-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9792c-135">See also</span></span>

- [<span data-ttu-id="9792c-136">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="9792c-136">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="9792c-137">IHostManualEvent, interface</span><span class="sxs-lookup"><span data-stu-id="9792c-137">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="9792c-138">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="9792c-138">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
