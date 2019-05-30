---
title: ICLRGCManager, interface
ms.date: 03/30/2017
api_name:
- ICLRGCManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager
helpviewer_keywords:
- ICLRGCManager interface [.NET Framework hosting]
ms.assetid: fb511c9b-3fe4-41b0-822a-6ba4a079d1f5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e284f94ad0dac9523bd6267e7bc1034a079503d
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380298"
---
# <a name="iclrgcmanager-interface"></a><span data-ttu-id="94053-102">ICLRGCManager, interface</span><span class="sxs-lookup"><span data-stu-id="94053-102">ICLRGCManager Interface</span></span>
<span data-ttu-id="94053-103">Fournit des méthodes qui permettent à un hôte d’interagir avec le système de garbage collection du common language runtime.</span><span class="sxs-lookup"><span data-stu-id="94053-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="94053-104">À compter de .NET Framework 4.5, vous pouvez utiliser la [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) pour définir la taille d’un segment de garbage collection et la taille maximale de la génération du système de nettoyage 0 à des valeurs (méthode) supérieur à la `DWORD` limite imposée par le [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="94053-104">Starting with the .NET Framework 4.5, you can use the [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="94053-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="94053-105">Methods</span></span>  
  
|<span data-ttu-id="94053-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="94053-106">Method</span></span>|<span data-ttu-id="94053-107">Description</span><span class="sxs-lookup"><span data-stu-id="94053-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="94053-108">Collect, méthode</span><span class="sxs-lookup"><span data-stu-id="94053-108">Collect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-collect-method.md)|<span data-ttu-id="94053-109">Force une garbage collection pour la génération spécifiée.</span><span class="sxs-lookup"><span data-stu-id="94053-109">Forces a garbage collection for the specified generation.</span></span>|  
|[<span data-ttu-id="94053-110">GetStats, méthode</span><span class="sxs-lookup"><span data-stu-id="94053-110">GetStats Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md)|<span data-ttu-id="94053-111">Obtient un jeu de statistiques actuelles concernant le système de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="94053-111">Gets a set of current statistics about the garbage collection system.</span></span>|  
|[<span data-ttu-id="94053-112">SetGCStartupLimits, méthode</span><span class="sxs-lookup"><span data-stu-id="94053-112">SetGCStartupLimits Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md)|<span data-ttu-id="94053-113">Définit la taille d’un segment de garbage collection et la taille maximale de la génération du système de nettoyage 0.</span><span class="sxs-lookup"><span data-stu-id="94053-113">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94053-114">Notes</span><span class="sxs-lookup"><span data-stu-id="94053-114">Remarks</span></span>  
 <span data-ttu-id="94053-115">Le common language runtime (CLR) implémente son mécanisme de garbage collection avec managé <xref:System.GC> type.</span><span class="sxs-lookup"><span data-stu-id="94053-115">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="94053-116">Pour plus d’informations sur le système de garbage collection, consultez [Garbage Collection](../../../../docs/standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="94053-116">For more information about the garbage collection system, see [Garbage Collection](../../../../docs/standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94053-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="94053-117">Requirements</span></span>  
 <span data-ttu-id="94053-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94053-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94053-119">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="94053-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="94053-120">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="94053-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="94053-121">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94053-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94053-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="94053-122">See also</span></span>

- [<span data-ttu-id="94053-123">Gestion automatique de la mémoire</span><span class="sxs-lookup"><span data-stu-id="94053-123">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)
- [<span data-ttu-id="94053-124">COR_GC_STATS, structure</span><span class="sxs-lookup"><span data-stu-id="94053-124">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [<span data-ttu-id="94053-125">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="94053-125">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="94053-126">Interfaces d’hébergement CLR</span><span class="sxs-lookup"><span data-stu-id="94053-126">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="94053-127">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="94053-127">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="94053-128">Hébergement</span><span class="sxs-lookup"><span data-stu-id="94053-128">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
