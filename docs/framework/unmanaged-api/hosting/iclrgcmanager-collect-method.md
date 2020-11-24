---
title: ICLRGCManager::Collect, méthode
ms.date: 03/30/2017
api_name:
- ICLRGCManager.Collect
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager::Collect
helpviewer_keywords:
- ICLRGCManager::Collect method [.NET Framework hosting]
- Collect method, ICLRGCManager interface [.NET Framework hosting]
ms.assetid: 0c6cbbea-c27c-4695-bda3-17c1910d8ddb
topic_type:
- apiref
ms.openlocfilehash: 90ce4e888ddb3a10dd0dfd7e68463311db86742f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677763"
---
# <a name="iclrgcmanagercollect-method"></a><span data-ttu-id="b668e-102">ICLRGCManager::Collect, méthode</span><span class="sxs-lookup"><span data-stu-id="b668e-102">ICLRGCManager::Collect Method</span></span>

<span data-ttu-id="b668e-103">Force une garbage collection pour la génération spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b668e-103">Forces a garbage collection for the specified generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b668e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b668e-104">Syntax</span></span>  
  
```cpp  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b668e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b668e-105">Parameters</span></span>  

 `Generation`  
 <span data-ttu-id="b668e-106">dans Génération à collecter.</span><span class="sxs-lookup"><span data-stu-id="b668e-106">[in] The generation to collect.</span></span> <span data-ttu-id="b668e-107">La valeur-1 force une collection de toutes les générations.</span><span class="sxs-lookup"><span data-stu-id="b668e-107">A value of -1 forces a collection of all generations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b668e-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="b668e-108">Return Value</span></span>  
  
|<span data-ttu-id="b668e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b668e-109">HRESULT</span></span>|<span data-ttu-id="b668e-110">Description</span><span class="sxs-lookup"><span data-stu-id="b668e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b668e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b668e-111">S_OK</span></span>|<span data-ttu-id="b668e-112">`Collect` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="b668e-112">`Collect` returned successfully.</span></span>|  
|<span data-ttu-id="b668e-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b668e-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b668e-114">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="b668e-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b668e-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b668e-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b668e-116">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="b668e-116">The call timed out.</span></span>|  
|<span data-ttu-id="b668e-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b668e-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b668e-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="b668e-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b668e-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b668e-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b668e-120">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="b668e-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b668e-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b668e-121">E_FAIL</span></span>|<span data-ttu-id="b668e-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="b668e-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b668e-123">Une fois que la méthode a retourné E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="b668e-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b668e-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b668e-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b668e-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="b668e-125">Remarks</span></span>  

 <span data-ttu-id="b668e-126">La `Collect` méthode force le garbage collector du CLR à exécuter une collection indépendamment de son état actuel.</span><span class="sxs-lookup"><span data-stu-id="b668e-126">The `Collect` method forces the CLR's garbage collector to perform a collection regardless of its current state.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b668e-127">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b668e-127">Requirements</span></span>  

 <span data-ttu-id="b668e-128">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b668e-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b668e-129">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b668e-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b668e-130">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b668e-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b668e-131">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b668e-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b668e-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b668e-132">See also</span></span>

- [<span data-ttu-id="b668e-133">Gestion automatique de la mémoire</span><span class="sxs-lookup"><span data-stu-id="b668e-133">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="b668e-134">Garbage collection</span><span class="sxs-lookup"><span data-stu-id="b668e-134">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="b668e-135">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="b668e-135">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="b668e-136">ICLRGCManager, interface</span><span class="sxs-lookup"><span data-stu-id="b668e-136">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)
- [<span data-ttu-id="b668e-137">Interfaces d'hébergement du CLR</span><span class="sxs-lookup"><span data-stu-id="b668e-137">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="b668e-138">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="b668e-138">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="b668e-139">Hébergement</span><span class="sxs-lookup"><span data-stu-id="b668e-139">Hosting</span></span>](index.md)
