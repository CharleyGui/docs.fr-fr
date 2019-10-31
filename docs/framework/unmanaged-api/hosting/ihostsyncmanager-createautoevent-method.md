---
title: IHostSyncManager::CreateAutoEvent, méthode
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateAutoEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateAutoEvent
helpviewer_keywords:
- IHostSyncManager::CreateAutoEvent method [.NET Framework hosting]
- CreateAutoEvent method [.NET Framework hosting]
ms.assetid: 3153643e-cf5c-4b44-8e0e-c2b22cb08208
topic_type:
- apiref
ms.openlocfilehash: b3778e12dd96d4f4653633252e13469601c4879d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139441"
---
# <a name="ihostsyncmanagercreateautoevent-method"></a><span data-ttu-id="646e3-102">IHostSyncManager::CreateAutoEvent, méthode</span><span class="sxs-lookup"><span data-stu-id="646e3-102">IHostSyncManager::CreateAutoEvent Method</span></span>
<span data-ttu-id="646e3-103">Crée un objet d’événement à réinitialisation automatique.</span><span class="sxs-lookup"><span data-stu-id="646e3-103">Creates an auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="646e3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="646e3-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAutoEvent (  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="646e3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="646e3-105">Parameters</span></span>  
 `ppEvent`  
 <span data-ttu-id="646e3-106">à Pointeur vers l’adresse d’une instance [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) implémentée par l’hôte, ou null si l’objet d’événement n’a pas pu être créé.</span><span class="sxs-lookup"><span data-stu-id="646e3-106">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance implemented by the host, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="646e3-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="646e3-107">Return Value</span></span>  
  
|<span data-ttu-id="646e3-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="646e3-108">HRESULT</span></span>|<span data-ttu-id="646e3-109">Description</span><span class="sxs-lookup"><span data-stu-id="646e3-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="646e3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="646e3-110">S_OK</span></span>|<span data-ttu-id="646e3-111">`CreateAutoEvent` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="646e3-111">`CreateAutoEvent` returned successfully.</span></span>|  
|<span data-ttu-id="646e3-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="646e3-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="646e3-113">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="646e3-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="646e3-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="646e3-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="646e3-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="646e3-115">The call timed out.</span></span>|  
|<span data-ttu-id="646e3-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="646e3-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="646e3-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="646e3-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="646e3-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="646e3-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="646e3-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="646e3-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="646e3-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="646e3-120">E_FAIL</span></span>|<span data-ttu-id="646e3-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="646e3-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="646e3-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="646e3-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="646e3-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="646e3-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="646e3-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="646e3-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="646e3-125">Mémoire disponible insuffisante pour créer l’objet d’événement demandé.</span><span class="sxs-lookup"><span data-stu-id="646e3-125">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="646e3-126">Notes</span><span class="sxs-lookup"><span data-stu-id="646e3-126">Remarks</span></span>  
 <span data-ttu-id="646e3-127">`CreateAutoEvent` crée un objet d’événement automatique dont l’État est automatiquement modifié en non signalé une fois que le thread en attente a été libéré.</span><span class="sxs-lookup"><span data-stu-id="646e3-127">`CreateAutoEvent` creates an auto-event object whose state is automatically changed to non-signaled after the waiting thread has been released.</span></span> <span data-ttu-id="646e3-128">Cette méthode reflète la fonction Win32 `CreateEvent` avec la valeur `false` spécifiée pour le paramètre `bManualReset`</span><span class="sxs-lookup"><span data-stu-id="646e3-128">This method mirrors the Win32 `CreateEvent` function with a value of `false` specified for the `bManualReset` parameter</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="646e3-129">spécifications</span><span class="sxs-lookup"><span data-stu-id="646e3-129">Requirements</span></span>  
 <span data-ttu-id="646e3-130">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="646e3-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="646e3-131">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="646e3-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="646e3-132">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="646e3-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="646e3-133">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="646e3-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="646e3-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="646e3-134">See also</span></span>

- [<span data-ttu-id="646e3-135">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="646e3-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="646e3-136">IHostAutoEvent, interface</span><span class="sxs-lookup"><span data-stu-id="646e3-136">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="646e3-137">IHostControl, interface</span><span class="sxs-lookup"><span data-stu-id="646e3-137">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
- [<span data-ttu-id="646e3-138">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="646e3-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
