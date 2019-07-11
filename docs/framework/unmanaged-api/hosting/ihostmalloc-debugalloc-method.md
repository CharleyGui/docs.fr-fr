---
title: IHostMAlloc::DebugAlloc, méthode
ms.date: 03/30/2017
api_name:
- IHostMAlloc.DebugAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::DebugAlloc
helpviewer_keywords:
- DebugAlloc method [.NET Framework hosting]
- IHostMAlloc::DebugAlloc method [.NET Framework hosting]
ms.assetid: 0bfbc527-bea2-43ce-b041-69186f4440dd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f87c9c04c4d5b1d65e8c844630a6034f3c72d484
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780969"
---
# <a name="ihostmallocdebugalloc-method"></a><span data-ttu-id="987e5-102">IHostMAlloc::DebugAlloc, méthode</span><span class="sxs-lookup"><span data-stu-id="987e5-102">IHostMAlloc::DebugAlloc Method</span></span>
<span data-ttu-id="987e5-103">Demande que l’hôte alloue la quantité de mémoire spécifiée à partir du tas et en outre suivre où la mémoire a été allouée.</span><span class="sxs-lookup"><span data-stu-id="987e5-103">Requests that the host allocate the specified amount of memory from the heap, and additionally track where the memory was allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="987e5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="987e5-104">Syntax</span></span>  
  
```cpp  
HRESULT DebugAlloc (  
    [in]  SIZE_T  cbSize,   
    [in]  EMemoryCriticalLevel dwCriticalLevel,   
    [in]  char*   pszFileName,   
    [in]  int     iLineNo,   
    [out] void**  ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="987e5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="987e5-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="987e5-106">[in] La taille, en octets, de la demande d’allocation de mémoire actuelle.</span><span class="sxs-lookup"><span data-stu-id="987e5-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="987e5-107">[in] Parmi les [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) valeurs, indiquant l’impact d’un échec d’allocation.</span><span class="sxs-lookup"><span data-stu-id="987e5-107">[in] One of the [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="987e5-108">[in] Le fichier de code de l’exécutable en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="987e5-108">[in] The code file of the executable being debugged.</span></span>  
  
 `iLineNo`  
 <span data-ttu-id="987e5-109">[in] Numéro de ligne dans `pszFileName` où l’allocation a été demandée.</span><span class="sxs-lookup"><span data-stu-id="987e5-109">[in] The line number in `pszFileName` where the allocation was requested.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="987e5-110">[out] Pointeur vers la mémoire allouée, ou null si la demande n’a pas pu être effectuée.</span><span class="sxs-lookup"><span data-stu-id="987e5-110">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="987e5-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="987e5-111">Return Value</span></span>  
  
|<span data-ttu-id="987e5-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="987e5-112">HRESULT</span></span>|<span data-ttu-id="987e5-113">Description</span><span class="sxs-lookup"><span data-stu-id="987e5-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="987e5-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="987e5-114">S_OK</span></span>|<span data-ttu-id="987e5-115">`DebugAlloc` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="987e5-115">`DebugAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="987e5-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="987e5-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="987e5-117">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="987e5-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="987e5-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="987e5-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="987e5-119">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="987e5-119">The call timed out.</span></span>|  
|<span data-ttu-id="987e5-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="987e5-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="987e5-121">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="987e5-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="987e5-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="987e5-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="987e5-123">Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="987e5-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="987e5-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="987e5-124">E_FAIL</span></span>|<span data-ttu-id="987e5-125">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="987e5-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="987e5-126">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus.</span><span class="sxs-lookup"><span data-stu-id="987e5-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="987e5-127">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="987e5-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="987e5-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="987e5-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="987e5-129">Mémoire était insuffisante pour terminer la demande d’allocation.</span><span class="sxs-lookup"><span data-stu-id="987e5-129">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="987e5-130">Notes</span><span class="sxs-lookup"><span data-stu-id="987e5-130">Remarks</span></span>  
 <span data-ttu-id="987e5-131">Le CLR obtient un pointeur d’interface vers un [IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance en appelant le [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="987e5-131">The CLR gets an interface pointer to an [IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span> <span data-ttu-id="987e5-132">`DebugAlloc` permet au runtime obtenir des informations de fichier de code pour une utilisation pendant le débogage.</span><span class="sxs-lookup"><span data-stu-id="987e5-132">`DebugAlloc` allows the runtime to get code file information for use during debugging.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="987e5-133">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="987e5-133">Requirements</span></span>  
 <span data-ttu-id="987e5-134">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="987e5-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="987e5-135">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="987e5-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="987e5-136">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="987e5-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="987e5-137">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="987e5-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="987e5-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="987e5-138">See also</span></span>

- [<span data-ttu-id="987e5-139">IHostMemoryManager, interface</span><span class="sxs-lookup"><span data-stu-id="987e5-139">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="987e5-140">IHostMalloc, interface</span><span class="sxs-lookup"><span data-stu-id="987e5-140">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
