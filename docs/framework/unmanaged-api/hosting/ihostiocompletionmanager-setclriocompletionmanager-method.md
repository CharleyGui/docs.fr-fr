---
title: IHostIoCompletionManager::SetCLRIoCompletionManager, méthode
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.SetCLRIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::SetCLRIoCompletionManager
helpviewer_keywords:
- IHostIoCompletionManager::SetCLRIoCompletionManager method [.NET Framework hosting]
- SetCLRIoCompletionManager method [.NET Framework hosting]
ms.assetid: 4254bb01-3a14-4f34-a3be-60ff1f5072b5
topic_type:
- apiref
ms.openlocfilehash: b84e92ca356ad83421d788a732926b614ffa4a8c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133788"
---
# <a name="ihostiocompletionmanagersetclriocompletionmanager-method"></a><span data-ttu-id="e2f95-102">IHostIoCompletionManager::SetCLRIoCompletionManager, méthode</span><span class="sxs-lookup"><span data-stu-id="e2f95-102">IHostIoCompletionManager::SetCLRIoCompletionManager Method</span></span>
<span data-ttu-id="e2f95-103">Fournit à l’hôte un pointeur d’interface vers l’instance [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) implémentée par le Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="e2f95-103">Provides the host with an interface pointer to the [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2f95-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e2f95-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRIoCompletionManager (  
    [in] ICLRIoCompletionManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e2f95-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e2f95-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="e2f95-106">dans Pointeur d’interface vers une instance de `ICLRIoCompletionManager` fournie par le CLR.</span><span class="sxs-lookup"><span data-stu-id="e2f95-106">[in] An interface pointer to an `ICLRIoCompletionManager` instance provided by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e2f95-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e2f95-107">Return Value</span></span>  
  
|<span data-ttu-id="e2f95-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e2f95-108">HRESULT</span></span>|<span data-ttu-id="e2f95-109">Description</span><span class="sxs-lookup"><span data-stu-id="e2f95-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e2f95-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e2f95-110">S_OK</span></span>|<span data-ttu-id="e2f95-111">`SetCLRIoCompletionManager` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="e2f95-111">`SetCLRIoCompletionManager` returned successfully.</span></span>|  
|<span data-ttu-id="e2f95-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e2f95-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e2f95-113">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="e2f95-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e2f95-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e2f95-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e2f95-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="e2f95-115">The call timed out.</span></span>|  
|<span data-ttu-id="e2f95-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e2f95-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e2f95-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="e2f95-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e2f95-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e2f95-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e2f95-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="e2f95-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e2f95-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e2f95-120">E_FAIL</span></span>|<span data-ttu-id="e2f95-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="e2f95-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e2f95-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="e2f95-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e2f95-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e2f95-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2f95-124">Notes</span><span class="sxs-lookup"><span data-stu-id="e2f95-124">Remarks</span></span>  
 <span data-ttu-id="e2f95-125">Une fois que le CLR a appelé `SetCLRIoCompletionManager`, l’hôte doit appeler [ICLRIoCompletionManager :: OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) pour notifier le CLR lorsqu’une demande d’e/s est terminée.</span><span class="sxs-lookup"><span data-stu-id="e2f95-125">After the CLR has called `SetCLRIoCompletionManager`, the host must call [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) to notify the CLR when an I/O request has been completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2f95-126">spécifications</span><span class="sxs-lookup"><span data-stu-id="e2f95-126">Requirements</span></span>  
 <span data-ttu-id="e2f95-127">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2f95-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2f95-128">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e2f95-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e2f95-129">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e2f95-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e2f95-130">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2f95-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2f95-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e2f95-131">See also</span></span>

- [<span data-ttu-id="e2f95-132">ICLRIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="e2f95-132">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="e2f95-133">IHostIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="e2f95-133">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
