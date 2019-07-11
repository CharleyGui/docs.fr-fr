---
title: IHostTaskManager::SetCLRTaskManager, méthode
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetCLRTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetCLRTaskManager
helpviewer_keywords:
- IHostTaskManager::SetCLRTaskManager method [.NET Framework hosting]
- SetCLRTaskManager method [.NET Framework hosting]
ms.assetid: ec90ee83-bd4b-408b-9274-62a923ab86a1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc5008461acc3b0653c53cee70cbfe89c90a440b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749397"
---
# <a name="ihosttaskmanagersetclrtaskmanager-method"></a><span data-ttu-id="816dc-102">IHostTaskManager::SetCLRTaskManager, méthode</span><span class="sxs-lookup"><span data-stu-id="816dc-102">IHostTaskManager::SetCLRTaskManager Method</span></span>
<span data-ttu-id="816dc-103">Fournit à l’hôte avec un pointeur d’interface vers un [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) instance implémentée par le common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="816dc-103">Provides the host with an interface pointer to an [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="816dc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="816dc-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRTaskManager (  
    [in] ICLRTaskManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="816dc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="816dc-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="816dc-106">[in] Un pointeur vers un `ICLRTaskManager` instance implémentée par le common language runtime.</span><span class="sxs-lookup"><span data-stu-id="816dc-106">[in] A pointer to an `ICLRTaskManager` instance implemented by the common language runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="816dc-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="816dc-107">Return Value</span></span>  
  
|<span data-ttu-id="816dc-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="816dc-108">HRESULT</span></span>|<span data-ttu-id="816dc-109">Description</span><span class="sxs-lookup"><span data-stu-id="816dc-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="816dc-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="816dc-110">S_OK</span></span>|<span data-ttu-id="816dc-111">`SetCLRTaskManager` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="816dc-111">`SetCLRTaskManager` returned successfully.</span></span>|  
|<span data-ttu-id="816dc-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="816dc-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="816dc-113">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="816dc-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="816dc-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="816dc-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="816dc-115">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="816dc-115">The call timed out.</span></span>|  
|<span data-ttu-id="816dc-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="816dc-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="816dc-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="816dc-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="816dc-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="816dc-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="816dc-119">Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="816dc-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="816dc-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="816dc-120">E_FAIL</span></span>|<span data-ttu-id="816dc-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="816dc-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="816dc-122">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus.</span><span class="sxs-lookup"><span data-stu-id="816dc-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="816dc-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="816dc-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="816dc-124">Notes</span><span class="sxs-lookup"><span data-stu-id="816dc-124">Remarks</span></span>  
 <span data-ttu-id="816dc-125">Le runtime appelle `SetCLRTaskManager` pour fournir l’hôte avec un pointeur d’interface vers un `ICLRTaskManager` instance.</span><span class="sxs-lookup"><span data-stu-id="816dc-125">The runtime calls `SetCLRTaskManager` to provide the host with an interface pointer to an `ICLRTaskManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="816dc-126">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="816dc-126">Requirements</span></span>  
 <span data-ttu-id="816dc-127">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="816dc-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="816dc-128">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="816dc-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="816dc-129">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="816dc-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="816dc-130">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="816dc-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="816dc-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="816dc-131">See also</span></span>

- [<span data-ttu-id="816dc-132">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="816dc-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="816dc-133">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="816dc-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="816dc-134">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="816dc-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="816dc-135">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="816dc-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
