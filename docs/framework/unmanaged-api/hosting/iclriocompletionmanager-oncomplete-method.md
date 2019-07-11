---
title: ICLRIoCompletionManager::OnComplete, méthode
ms.date: 03/30/2017
api_name:
- ICLRIoCompletionManager.OnComplete
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRIoCompletionManager::OnComplete
helpviewer_keywords:
- OnComplete method [.NET Framework hosting]
- ICLRIoCompletionManager::OnComplete method [.NET Framework hosting]
ms.assetid: 003f6974-9727-4322-bed5-e330d1224d0b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9c3d4674280bf5aa459fec2b195c3164c75c6c3d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779630"
---
# <a name="iclriocompletionmanageroncomplete-method"></a><span data-ttu-id="71ad5-102">ICLRIoCompletionManager::OnComplete, méthode</span><span class="sxs-lookup"><span data-stu-id="71ad5-102">ICLRIoCompletionManager::OnComplete Method</span></span>
<span data-ttu-id="71ad5-103">Notifie le common language runtime (CLR) de l’état d’une requête d’e/s qui a été effectuée à l’aide d’un appel à la [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="71ad5-103">Notifies the common language runtime (CLR) of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71ad5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="71ad5-104">Syntax</span></span>  
  
```cpp  
HRESULT OnComplete (  
    [in] DWORD dwErrorCode,  
    [in] DWORD NumberOfBytesTransferred,  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="71ad5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="71ad5-105">Parameters</span></span>  
 `dwErrorCode`  
 <span data-ttu-id="71ad5-106">[in] Valeur HRESULT qui indique l’état de l’opération de liaison.</span><span class="sxs-lookup"><span data-stu-id="71ad5-106">[in] An HRESULT value that indicates the status of the bind operation.</span></span>  
  
- <span data-ttu-id="71ad5-107">S_OK indique que l’opération a réussi.</span><span class="sxs-lookup"><span data-stu-id="71ad5-107">S_OK indicates that the operation completed successfully.</span></span>  
  
- <span data-ttu-id="71ad5-108">HOST_E_INTERRUPTED indique que l’appel s’est arrêté avant la fin.</span><span class="sxs-lookup"><span data-stu-id="71ad5-108">HOST_E_INTERRUPTED indicates that the call terminated before completion.</span></span>  
  
- <span data-ttu-id="71ad5-109">E_FAIL indique qu’une défaillance grave, irrécupérable et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="71ad5-109">E_FAIL indicates that an unknown, unrecoverable, catastrophic failure occurred.</span></span>  
  
 `NumberOfBytesTransferred`  
 <span data-ttu-id="71ad5-110">[in] Le nombre d’octets transférés pendant le traitement de la demande d’e/s.</span><span class="sxs-lookup"><span data-stu-id="71ad5-110">[in] The number of bytes transferred during the processing of the I/O request.</span></span>  
  
 `pvOverlapped`  
 <span data-ttu-id="71ad5-111">[in] Un pointeur vers le `OVERLAPPED` structure qui a été passée à l’appel à la `IHostIoCompletionManager::Bind` (méthode).</span><span class="sxs-lookup"><span data-stu-id="71ad5-111">[in] A pointer to the `OVERLAPPED` structure that was passed to the call to the `IHostIoCompletionManager::Bind` method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="71ad5-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="71ad5-112">Return Value</span></span>  
  
|<span data-ttu-id="71ad5-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="71ad5-113">HRESULT</span></span>|<span data-ttu-id="71ad5-114">Description</span><span class="sxs-lookup"><span data-stu-id="71ad5-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="71ad5-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="71ad5-115">S_OK</span></span>|<span data-ttu-id="71ad5-116">`OnComplete` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="71ad5-116">`OnComplete` returned successfully.</span></span>|  
|<span data-ttu-id="71ad5-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="71ad5-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="71ad5-118">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="71ad5-118">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="71ad5-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="71ad5-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="71ad5-120">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="71ad5-120">The call timed out.</span></span>|  
|<span data-ttu-id="71ad5-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="71ad5-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="71ad5-122">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="71ad5-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="71ad5-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="71ad5-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="71ad5-124">Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="71ad5-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="71ad5-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="71ad5-125">E_FAIL</span></span>|<span data-ttu-id="71ad5-126">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="71ad5-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="71ad5-127">Une fois une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus.</span><span class="sxs-lookup"><span data-stu-id="71ad5-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="71ad5-128">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="71ad5-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71ad5-129">Notes</span><span class="sxs-lookup"><span data-stu-id="71ad5-129">Remarks</span></span>  
 <span data-ttu-id="71ad5-130">Si l’hôte implémente une abstraction de terminaison d’e/s, le CLR effectue des requêtes d’e/s via l’hôte à l’aide de méthodes de [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="71ad5-130">If the host implements an I/O completion abstraction, the CLR makes I/O requests through the host by using methods of [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md).</span></span> <span data-ttu-id="71ad5-131">L’hôte appelle ensuite la `OnComplete` méthode pour informer le runtime du résultat de ces demandes.</span><span class="sxs-lookup"><span data-stu-id="71ad5-131">The host then calls the `OnComplete` method to notify the runtime of the outcome of such requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71ad5-132">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="71ad5-132">Requirements</span></span>  
 <span data-ttu-id="71ad5-133">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71ad5-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71ad5-134">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="71ad5-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="71ad5-135">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="71ad5-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="71ad5-136">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71ad5-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71ad5-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="71ad5-137">See also</span></span>

- [<span data-ttu-id="71ad5-138">ICLRIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="71ad5-138">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="71ad5-139">IHostIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="71ad5-139">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="71ad5-140">IHostThreadPoolManager, interface</span><span class="sxs-lookup"><span data-stu-id="71ad5-140">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
