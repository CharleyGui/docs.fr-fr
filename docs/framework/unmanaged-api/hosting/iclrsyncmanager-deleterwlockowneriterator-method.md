---
title: ICLRSyncManager::DeleteRWLockOwnerIterator, méthode
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.DeleteRWLockOwnerIterator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::DeleteRWLockOwnerIterator
helpviewer_keywords:
- ICLRSyncManager::DeleteRWLockOwnerIterator method [.NET Framework hosting]
- DeleteRWLockOwnerIterator method [.NET Framework hosting]
ms.assetid: fcfd340a-b7d6-44e4-8167-2c05b789d483
topic_type:
- apiref
ms.openlocfilehash: fb02b5c941e15d172140565e8efb625234947cd7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130574"
---
# <a name="iclrsyncmanagerdeleterwlockowneriterator-method"></a><span data-ttu-id="1e12c-102">ICLRSyncManager::DeleteRWLockOwnerIterator, méthode</span><span class="sxs-lookup"><span data-stu-id="1e12c-102">ICLRSyncManager::DeleteRWLockOwnerIterator Method</span></span>
<span data-ttu-id="1e12c-103">Demande que le common language runtime (CLR) détruise un itérateur qui a été créé par un appel à [ICLRSyncManager :: CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span><span class="sxs-lookup"><span data-stu-id="1e12c-103">Requests that the common language runtime (CLR) destroy an iterator that was created by a call to [ICLRSyncManager::CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e12c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1e12c-104">Syntax</span></span>  
  
```cpp  
HRESULT DeleteRWLockOwnerIterator (  
    [in] SIZE_T  Iterator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e12c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1e12c-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="1e12c-106">dans Itérateur qui a été créé à l’aide d’un appel à `CreateRWLockOwnerIterator`.</span><span class="sxs-lookup"><span data-stu-id="1e12c-106">[in] The iterator that was created by using a call to `CreateRWLockOwnerIterator`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1e12c-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="1e12c-107">Return Value</span></span>  
  
|<span data-ttu-id="1e12c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1e12c-108">HRESULT</span></span>|<span data-ttu-id="1e12c-109">Description</span><span class="sxs-lookup"><span data-stu-id="1e12c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1e12c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1e12c-110">S_OK</span></span>|<span data-ttu-id="1e12c-111">`DeleteRWLockOwnerIterator` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="1e12c-111">`DeleteRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="1e12c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1e12c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1e12c-113">Le CLR n’a pas été chargé dans un processus ou est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="1e12c-113">The CLR has not been loaded into a process, or is in a state in which it cannot run managed code or successfully process the call.</span></span>|  
|<span data-ttu-id="1e12c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1e12c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1e12c-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="1e12c-115">The call timed out.</span></span>|  
|<span data-ttu-id="1e12c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1e12c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1e12c-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="1e12c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1e12c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1e12c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1e12c-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="1e12c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1e12c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1e12c-120">E_FAIL</span></span>|<span data-ttu-id="1e12c-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="1e12c-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1e12c-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="1e12c-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1e12c-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1e12c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e12c-124">Notes</span><span class="sxs-lookup"><span data-stu-id="1e12c-124">Remarks</span></span>  
 <span data-ttu-id="1e12c-125">L’hôte peut appeler cette méthode et `CreateRWLockOwnerIterator` pour s’assurer que son implémentation de thread reste synchronisée.</span><span class="sxs-lookup"><span data-stu-id="1e12c-125">The host can call this method and `CreateRWLockOwnerIterator` to ensure that its threading implementation remains synchronized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e12c-126">spécifications</span><span class="sxs-lookup"><span data-stu-id="1e12c-126">Requirements</span></span>  
 <span data-ttu-id="1e12c-127">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e12c-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e12c-128">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1e12c-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1e12c-129">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1e12c-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1e12c-130">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e12c-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e12c-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1e12c-131">See also</span></span>

- [<span data-ttu-id="1e12c-132">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="1e12c-132">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="1e12c-133">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="1e12c-133">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
