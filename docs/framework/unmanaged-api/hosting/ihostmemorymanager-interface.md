---
title: IHostMemoryManager, interface
ms.date: 03/30/2017
api_name:
- IHostMemoryManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager
helpviewer_keywords:
- IHostMemoryManager interface [.NET Framework hosting]
ms.assetid: a945d439-3b34-4aa4-b575-8413dd7806ce
topic_type:
- apiref
ms.openlocfilehash: 4e7e76a4a3ab291ee97ad0912e3d6224cdf96fba
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804491"
---
# <a name="ihostmemorymanager-interface"></a><span data-ttu-id="238ae-102">IHostMemoryManager, interface</span><span class="sxs-lookup"><span data-stu-id="238ae-102">IHostMemoryManager Interface</span></span>
<span data-ttu-id="238ae-103">Fournit des méthodes qui permettent au common language runtime (CLR) de faire des demandes de mémoire virtuelle via l’hôte, au lieu d’utiliser les fonctions de mémoire virtuelle Win32 standard.</span><span class="sxs-lookup"><span data-stu-id="238ae-103">Provides methods that allow the common language runtime (CLR) to make virtual memory requests through the host, instead of using the standard Win32 virtual memory functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="238ae-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="238ae-104">Methods</span></span>  
  
|<span data-ttu-id="238ae-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="238ae-105">Method</span></span>|<span data-ttu-id="238ae-106">Description</span><span class="sxs-lookup"><span data-stu-id="238ae-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="238ae-107">AcquiredVirtualAddressSpace, méthode</span><span class="sxs-lookup"><span data-stu-id="238ae-107">AcquiredVirtualAddressSpace Method</span></span>](ihostmemorymanager-acquiredvirtualaddressspace-method.md)|<span data-ttu-id="238ae-108">Avertit l’hôte que le common language runtime (CLR) a acquis la mémoire spécifiée à partir du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="238ae-108">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>|  
|[<span data-ttu-id="238ae-109">CreateMAlloc, méthode</span><span class="sxs-lookup"><span data-stu-id="238ae-109">CreateMAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)|<span data-ttu-id="238ae-110">Obtient un pointeur d’interface vers une instance d' [IHostMalloc](ihostmalloc-interface.md) utilisée pour demander des allocations de mémoire à partir d’un tas créé par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="238ae-110">Gets an interface pointer to an [IHostMAlloc](ihostmalloc-interface.md) instance that is used to request memory allocations from a heap created by the host.</span></span>|  
|[<span data-ttu-id="238ae-111">GetMemoryLoad, méthode</span><span class="sxs-lookup"><span data-stu-id="238ae-111">GetMemoryLoad Method</span></span>](ihostmemorymanager-getmemoryload-method.md)|<span data-ttu-id="238ae-112">Obtient la quantité de mémoire physique en cours d’utilisation, telle qu’elle est signalée par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="238ae-112">Gets the amount of physical memory that is currently being used, as reported by the host.</span></span>|  
|[<span data-ttu-id="238ae-113">NeedsVirtualAddressSpace, méthode</span><span class="sxs-lookup"><span data-stu-id="238ae-113">NeedsVirtualAddressSpace Method</span></span>](ihostmemorymanager-needsvirtualaddressspace-method.md)|<span data-ttu-id="238ae-114">Avertit l’hôte que le CLR va tenter d’utiliser la mémoire spécifiée.</span><span class="sxs-lookup"><span data-stu-id="238ae-114">Notifies the host that the CLR is going to attempt to use the specified memory.</span></span>|  
|[<span data-ttu-id="238ae-115">RegisterMemoryNotificationCallback, méthode</span><span class="sxs-lookup"><span data-stu-id="238ae-115">RegisterMemoryNotificationCallback Method</span></span>](ihostmemorymanager-registermemorynotificationcallback-method.md)|<span data-ttu-id="238ae-116">Inscrit un pointeur vers une fonction de rappel que l’hôte appelle pour notifier le CLR de la charge de mémoire actuelle sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="238ae-116">Registers a pointer to a callback function that the host invokes to notify the CLR of the current memory load on the computer.</span></span>|  
|[<span data-ttu-id="238ae-117">ReleasedVirtualAddressSpace, méthode</span><span class="sxs-lookup"><span data-stu-id="238ae-117">ReleasedVirtualAddressSpace Method</span></span>](ihostmemorymanager-releasedvirtualaddressspace-method.md)|<span data-ttu-id="238ae-118">Avertit l’hôte que le CLR a fini d’utiliser la mémoire spécifiée.</span><span class="sxs-lookup"><span data-stu-id="238ae-118">Notifies the host that the CLR has finished using the specified memory.</span></span>|  
|[<span data-ttu-id="238ae-119">VirtualAlloc, méthode</span><span class="sxs-lookup"><span data-stu-id="238ae-119">VirtualAlloc Method</span></span>](ihostmemorymanager-virtualalloc-method.md)|<span data-ttu-id="238ae-120">Sert de wrapper logique pour la fonction Win32 correspondante, qui réserve ou valide une région de pages dans l’espace d’adressage virtuel du processus appelant.</span><span class="sxs-lookup"><span data-stu-id="238ae-120">Serves as a logical wrapper for the corresponding Win32 function, which reserves or commits a region of pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="238ae-121">VirtualFree, méthode</span><span class="sxs-lookup"><span data-stu-id="238ae-121">VirtualFree Method</span></span>](ihostmemorymanager-virtualfree-method.md)|<span data-ttu-id="238ae-122">Sert de wrapper logique pour la fonction Win32 correspondante, qui libère, annule ou libère et annule la validation d’une région de pages dans l’espace d’adressage virtuel du processus appelant.</span><span class="sxs-lookup"><span data-stu-id="238ae-122">Serves as a logical wrapper for the corresponding Win32 function, which releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="238ae-123">VirtualProtect, méthode</span><span class="sxs-lookup"><span data-stu-id="238ae-123">VirtualProtect Method</span></span>](ihostmemorymanager-virtualprotect-method.md)|<span data-ttu-id="238ae-124">Sert de wrapper logique pour la fonction Win32 correspondante, qui modifie la protection sur une région de pages validées dans l’espace d’adressage virtuel du processus appelant.</span><span class="sxs-lookup"><span data-stu-id="238ae-124">Serves as a logical wrapper for the corresponding Win32 function, which changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="238ae-125">VirtualQuery, méthode</span><span class="sxs-lookup"><span data-stu-id="238ae-125">VirtualQuery Method</span></span>](ihostmemorymanager-virtualquery-method.md)|<span data-ttu-id="238ae-126">Sert de wrapper logique pour la fonction Win32 correspondante, qui récupère des informations sur une plage de pages dans l’espace d’adressage virtuel du processus appelant.</span><span class="sxs-lookup"><span data-stu-id="238ae-126">Serves as a logical wrapper for the corresponding Win32 function, which retrieves information about a range of pages in the virtual address space of the calling process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="238ae-127">Notes</span><span class="sxs-lookup"><span data-stu-id="238ae-127">Remarks</span></span>  
 <span data-ttu-id="238ae-128">`IHostMemoryManager`fournit également des méthodes pour que le CLR obtienne un pointeur permettant d’effectuer des demandes de mémoire sur le tas et d’obtenir le niveau de sollicitation de la mémoire dans le processus, comme indiqué par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="238ae-128">`IHostMemoryManager` also provides methods for the CLR to obtain a pointer through which to make memory requests on the heap and to get the level of memory pressure in the process, as reported by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="238ae-129">Spécifications</span><span class="sxs-lookup"><span data-stu-id="238ae-129">Requirements</span></span>  
 <span data-ttu-id="238ae-130">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="238ae-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="238ae-131">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="238ae-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="238ae-132">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="238ae-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="238ae-133">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="238ae-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="238ae-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="238ae-134">See also</span></span>

- [<span data-ttu-id="238ae-135">IHostMalloc, interface</span><span class="sxs-lookup"><span data-stu-id="238ae-135">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
- [<span data-ttu-id="238ae-136">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="238ae-136">Hosting Interfaces</span></span>](hosting-interfaces.md)
