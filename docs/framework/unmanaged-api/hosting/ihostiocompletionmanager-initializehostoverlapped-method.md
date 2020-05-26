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
ms.openlocfilehash: cf257ab86d27946c861c89dff5e6f09a42013e58
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804712"
---
# <a name="ihostiocompletionmanagerinitializehostoverlapped-method"></a><span data-ttu-id="3cff2-102">IHostIoCompletionManager::InitializeHostOverlapped, méthode</span><span class="sxs-lookup"><span data-stu-id="3cff2-102">IHostIoCompletionManager::InitializeHostOverlapped Method</span></span>
<span data-ttu-id="3cff2-103">Fournit à l’hôte la possibilité d’initialiser toutes les données personnalisées à ajouter à une `OVERLAPPED` structure Win32 utilisée pour les demandes d’e/s asynchrones.</span><span class="sxs-lookup"><span data-stu-id="3cff2-103">Provides the host with an opportunity to initialize any custom data to append to a Win32 `OVERLAPPED` structure that is used for asynchronous I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cff2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3cff2-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeHostOverlapped (  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3cff2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3cff2-105">Parameters</span></span>  
 `pvOverlapped`  
 <span data-ttu-id="3cff2-106">dans Pointeur vers la structure Win32 `OVERLAPPED` à inclure dans la requête d’e/s.</span><span class="sxs-lookup"><span data-stu-id="3cff2-106">[in] A pointer to the Win32 `OVERLAPPED` structure to be included with the I/O request.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3cff2-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="3cff2-107">Return Value</span></span>  
  
|<span data-ttu-id="3cff2-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3cff2-108">HRESULT</span></span>|<span data-ttu-id="3cff2-109">Description</span><span class="sxs-lookup"><span data-stu-id="3cff2-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3cff2-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3cff2-110">S_OK</span></span>|<span data-ttu-id="3cff2-111">`InitializeHostOverlapped`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="3cff2-111">`InitializeHostOverlapped` returned successfully.</span></span>|  
|<span data-ttu-id="3cff2-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3cff2-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3cff2-113">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="3cff2-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3cff2-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3cff2-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3cff2-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="3cff2-115">The call timed out.</span></span>|  
|<span data-ttu-id="3cff2-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3cff2-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3cff2-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="3cff2-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3cff2-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3cff2-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3cff2-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="3cff2-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3cff2-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3cff2-120">E_FAIL</span></span>|<span data-ttu-id="3cff2-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="3cff2-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3cff2-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="3cff2-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3cff2-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3cff2-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3cff2-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="3cff2-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="3cff2-125">Mémoire disponible insuffisante pour allouer la ressource demandée.</span><span class="sxs-lookup"><span data-stu-id="3cff2-125">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3cff2-126">Notes</span><span class="sxs-lookup"><span data-stu-id="3cff2-126">Remarks</span></span>  
 <span data-ttu-id="3cff2-127">Les fonctions de la plate-forme Windows utilisent la `OVERLAPPED` structure pour stocker l’état des demandes d’e/s asynchrones.</span><span class="sxs-lookup"><span data-stu-id="3cff2-127">The Windows Platform functions use the `OVERLAPPED` structure to store state for asynchronous I/O requests.</span></span> <span data-ttu-id="3cff2-128">Le CLR appelle la `InitializeHostOverlapped` méthode pour permettre à l’hôte d’ajouter des données personnalisées à une `OVERLAPPED` instance.</span><span class="sxs-lookup"><span data-stu-id="3cff2-128">The CLR calls the `InitializeHostOverlapped` method to give the host the opportunity to append custom data to an `OVERLAPPED` instance.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3cff2-129">Pour atteindre le début de leur bloc de données personnalisé, les hôtes doivent définir le décalage sur la taille de la `OVERLAPPED` structure ( `sizeof(OVERLAPPED)` ).</span><span class="sxs-lookup"><span data-stu-id="3cff2-129">To get to the beginning of their custom data block, hosts must set the offset to the size of the `OVERLAPPED` structure (`sizeof(OVERLAPPED)`).</span></span>  
  
 <span data-ttu-id="3cff2-130">Une valeur de retour de E_OUTOFMEMORY indique que l’hôte n’a pas réussi à initialiser ses données personnalisées.</span><span class="sxs-lookup"><span data-stu-id="3cff2-130">A return value of E_OUTOFMEMORY indicates that the host has failed to initialize its custom data.</span></span> <span data-ttu-id="3cff2-131">Dans ce cas, le CLR signale une erreur et fait échouer l’appel.</span><span class="sxs-lookup"><span data-stu-id="3cff2-131">In this case, the CLR reports an error and fails the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3cff2-132">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3cff2-132">Requirements</span></span>  
 <span data-ttu-id="3cff2-133">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3cff2-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3cff2-134">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3cff2-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3cff2-135">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3cff2-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3cff2-136">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3cff2-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cff2-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3cff2-137">See also</span></span>

- [<span data-ttu-id="3cff2-138">ICLRIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="3cff2-138">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="3cff2-139">GetHostOverlappedSize, méthode</span><span class="sxs-lookup"><span data-stu-id="3cff2-139">GetHostOverlappedSize Method</span></span>](ihostiocompletionmanager-gethostoverlappedsize-method.md)
- [<span data-ttu-id="3cff2-140">IHostIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="3cff2-140">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
