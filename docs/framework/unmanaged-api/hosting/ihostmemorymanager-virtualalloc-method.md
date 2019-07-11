---
title: IHostMemoryManager::VirtualAlloc, méthode
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualAlloc
helpviewer_keywords:
- VirtualAlloc method [.NET Framework hosting]
- IHostMemoryManager::VirtualAlloc method [.NET Framework hosting]
ms.assetid: 4dff3646-a050-4bd9-ac31-fe307e8637ec
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9a0764cb212a95412a4dcf9455b7648ee863951e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767668"
---
# <a name="ihostmemorymanagervirtualalloc-method"></a><span data-ttu-id="73a9c-102">IHostMemoryManager::VirtualAlloc, méthode</span><span class="sxs-lookup"><span data-stu-id="73a9c-102">IHostMemoryManager::VirtualAlloc Method</span></span>
<span data-ttu-id="73a9c-103">Sert de wrapper logique pour la fonction Win32 correspondante.</span><span class="sxs-lookup"><span data-stu-id="73a9c-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="73a9c-104">L’implémentation Win32 de `VirtualAlloc` réserve ou valide une région de pages dans l’espace d’adressage virtuel du processus appelant.</span><span class="sxs-lookup"><span data-stu-id="73a9c-104">The Win32 implementation of `VirtualAlloc` reserves or commits a region of pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73a9c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73a9c-105">Syntax</span></span>  
  
```cpp  
HRESULT VirtualAlloc (  
    [in]  void*   pAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flAllocationType,  
    [in]  DWORD   flProtect,  
    [in]  EMemoryCriticalLevel dwCriticalLevel,  
    [out] void**  ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73a9c-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="73a9c-106">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="73a9c-107">[in] Pointeur vers l’adresse de départ de la région à allouer.</span><span class="sxs-lookup"><span data-stu-id="73a9c-107">[in] A pointer to the starting address of the region to allocate.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="73a9c-108">[in] La taille, en octets, de la région.</span><span class="sxs-lookup"><span data-stu-id="73a9c-108">[in] The size, in bytes, of the region.</span></span>  
  
 `flAllocationType`  
 <span data-ttu-id="73a9c-109">[in] Le type d’allocation de mémoire.</span><span class="sxs-lookup"><span data-stu-id="73a9c-109">[in] The type of memory allocation.</span></span>  
  
 `flProtect`  
 <span data-ttu-id="73a9c-110">[in] Protection de la mémoire pour la région de pages à allouer.</span><span class="sxs-lookup"><span data-stu-id="73a9c-110">[in] Memory protection for the region of pages to be allocated.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="73a9c-111">[in] Un [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) valeur qui indique l’impact d’un échec d’allocation.</span><span class="sxs-lookup"><span data-stu-id="73a9c-111">[in] An [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) value that indicates the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="73a9c-112">[out] Pointeur vers l’adresse de départ de la mémoire allouée, ou null si la demande n’a pas pu être satisfaite.</span><span class="sxs-lookup"><span data-stu-id="73a9c-112">[out] Pointer to the starting address of the allocated memory, or null if the request could not be satisfied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="73a9c-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="73a9c-113">Return Value</span></span>  
  
|<span data-ttu-id="73a9c-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="73a9c-114">HRESULT</span></span>|<span data-ttu-id="73a9c-115">Description</span><span class="sxs-lookup"><span data-stu-id="73a9c-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="73a9c-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="73a9c-116">S_OK</span></span>|<span data-ttu-id="73a9c-117">`VirtualAlloc` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="73a9c-117">`VirtualAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="73a9c-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="73a9c-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="73a9c-119">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="73a9c-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="73a9c-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="73a9c-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="73a9c-121">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="73a9c-121">The call timed out.</span></span>|  
|<span data-ttu-id="73a9c-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="73a9c-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="73a9c-123">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="73a9c-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="73a9c-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="73a9c-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="73a9c-125">Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="73a9c-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="73a9c-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="73a9c-126">E_FAIL</span></span>|<span data-ttu-id="73a9c-127">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="73a9c-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="73a9c-128">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus.</span><span class="sxs-lookup"><span data-stu-id="73a9c-128">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="73a9c-129">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="73a9c-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="73a9c-130">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="73a9c-130">E_OUTOFMEMORY</span></span>|<span data-ttu-id="73a9c-131">Mémoire était insuffisante pour terminer la demande d’allocation</span><span class="sxs-lookup"><span data-stu-id="73a9c-131">Not enough memory was available to complete the allocation request</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73a9c-132">Notes</span><span class="sxs-lookup"><span data-stu-id="73a9c-132">Remarks</span></span>  
 <span data-ttu-id="73a9c-133">Vous réservez une région dans l’espace d’adressage de votre processus en appelant `VirtualAlloc`.</span><span class="sxs-lookup"><span data-stu-id="73a9c-133">You reserve a region in the address space of your process by calling `VirtualAlloc`.</span></span> <span data-ttu-id="73a9c-134">Le `pAddress` paramètre contient l’adresse de début du bloc de mémoire souhaitée.</span><span class="sxs-lookup"><span data-stu-id="73a9c-134">The `pAddress` parameter contains the beginning address of the memory block you want.</span></span> <span data-ttu-id="73a9c-135">Ce paramètre est généralement défini sur null.</span><span class="sxs-lookup"><span data-stu-id="73a9c-135">This parameter is typically set to null.</span></span> <span data-ttu-id="73a9c-136">Le système d’exploitation conserve un enregistrement des plages d’adresses libres disponibles pour votre processus.</span><span class="sxs-lookup"><span data-stu-id="73a9c-136">The operating system keeps a record of free address ranges available to your process.</span></span> <span data-ttu-id="73a9c-137">Un `pAddress` NULL comme valeur prescrit au système de réserver la région chaque fois qu’il juge.</span><span class="sxs-lookup"><span data-stu-id="73a9c-137">A `pAddress` value of null instructs the system to reserve the region wherever it sees fit.</span></span> <span data-ttu-id="73a9c-138">Vous pouvez également fournir une adresse de départ spécifique pour le bloc de mémoire.</span><span class="sxs-lookup"><span data-stu-id="73a9c-138">Alternatively, you can provide a specific starting address for the memory block.</span></span> <span data-ttu-id="73a9c-139">Dans les deux cas, le paramètre de sortie `ppMem` est retourné comme un pointeur vers la mémoire allouée.</span><span class="sxs-lookup"><span data-stu-id="73a9c-139">In both cases, the output parameter `ppMem` is returned as a pointer to the allocated memory.</span></span> <span data-ttu-id="73a9c-140">La fonction elle-même retourne une valeur HRESULT.</span><span class="sxs-lookup"><span data-stu-id="73a9c-140">The function itself returns an HRESULT value.</span></span>  
  
 <span data-ttu-id="73a9c-141">Win32 `VirtualAlloc` fonction n’a pas un `ppMem` paramètre et retourne le pointeur vers la mémoire allouée à la place.</span><span class="sxs-lookup"><span data-stu-id="73a9c-141">The Win32 `VirtualAlloc` function does not have a `ppMem` parameter, and returns the pointer to the allocated memory instead.</span></span> <span data-ttu-id="73a9c-142">Pour plus d’informations, consultez la documentation de la plateforme de Windows.</span><span class="sxs-lookup"><span data-stu-id="73a9c-142">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73a9c-143">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="73a9c-143">Requirements</span></span>  
 <span data-ttu-id="73a9c-144">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73a9c-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73a9c-145">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="73a9c-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="73a9c-146">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="73a9c-146">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="73a9c-147">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73a9c-147">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73a9c-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="73a9c-148">See also</span></span>

- [<span data-ttu-id="73a9c-149">IHostMemoryManager, interface</span><span class="sxs-lookup"><span data-stu-id="73a9c-149">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
