---
title: ICLRGCManager2, interface
ms.date: 03/30/2017
api_name:
- ICLRGCManager2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager2
helpviewer_keywords:
- ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 4b5ffd7b-9ad7-41cd-9bba-34030ae3da7e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c54707d4c767fbb644ed892767be8351d2fd95b5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966185"
---
# <a name="iclrgcmanager2-interface"></a><span data-ttu-id="fae2b-102">ICLRGCManager2, interface</span><span class="sxs-lookup"><span data-stu-id="fae2b-102">ICLRGCManager2 Interface</span></span>
<span data-ttu-id="fae2b-103">Fournit des méthodes qui permettent à un hôte d’interagir avec le système de garbage collection du common language runtime.</span><span class="sxs-lookup"><span data-stu-id="fae2b-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fae2b-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="fae2b-104">Methods</span></span>  
  
|<span data-ttu-id="fae2b-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="fae2b-105">Method</span></span>|<span data-ttu-id="fae2b-106">Description</span><span class="sxs-lookup"><span data-stu-id="fae2b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fae2b-107">SetGCStartupLimitsEx, méthode</span><span class="sxs-lookup"><span data-stu-id="fae2b-107">SetGCStartupLimitsEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)|<span data-ttu-id="fae2b-108">Définit la taille d’un segment de garbage collection et la taille maximale de la génération 0 du système garbage collection.</span><span class="sxs-lookup"><span data-stu-id="fae2b-108">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span> <span data-ttu-id="fae2b-109">Active la génération 0 et la taille des `DWORD`segments supérieure à.</span><span class="sxs-lookup"><span data-stu-id="fae2b-109">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fae2b-110">Notes</span><span class="sxs-lookup"><span data-stu-id="fae2b-110">Remarks</span></span>  
 <span data-ttu-id="fae2b-111">Cette interface hérite de l' [interface ICLRGCManager](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="fae2b-111">This interface inherits from the [ICLRGCManager Interface](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span></span>  
  
 <span data-ttu-id="fae2b-112">Le Common Language Runtime (CLR) implémente son mécanisme de garbage collection avec le <xref:System.GC> type managé.</span><span class="sxs-lookup"><span data-stu-id="fae2b-112">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="fae2b-113">Pour plus d’informations sur le système de garbage collection, consultez [garbage collection](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="fae2b-113">For more information about the garbage collection system, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fae2b-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="fae2b-114">Requirements</span></span>  
 <span data-ttu-id="fae2b-115">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fae2b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fae2b-116">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fae2b-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fae2b-117">**Bibliothèque** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="fae2b-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fae2b-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fae2b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fae2b-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fae2b-119">See also</span></span>

- [<span data-ttu-id="fae2b-120">Gestion automatique de la mémoire</span><span class="sxs-lookup"><span data-stu-id="fae2b-120">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="fae2b-121">COR_GC_STATS, structure</span><span class="sxs-lookup"><span data-stu-id="fae2b-121">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [<span data-ttu-id="fae2b-122">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="fae2b-122">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="fae2b-123">Interfaces d’hébergement CLR ajoutées dans .NET Framework 4 et 4.5</span><span class="sxs-lookup"><span data-stu-id="fae2b-123">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="fae2b-124">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="fae2b-124">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="fae2b-125">Hébergement</span><span class="sxs-lookup"><span data-stu-id="fae2b-125">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
