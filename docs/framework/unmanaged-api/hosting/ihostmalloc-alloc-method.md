---
title: IHostMAlloc::Alloc, méthode
ms.date: 03/30/2017
api_name:
- IHostMAlloc.Alloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::Alloc
helpviewer_keywords:
- Alloc method, IHostMAlloc interface [.NET Framework hosting]
- IHostMAlloc::Alloc method [.NET Framework hosting]
ms.assetid: a3007f5e-d75d-4b37-842b-704e9edced5e
topic_type:
- apiref
ms.openlocfilehash: dded37fdef02963f60883b289462aa6a96693b3d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176303"
---
# <a name="ihostmallocalloc-method"></a><span data-ttu-id="2ff0c-102">IHostMAlloc::Alloc, méthode</span><span class="sxs-lookup"><span data-stu-id="2ff0c-102">IHostMAlloc::Alloc Method</span></span>
<span data-ttu-id="2ff0c-103">Demande que l’hôte alloue la quantité spécifiée de mémoire du tas.</span><span class="sxs-lookup"><span data-stu-id="2ff0c-103">Requests that the host allocate the specified amount of memory from the heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ff0c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ff0c-104">Syntax</span></span>  
  
```cpp  
HRESULT Alloc (  
    [in] SIZE_T  cbSize,
    [in] EMemoryCriticalLevel dwCriticalLevel,
    [out] void** ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ff0c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ff0c-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="2ff0c-106">[dans] La taille, dans les octets, de la demande actuelle d’allocation de mémoire.</span><span class="sxs-lookup"><span data-stu-id="2ff0c-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="2ff0c-107">[dans] L’une des valeurs [EMemoryCriticalLevel,](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) indiquant l’impact d’une défaillance de l’allocation.</span><span class="sxs-lookup"><span data-stu-id="2ff0c-107">[in] One of the [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="2ff0c-108">[out] Un pointeur à la mémoire allouée, ou nul si la demande ne pouvait pas être complétée.</span><span class="sxs-lookup"><span data-stu-id="2ff0c-108">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2ff0c-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="2ff0c-109">Return Value</span></span>  
  
|<span data-ttu-id="2ff0c-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2ff0c-110">HRESULT</span></span>|<span data-ttu-id="2ff0c-111">Description</span><span class="sxs-lookup"><span data-stu-id="2ff0c-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2ff0c-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="2ff0c-112">S_OK</span></span>|<span data-ttu-id="2ff0c-113">`Alloc`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="2ff0c-113">`Alloc` returned successfully.</span></span>|  
|<span data-ttu-id="2ff0c-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2ff0c-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2ff0c-115">L’heure courante de l’exécution de la langue (CLR) n’a pas été chargée dans un processus, ou le CLR est dans un état où il ne peut pas exécuter le code géré ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="2ff0c-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2ff0c-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2ff0c-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2ff0c-117">L’appel s’est fait chronométrer.</span><span class="sxs-lookup"><span data-stu-id="2ff0c-117">The call timed out.</span></span>|  
|<span data-ttu-id="2ff0c-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2ff0c-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2ff0c-119">L’appelant n’est pas propriétaire de la serrure.</span><span class="sxs-lookup"><span data-stu-id="2ff0c-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2ff0c-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2ff0c-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2ff0c-121">Un événement a été annulé alors qu’un fil bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="2ff0c-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2ff0c-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2ff0c-122">E_FAIL</span></span>|<span data-ttu-id="2ff0c-123">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="2ff0c-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2ff0c-124">Lorsqu’une méthode revient E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="2ff0c-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2ff0c-125">Les appels ultérieurs aux méthodes d’hébergement reviennent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2ff0c-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2ff0c-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="2ff0c-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="2ff0c-127">Il n’y avait pas assez de mémoire disponible pour remplir la demande d’allocation.</span><span class="sxs-lookup"><span data-stu-id="2ff0c-127">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ff0c-128">Notes </span><span class="sxs-lookup"><span data-stu-id="2ff0c-128">Remarks</span></span>  
 <span data-ttu-id="2ff0c-129">Le CLR obtient un `IHostMalloc` pointeur d’interface à une instance en appelant le [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) méthode.</span><span class="sxs-lookup"><span data-stu-id="2ff0c-129">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ff0c-130">Spécifications</span><span class="sxs-lookup"><span data-stu-id="2ff0c-130">Requirements</span></span>  
 <span data-ttu-id="2ff0c-131">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ff0c-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ff0c-132">**En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor</span><span class="sxs-lookup"><span data-stu-id="2ff0c-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2ff0c-133">**Bibliothèque:** Inclus comme une ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2ff0c-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2ff0c-134">**.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ff0c-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ff0c-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2ff0c-135">See also</span></span>

- [<span data-ttu-id="2ff0c-136">IHostMemoryManager, interface</span><span class="sxs-lookup"><span data-stu-id="2ff0c-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="2ff0c-137">IHostMalloc, interface</span><span class="sxs-lookup"><span data-stu-id="2ff0c-137">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
