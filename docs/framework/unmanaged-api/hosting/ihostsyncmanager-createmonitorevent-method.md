---
title: IHostSyncManager::CreateMonitorEvent, méthode
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateMonitorEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateMonitorEvent
helpviewer_keywords:
- CreateMonitorEvent method [.NET Framework hosting]
- IHostSyncManager::CreateMonitorEvent method [.NET Framework hosting]
ms.assetid: 524c7fd3-9b5c-46e7-99ba-555fd2fe33f0
topic_type:
- apiref
ms.openlocfilehash: c0f7e1fd6bf4c9386300b11477df85e87899fc67
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803318"
---
# <a name="ihostsyncmanagercreatemonitorevent-method"></a><span data-ttu-id="77597-102">IHostSyncManager::CreateMonitorEvent, méthode</span><span class="sxs-lookup"><span data-stu-id="77597-102">IHostSyncManager::CreateMonitorEvent Method</span></span>
<span data-ttu-id="77597-103">Crée un objet d’événement de réinitialisation automatique surveillé.</span><span class="sxs-lookup"><span data-stu-id="77597-103">Creates a monitored auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77597-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="77597-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateMonitorEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77597-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="77597-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="77597-106">dans Cookie à associer à l’objet d’événement.</span><span class="sxs-lookup"><span data-stu-id="77597-106">[in] A cookie to associate with the event object.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="77597-107">à Pointeur vers l’adresse d’une instance [IHostAutoEvent](ihostautoevent-interface.md) , ou null si l’objet d’événement n’a pas pu être créé.</span><span class="sxs-lookup"><span data-stu-id="77597-107">[out] A pointer to the address of an [IHostAutoEvent](ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="77597-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="77597-108">Return Value</span></span>  
  
|<span data-ttu-id="77597-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="77597-109">HRESULT</span></span>|<span data-ttu-id="77597-110">Description</span><span class="sxs-lookup"><span data-stu-id="77597-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="77597-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="77597-111">S_OK</span></span>|<span data-ttu-id="77597-112">`CreateMonitorEvent`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="77597-112">`CreateMonitorEvent` returned successfully.</span></span>|  
|<span data-ttu-id="77597-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="77597-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="77597-114">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="77597-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="77597-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="77597-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="77597-116">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="77597-116">The call timed out.</span></span>|  
|<span data-ttu-id="77597-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="77597-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="77597-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="77597-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="77597-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="77597-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="77597-120">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="77597-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="77597-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="77597-121">E_FAIL</span></span>|<span data-ttu-id="77597-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="77597-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="77597-123">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="77597-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="77597-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="77597-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="77597-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="77597-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="77597-126">Mémoire disponible insuffisante pour créer l’objet d’événement demandé.</span><span class="sxs-lookup"><span data-stu-id="77597-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77597-127">Notes</span><span class="sxs-lookup"><span data-stu-id="77597-127">Remarks</span></span>  
 <span data-ttu-id="77597-128">`CreateMonitorEvent`retourne un `IHostAutoEvent` que le CLR utilise dans son implémentation du type managé <xref:System.Threading.Monitor?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="77597-128">`CreateMonitorEvent` returns an `IHostAutoEvent` that the CLR uses in its implementation of the managed <xref:System.Threading.Monitor?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="77597-129">Cette méthode reflète la `CreateEvent` fonction Win32, avec `false` la valeur spécifiée pour le `bManualReset` paramètre.</span><span class="sxs-lookup"><span data-stu-id="77597-129">This method mirrors the Win32 `CreateEvent` function, with a value of `false` specified for the `bManualReset` parameter.</span></span>  
  
 <span data-ttu-id="77597-130">L’hôte peut utiliser le cookie pour déterminer quelle tâche est en attente sur l’analyse en appelant la méthode [ICLRSyncManager :: GetMonitorOwner,](iclrsyncmanager-getmonitorowner-method.md) .</span><span class="sxs-lookup"><span data-stu-id="77597-130">The host can use the cookie to determine which task is waiting on the monitor by calling the [ICLRSyncManager::GetMonitorOwner](iclrsyncmanager-getmonitorowner-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77597-131">Spécifications</span><span class="sxs-lookup"><span data-stu-id="77597-131">Requirements</span></span>  
 <span data-ttu-id="77597-132">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77597-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77597-133">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="77597-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="77597-134">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="77597-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="77597-135">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77597-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77597-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="77597-136">See also</span></span>

- [<span data-ttu-id="77597-137">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="77597-137">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="77597-138">IHostAutoEvent, interface</span><span class="sxs-lookup"><span data-stu-id="77597-138">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="77597-139">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="77597-139">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- <xref:System.Threading.Monitor>
