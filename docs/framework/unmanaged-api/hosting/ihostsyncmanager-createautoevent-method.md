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
ms.openlocfilehash: ba221beaa0edce49e75f75edddaee72e1beb9747
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803501"
---
# <a name="ihostsyncmanagercreateautoevent-method"></a><span data-ttu-id="f425e-102">IHostSyncManager::CreateAutoEvent, méthode</span><span class="sxs-lookup"><span data-stu-id="f425e-102">IHostSyncManager::CreateAutoEvent Method</span></span>
<span data-ttu-id="f425e-103">Crée un objet d’événement à réinitialisation automatique.</span><span class="sxs-lookup"><span data-stu-id="f425e-103">Creates an auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f425e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f425e-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAutoEvent (  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f425e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f425e-105">Parameters</span></span>  
 `ppEvent`  
 <span data-ttu-id="f425e-106">à Pointeur vers l’adresse d’une instance [IHostAutoEvent](ihostautoevent-interface.md) implémentée par l’hôte, ou null si l’objet d’événement n’a pas pu être créé.</span><span class="sxs-lookup"><span data-stu-id="f425e-106">[out] A pointer to the address of an [IHostAutoEvent](ihostautoevent-interface.md) instance implemented by the host, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f425e-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f425e-107">Return Value</span></span>  
  
|<span data-ttu-id="f425e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f425e-108">HRESULT</span></span>|<span data-ttu-id="f425e-109">Description</span><span class="sxs-lookup"><span data-stu-id="f425e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f425e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f425e-110">S_OK</span></span>|<span data-ttu-id="f425e-111">`CreateAutoEvent`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="f425e-111">`CreateAutoEvent` returned successfully.</span></span>|  
|<span data-ttu-id="f425e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f425e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f425e-113">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="f425e-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f425e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f425e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f425e-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="f425e-115">The call timed out.</span></span>|  
|<span data-ttu-id="f425e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f425e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f425e-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="f425e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f425e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f425e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f425e-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="f425e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f425e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f425e-120">E_FAIL</span></span>|<span data-ttu-id="f425e-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="f425e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f425e-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="f425e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f425e-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f425e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f425e-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="f425e-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="f425e-125">Mémoire disponible insuffisante pour créer l’objet d’événement demandé.</span><span class="sxs-lookup"><span data-stu-id="f425e-125">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f425e-126">Notes</span><span class="sxs-lookup"><span data-stu-id="f425e-126">Remarks</span></span>  
 <span data-ttu-id="f425e-127">`CreateAutoEvent`crée un objet d’événement automatique dont l’État est automatiquement modifié en non signalé après la libération du thread en attente.</span><span class="sxs-lookup"><span data-stu-id="f425e-127">`CreateAutoEvent` creates an auto-event object whose state is automatically changed to non-signaled after the waiting thread has been released.</span></span> <span data-ttu-id="f425e-128">Cette méthode reflète la `CreateEvent` fonction Win32 avec la valeur `false` spécifiée pour le `bManualReset` paramètre.</span><span class="sxs-lookup"><span data-stu-id="f425e-128">This method mirrors the Win32 `CreateEvent` function with a value of `false` specified for the `bManualReset` parameter</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f425e-129">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f425e-129">Requirements</span></span>  
 <span data-ttu-id="f425e-130">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f425e-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f425e-131">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f425e-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f425e-132">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f425e-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f425e-133">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f425e-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f425e-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f425e-134">See also</span></span>

- [<span data-ttu-id="f425e-135">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="f425e-135">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="f425e-136">IHostAutoEvent, interface</span><span class="sxs-lookup"><span data-stu-id="f425e-136">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="f425e-137">IHostControl, interface</span><span class="sxs-lookup"><span data-stu-id="f425e-137">IHostControl Interface</span></span>](ihostcontrol-interface.md)
- [<span data-ttu-id="f425e-138">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="f425e-138">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
