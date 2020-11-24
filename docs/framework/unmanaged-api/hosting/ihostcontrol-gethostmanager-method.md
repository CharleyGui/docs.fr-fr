---
title: IHostControl::GetHostManager, méthode
ms.date: 03/30/2017
api_name:
- IHostControl.GetHostManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl::GetHostManager
helpviewer_keywords:
- GetHostManager method [.NET Framework hosting]
- IHostControl::GetHostManager method [.NET Framework hosting]
ms.assetid: 0fa34bca-ed18-4626-9e78-d33684d18edb
topic_type:
- apiref
ms.openlocfilehash: e340dcb5dc093f965e6c08a24a3d65ed0aa6e07a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680820"
---
# <a name="ihostcontrolgethostmanager-method"></a><span data-ttu-id="21e42-102">IHostControl::GetHostManager, méthode</span><span class="sxs-lookup"><span data-stu-id="21e42-102">IHostControl::GetHostManager Method</span></span>

<span data-ttu-id="21e42-103">Obtient un pointeur d’interface vers l’implémentation de l’hôte de l’interface avec le spécifié `IID` .</span><span class="sxs-lookup"><span data-stu-id="21e42-103">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21e42-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21e42-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHostManager (  
    [in] REFIID riid,  
    [out, iid_is(riid)] void** ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21e42-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="21e42-105">Parameters</span></span>  

 `riid`  
 <span data-ttu-id="21e42-106">dans `IID` De l’interface pour laquelle le Common Language Runtime (CLR) interroge.</span><span class="sxs-lookup"><span data-stu-id="21e42-106">[in] The `IID` of the interface that the common language runtime (CLR) is querying for.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="21e42-107">à Pointeur vers l’interface implémentée par l’hôte, ou null si l’hôte ne prend pas en charge cette interface.</span><span class="sxs-lookup"><span data-stu-id="21e42-107">[out] A pointer to the host-implemented interface, or null if the host does not support this interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="21e42-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="21e42-108">Return Value</span></span>  
  
|<span data-ttu-id="21e42-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="21e42-109">HRESULT</span></span>|<span data-ttu-id="21e42-110">Description</span><span class="sxs-lookup"><span data-stu-id="21e42-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="21e42-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="21e42-111">S_OK</span></span>|<span data-ttu-id="21e42-112">`GetHostManager` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="21e42-112">`GetHostManager` returned successfully.</span></span>|  
|<span data-ttu-id="21e42-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="21e42-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="21e42-114">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="21e42-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="21e42-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="21e42-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="21e42-116">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="21e42-116">The call timed out.</span></span>|  
|<span data-ttu-id="21e42-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="21e42-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="21e42-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="21e42-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="21e42-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="21e42-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="21e42-120">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="21e42-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="21e42-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="21e42-121">E_FAIL</span></span>|<span data-ttu-id="21e42-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="21e42-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="21e42-123">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="21e42-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="21e42-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="21e42-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="21e42-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="21e42-125">E_INVALIDARG</span></span>|<span data-ttu-id="21e42-126">Le demandé `IID` n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="21e42-126">The requested `IID` is not valid.</span></span>|  
|<span data-ttu-id="21e42-127">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="21e42-127">E_NOINTERFACE</span></span>|<span data-ttu-id="21e42-128">L’interface demandée n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="21e42-128">The requested interface is not supported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21e42-129">Remarques</span><span class="sxs-lookup"><span data-stu-id="21e42-129">Remarks</span></span>  

 <span data-ttu-id="21e42-130">Le CLR interroge l’hôte pour déterminer s’il prend en charge une ou plusieurs des interfaces suivantes :</span><span class="sxs-lookup"><span data-stu-id="21e42-130">The CLR queries the host to determine whether it supports one or more of the following interfaces:</span></span>  
  
- [<span data-ttu-id="21e42-131">IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="21e42-131">IHostMemoryManager</span></span>](ihostmemorymanager-interface.md)  
  
- [<span data-ttu-id="21e42-132">IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="21e42-132">IHostTaskManager</span></span>](ihosttaskmanager-interface.md)  
  
- [<span data-ttu-id="21e42-133">IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="21e42-133">IHostThreadPoolManager</span></span>](ihostthreadpoolmanager-interface.md)  
  
- [<span data-ttu-id="21e42-134">IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="21e42-134">IHostIoCompletionManager</span></span>](ihostiocompletionmanager-interface.md)  
  
- [<span data-ttu-id="21e42-135">IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="21e42-135">IHostSyncManager</span></span>](ihostsyncmanager-interface.md)  
  
- [<span data-ttu-id="21e42-136">IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="21e42-136">IHostAssemblyManager</span></span>](ihostassemblymanager-interface.md)  
  
- [<span data-ttu-id="21e42-137">IHostGCManager</span><span class="sxs-lookup"><span data-stu-id="21e42-137">IHostGCManager</span></span>](ihostgcmanager-interface.md)  
  
- [<span data-ttu-id="21e42-138">IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="21e42-138">IHostPolicyManager</span></span>](ihostpolicymanager-interface.md)  
  
- [<span data-ttu-id="21e42-139">IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="21e42-139">IHostSecurityManager</span></span>](ihostsecuritymanager-interface.md)  
  
 <span data-ttu-id="21e42-140">Si l’hôte prend en charge l’interface spécifiée, il définit `ppObject` à son implémentation de cette interface.</span><span class="sxs-lookup"><span data-stu-id="21e42-140">If the host supports the specified interface, it sets `ppObject` to its implementation of that interface.</span></span> <span data-ttu-id="21e42-141">Dans le cas contraire, elle définit `ppObject` sur la valeur null.</span><span class="sxs-lookup"><span data-stu-id="21e42-141">Otherwise, it sets `ppObject` to null.</span></span>  
  
 <span data-ttu-id="21e42-142">Le CLR n’appelle pas `Release` sur les gestionnaires d’ordinateurs hôtes, même lorsque vous l’arrêtez.</span><span class="sxs-lookup"><span data-stu-id="21e42-142">The CLR does not call `Release` on host managers, even when you shut it down.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21e42-143">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="21e42-143">Requirements</span></span>  

 <span data-ttu-id="21e42-144">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21e42-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21e42-145">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="21e42-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="21e42-146">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="21e42-146">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="21e42-147">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21e42-147">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21e42-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21e42-148">See also</span></span>

- [<span data-ttu-id="21e42-149">IHostControl, interface</span><span class="sxs-lookup"><span data-stu-id="21e42-149">IHostControl Interface</span></span>](ihostcontrol-interface.md)
