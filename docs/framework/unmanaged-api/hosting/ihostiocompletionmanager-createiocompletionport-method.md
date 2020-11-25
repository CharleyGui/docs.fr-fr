---
title: IHostIoCompletionManager::CreateIoCompletionPort, méthode
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.CreateIoCompletionPort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::CreateIoCompletionPort
helpviewer_keywords:
- IHostIoCompletionManager::CreateIoCompletionPort method [.NET Framework hosting]
- CreateIoCompletionPort method [.NET Framework hosting]
ms.assetid: 907a2b43-68db-44a7-acac-89e792e7bb3c
topic_type:
- apiref
ms.openlocfilehash: 0c74e073d55ab7dc98620052a0cfd68c294f7a1c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724271"
---
# <a name="ihostiocompletionmanagercreateiocompletionport-method"></a><span data-ttu-id="21f6f-102">IHostIoCompletionManager::CreateIoCompletionPort, méthode</span><span class="sxs-lookup"><span data-stu-id="21f6f-102">IHostIoCompletionManager::CreateIoCompletionPort Method</span></span>

<span data-ttu-id="21f6f-103">Demande que l’hôte crée un port de terminaison d’e/s.</span><span class="sxs-lookup"><span data-stu-id="21f6f-103">Requests that the host create a new I/O completion port.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21f6f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21f6f-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateIoCompletionPort (  
    [out] HANDLE *phPort  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21f6f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="21f6f-105">Parameters</span></span>  

 `phPort`  
 <span data-ttu-id="21f6f-106">à Pointeur vers un handle vers le port de terminaison d’e/s nouvellement créé, ou 0 (zéro), si le port n’a pas pu être créé.</span><span class="sxs-lookup"><span data-stu-id="21f6f-106">[out] A pointer to a handle to the newly created I/O completion port, or 0 (zero), if the port could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="21f6f-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="21f6f-107">Return Value</span></span>  
  
|<span data-ttu-id="21f6f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="21f6f-108">HRESULT</span></span>|<span data-ttu-id="21f6f-109">Description</span><span class="sxs-lookup"><span data-stu-id="21f6f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="21f6f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="21f6f-110">S_OK</span></span>|<span data-ttu-id="21f6f-111">`CreateIoCompletionPort` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="21f6f-111">`CreateIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="21f6f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="21f6f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="21f6f-113">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="21f6f-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="21f6f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="21f6f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="21f6f-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="21f6f-115">The call timed out.</span></span>|  
|<span data-ttu-id="21f6f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="21f6f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="21f6f-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="21f6f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="21f6f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="21f6f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="21f6f-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="21f6f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="21f6f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="21f6f-120">E_FAIL</span></span>|<span data-ttu-id="21f6f-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="21f6f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="21f6f-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="21f6f-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="21f6f-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="21f6f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="21f6f-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="21f6f-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="21f6f-125">Mémoire disponible insuffisante pour allouer la ressource demandée.</span><span class="sxs-lookup"><span data-stu-id="21f6f-125">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21f6f-126">Remarques</span><span class="sxs-lookup"><span data-stu-id="21f6f-126">Remarks</span></span>  

 <span data-ttu-id="21f6f-127">Le CLR appelle la `CreateIoCompletionPort` méthode pour demander que l’hôte crée un port de terminaison d’e/s.</span><span class="sxs-lookup"><span data-stu-id="21f6f-127">The CLR calls the `CreateIoCompletionPort` method to request that the host create a new I/O completion port.</span></span> <span data-ttu-id="21f6f-128">Il lie les opérations d’e/s à ce port via un appel à la méthode [IHostIoCompletionManager :: bind](ihostiocompletionmanager-bind-method.md) .</span><span class="sxs-lookup"><span data-stu-id="21f6f-128">It binds I/O operations to this port through a call to the [IHostIoCompletionManager::Bind](ihostiocompletionmanager-bind-method.md) method.</span></span> <span data-ttu-id="21f6f-129">L’hôte signale l’État au CLR en appelant [ICLRIoCompletionManager :: OnComplete](iclriocompletionmanager-oncomplete-method.md).</span><span class="sxs-lookup"><span data-stu-id="21f6f-129">The host reports status back to the CLR by calling [ICLRIoCompletionManager::OnComplete](iclriocompletionmanager-oncomplete-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21f6f-130">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="21f6f-130">Requirements</span></span>  

 <span data-ttu-id="21f6f-131">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21f6f-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21f6f-132">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="21f6f-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="21f6f-133">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="21f6f-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="21f6f-134">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21f6f-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21f6f-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21f6f-135">See also</span></span>

- [<span data-ttu-id="21f6f-136">ICLRIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="21f6f-136">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="21f6f-137">IHostIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="21f6f-137">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
