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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b6187da564a62b8c30abdc6a150f0df45d565615
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763874"
---
# <a name="ihostcontrolgethostmanager-method"></a><span data-ttu-id="c2043-102">IHostControl::GetHostManager, méthode</span><span class="sxs-lookup"><span data-stu-id="c2043-102">IHostControl::GetHostManager Method</span></span>
<span data-ttu-id="c2043-103">Obtient un pointeur d’interface vers l’implémentation de l’hôte de l’interface avec la valeur `IID`.</span><span class="sxs-lookup"><span data-stu-id="c2043-103">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2043-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c2043-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHostManager (  
    [in] REFIID riid,  
    [out, iid_is(riid)] void** ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2043-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c2043-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="c2043-106">[in] Le `IID` de l’interface que le common language runtime (CLR) effectue une requête.</span><span class="sxs-lookup"><span data-stu-id="c2043-106">[in] The `IID` of the interface that the common language runtime (CLR) is querying for.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="c2043-107">[out] Un pointeur vers l’interface implémentée par l’hôte, ou null si l’hôte ne prend pas en charge cette interface.</span><span class="sxs-lookup"><span data-stu-id="c2043-107">[out] A pointer to the host-implemented interface, or null if the host does not support this interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c2043-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c2043-108">Return Value</span></span>  
  
|<span data-ttu-id="c2043-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c2043-109">HRESULT</span></span>|<span data-ttu-id="c2043-110">Description</span><span class="sxs-lookup"><span data-stu-id="c2043-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c2043-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c2043-111">S_OK</span></span>|<span data-ttu-id="c2043-112">`GetHostManager` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="c2043-112">`GetHostManager` returned successfully.</span></span>|  
|<span data-ttu-id="c2043-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c2043-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c2043-114">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="c2043-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c2043-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c2043-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c2043-116">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="c2043-116">The call timed out.</span></span>|  
|<span data-ttu-id="c2043-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c2043-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c2043-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="c2043-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c2043-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c2043-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c2043-120">Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="c2043-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c2043-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c2043-121">E_FAIL</span></span>|<span data-ttu-id="c2043-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="c2043-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c2043-123">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus.</span><span class="sxs-lookup"><span data-stu-id="c2043-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c2043-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c2043-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c2043-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c2043-125">E_INVALIDARG</span></span>|<span data-ttu-id="c2043-126">Demandé `IID` n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="c2043-126">The requested `IID` is not valid.</span></span>|  
|<span data-ttu-id="c2043-127">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="c2043-127">E_NOINTERFACE</span></span>|<span data-ttu-id="c2043-128">L’interface demandée n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="c2043-128">The requested interface is not supported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2043-129">Notes</span><span class="sxs-lookup"><span data-stu-id="c2043-129">Remarks</span></span>  
 <span data-ttu-id="c2043-130">Le CLR interroge l’hôte pour déterminer si elle prend en charge un ou plusieurs des interfaces suivantes :</span><span class="sxs-lookup"><span data-stu-id="c2043-130">The CLR queries the host to determine whether it supports one or more of the following interfaces:</span></span>  
  
- [<span data-ttu-id="c2043-131">IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="c2043-131">IHostMemoryManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
  
- [<span data-ttu-id="c2043-132">IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="c2043-132">IHostTaskManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
  
- [<span data-ttu-id="c2043-133">IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="c2043-133">IHostThreadPoolManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
  
- [<span data-ttu-id="c2043-134">IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="c2043-134">IHostIoCompletionManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
  
- [<span data-ttu-id="c2043-135">IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="c2043-135">IHostSyncManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
  
- [<span data-ttu-id="c2043-136">IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="c2043-136">IHostAssemblyManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
  
- [<span data-ttu-id="c2043-137">IHostGCManager</span><span class="sxs-lookup"><span data-stu-id="c2043-137">IHostGCManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)  
  
- [<span data-ttu-id="c2043-138">IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="c2043-138">IHostPolicyManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
  
- [<span data-ttu-id="c2043-139">IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="c2043-139">IHostSecurityManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
  
 <span data-ttu-id="c2043-140">Si l’hôte prend en charge l’interface spécifiée, il définit `ppObject` à son implémentation de cette interface.</span><span class="sxs-lookup"><span data-stu-id="c2043-140">If the host supports the specified interface, it sets `ppObject` to its implementation of that interface.</span></span> <span data-ttu-id="c2043-141">Sinon, il définit `ppObject` avec la valeur null.</span><span class="sxs-lookup"><span data-stu-id="c2043-141">Otherwise, it sets `ppObject` to null.</span></span>  
  
 <span data-ttu-id="c2043-142">Le CLR n’appelle pas `Release` sur les gestionnaires d’hôte, même lorsque vous arrêtez.</span><span class="sxs-lookup"><span data-stu-id="c2043-142">The CLR does not call `Release` on host managers, even when you shut it down.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2043-143">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c2043-143">Requirements</span></span>  
 <span data-ttu-id="c2043-144">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2043-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2043-145">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c2043-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c2043-146">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c2043-146">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c2043-147">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2043-147">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2043-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c2043-148">See also</span></span>

- [<span data-ttu-id="c2043-149">IHostControl, interface</span><span class="sxs-lookup"><span data-stu-id="c2043-149">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
