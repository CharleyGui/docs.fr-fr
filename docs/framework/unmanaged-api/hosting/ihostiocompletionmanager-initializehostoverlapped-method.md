---
title: IHostIoCompletionManager::InitializeHostOverlapped, méthode
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.InitializeHostOverlapped
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped
helpviewer_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped method [.NET Framework hosting]
- InitializeHostOverlapped method [.NET Framework hosting]
ms.assetid: c35199bf-bc47-4901-b467-4e8a37644bbb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac7014962b99ac167e8192c13b2bae5ca92470f0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948523"
---
# <a name="ihostiocompletionmanagerinitializehostoverlapped-method"></a><span data-ttu-id="60625-102">IHostIoCompletionManager::InitializeHostOverlapped, méthode</span><span class="sxs-lookup"><span data-stu-id="60625-102">IHostIoCompletionManager::InitializeHostOverlapped Method</span></span>
<span data-ttu-id="60625-103">Fournit à l’hôte la possibilité d’initialiser toutes les données personnalisées à ajouter à `OVERLAPPED` une structure Win32 utilisée pour les demandes d’e/s asynchrones.</span><span class="sxs-lookup"><span data-stu-id="60625-103">Provides the host with an opportunity to initialize any custom data to append to a Win32 `OVERLAPPED` structure that is used for asynchronous I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60625-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60625-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeHostOverlapped (  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60625-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="60625-105">Parameters</span></span>  
 `pvOverlapped`  
 <span data-ttu-id="60625-106">dans Pointeur vers la structure Win32 `OVERLAPPED` à inclure dans la requête d’e/s.</span><span class="sxs-lookup"><span data-stu-id="60625-106">[in] A pointer to the Win32 `OVERLAPPED` structure to be included with the I/O request.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="60625-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="60625-107">Return Value</span></span>  
  
|<span data-ttu-id="60625-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="60625-108">HRESULT</span></span>|<span data-ttu-id="60625-109">Description</span><span class="sxs-lookup"><span data-stu-id="60625-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="60625-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="60625-110">S_OK</span></span>|<span data-ttu-id="60625-111">`InitializeHostOverlapped`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="60625-111">`InitializeHostOverlapped` returned successfully.</span></span>|  
|<span data-ttu-id="60625-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="60625-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="60625-113">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="60625-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="60625-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="60625-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="60625-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="60625-115">The call timed out.</span></span>|  
|<span data-ttu-id="60625-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="60625-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="60625-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="60625-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="60625-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="60625-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="60625-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="60625-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="60625-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="60625-120">E_FAIL</span></span>|<span data-ttu-id="60625-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="60625-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="60625-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="60625-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="60625-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="60625-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="60625-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="60625-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="60625-125">Mémoire disponible insuffisante pour allouer la ressource demandée.</span><span class="sxs-lookup"><span data-stu-id="60625-125">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60625-126">Notes</span><span class="sxs-lookup"><span data-stu-id="60625-126">Remarks</span></span>  
 <span data-ttu-id="60625-127">Les fonctions de la plate- `OVERLAPPED` forme Windows utilisent la structure pour stocker l’état des demandes d’e/s asynchrones.</span><span class="sxs-lookup"><span data-stu-id="60625-127">The Windows Platform functions use the `OVERLAPPED` structure to store state for asynchronous I/O requests.</span></span> <span data-ttu-id="60625-128">Le CLR appelle la `InitializeHostOverlapped` méthode pour permettre à l’hôte d’ajouter des données personnalisées à `OVERLAPPED` une instance.</span><span class="sxs-lookup"><span data-stu-id="60625-128">The CLR calls the `InitializeHostOverlapped` method to give the host the opportunity to append custom data to an `OVERLAPPED` instance.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="60625-129">Pour atteindre le début de leur bloc de données personnalisé, les hôtes doivent définir le décalage sur la taille de `OVERLAPPED` la structure`sizeof(OVERLAPPED)`().</span><span class="sxs-lookup"><span data-stu-id="60625-129">To get to the beginning of their custom data block, hosts must set the offset to the size of the `OVERLAPPED` structure (`sizeof(OVERLAPPED)`).</span></span>  
  
 <span data-ttu-id="60625-130">Une valeur de retour E_OUTOFMEMORY indique que l’hôte n’a pas réussi à initialiser ses données personnalisées.</span><span class="sxs-lookup"><span data-stu-id="60625-130">A return value of E_OUTOFMEMORY indicates that the host has failed to initialize its custom data.</span></span> <span data-ttu-id="60625-131">Dans ce cas, le CLR signale une erreur et fait échouer l’appel.</span><span class="sxs-lookup"><span data-stu-id="60625-131">In this case, the CLR reports an error and fails the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60625-132">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="60625-132">Requirements</span></span>  
 <span data-ttu-id="60625-133">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60625-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60625-134">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="60625-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="60625-135">**Bibliothèque** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="60625-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="60625-136">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60625-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60625-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="60625-137">See also</span></span>

- [<span data-ttu-id="60625-138">ICLRIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="60625-138">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="60625-139">GetHostOverlappedSize, méthode</span><span class="sxs-lookup"><span data-stu-id="60625-139">GetHostOverlappedSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)
- [<span data-ttu-id="60625-140">IHostIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="60625-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
