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
ms.openlocfilehash: 20ad5485b8603cc7de1c27c00d53c8939871d525
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178039"
---
# <a name="ihostmallocdebugalloc-method"></a><span data-ttu-id="5b9d1-102">IHostMAlloc::DebugAlloc, méthode</span><span class="sxs-lookup"><span data-stu-id="5b9d1-102">IHostMAlloc::DebugAlloc Method</span></span>
<span data-ttu-id="5b9d1-103">Demande que l’hôte alloue la quantité spécifiée de mémoire du tas, et en outre suivre où la mémoire a été allouée.</span><span class="sxs-lookup"><span data-stu-id="5b9d1-103">Requests that the host allocate the specified amount of memory from the heap, and additionally track where the memory was allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b9d1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b9d1-104">Syntax</span></span>  
  
```cpp  
HRESULT DebugAlloc (  
    [in]  SIZE_T  cbSize,
    [in]  EMemoryCriticalLevel dwCriticalLevel,
    [in]  char*   pszFileName,
    [in]  int     iLineNo,
    [out] void**  ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b9d1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5b9d1-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="5b9d1-106">[dans] La taille, dans les octets, de la demande actuelle d’allocation de mémoire.</span><span class="sxs-lookup"><span data-stu-id="5b9d1-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="5b9d1-107">[dans] L’une des valeurs [EMemoryCriticalLevel,](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) indiquant l’impact d’une défaillance de l’allocation.</span><span class="sxs-lookup"><span data-stu-id="5b9d1-107">[in] One of the [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="5b9d1-108">[dans] Le fichier de code de l’exécutable étant débogé.</span><span class="sxs-lookup"><span data-stu-id="5b9d1-108">[in] The code file of the executable being debugged.</span></span>  
  
 `iLineNo`  
 <span data-ttu-id="5b9d1-109">[dans] Le numéro `pszFileName` de ligne dans lequel l’allocation a été demandée.</span><span class="sxs-lookup"><span data-stu-id="5b9d1-109">[in] The line number in `pszFileName` where the allocation was requested.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="5b9d1-110">[out] Un pointeur à la mémoire allouée, ou nul si la demande ne pouvait pas être complétée.</span><span class="sxs-lookup"><span data-stu-id="5b9d1-110">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5b9d1-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="5b9d1-111">Return Value</span></span>  
  
|<span data-ttu-id="5b9d1-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5b9d1-112">HRESULT</span></span>|<span data-ttu-id="5b9d1-113">Description</span><span class="sxs-lookup"><span data-stu-id="5b9d1-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5b9d1-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="5b9d1-114">S_OK</span></span>|<span data-ttu-id="5b9d1-115">`DebugAlloc`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="5b9d1-115">`DebugAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="5b9d1-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5b9d1-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5b9d1-117">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un état dans lequel il ne peut pas exécuter le code géré ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="5b9d1-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5b9d1-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5b9d1-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5b9d1-119">L’appel s’est fait chronométrer.</span><span class="sxs-lookup"><span data-stu-id="5b9d1-119">The call timed out.</span></span>|  
|<span data-ttu-id="5b9d1-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5b9d1-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5b9d1-121">L’appelant n’est pas propriétaire de la serrure.</span><span class="sxs-lookup"><span data-stu-id="5b9d1-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5b9d1-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5b9d1-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5b9d1-123">Un événement a été annulé alors qu’un fil bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="5b9d1-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5b9d1-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5b9d1-124">E_FAIL</span></span>|<span data-ttu-id="5b9d1-125">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="5b9d1-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5b9d1-126">Lorsqu’une méthode revient E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="5b9d1-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5b9d1-127">Les appels ultérieurs aux méthodes d’hébergement reviennent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5b9d1-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5b9d1-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="5b9d1-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="5b9d1-129">Il n’y avait pas assez de mémoire disponible pour remplir la demande d’allocation.</span><span class="sxs-lookup"><span data-stu-id="5b9d1-129">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b9d1-130">Notes </span><span class="sxs-lookup"><span data-stu-id="5b9d1-130">Remarks</span></span>  
 <span data-ttu-id="5b9d1-131">Le CLR obtient un pointeur d’interface à une instance [IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) en appelant le [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) méthode.</span><span class="sxs-lookup"><span data-stu-id="5b9d1-131">The CLR gets an interface pointer to an [IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span> <span data-ttu-id="5b9d1-132">`DebugAlloc`permet au temps d’exécution d’obtenir des informations de fichier de code pour une utilisation pendant le débogage.</span><span class="sxs-lookup"><span data-stu-id="5b9d1-132">`DebugAlloc` allows the runtime to get code file information for use during debugging.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b9d1-133">Spécifications</span><span class="sxs-lookup"><span data-stu-id="5b9d1-133">Requirements</span></span>  
 <span data-ttu-id="5b9d1-134">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b9d1-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b9d1-135">**En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor</span><span class="sxs-lookup"><span data-stu-id="5b9d1-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5b9d1-136">**Bibliothèque:** Inclus comme une ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5b9d1-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5b9d1-137">**.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b9d1-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b9d1-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5b9d1-138">See also</span></span>

- [<span data-ttu-id="5b9d1-139">IHostMemoryManager, interface</span><span class="sxs-lookup"><span data-stu-id="5b9d1-139">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="5b9d1-140">IHostMalloc, interface</span><span class="sxs-lookup"><span data-stu-id="5b9d1-140">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
