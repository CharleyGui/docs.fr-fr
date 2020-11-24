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
ms.openlocfilehash: dbe3df6bb20e5ad8f9eb534a366405eb9c33984f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678244"
---
# <a name="iclrgcmanager-interface"></a><span data-ttu-id="0253d-102">ICLRGCManager, interface</span><span class="sxs-lookup"><span data-stu-id="0253d-102">ICLRGCManager Interface</span></span>

<span data-ttu-id="0253d-103">Fournit des méthodes qui permettent à un hôte d’interagir avec le système de garbage collection du common language runtime.</span><span class="sxs-lookup"><span data-stu-id="0253d-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0253d-104">À partir de la .NET Framework 4,5, vous pouvez utiliser la méthode [ICLRGCManager2 :: setgcstartuplimitsex,](iclrgcmanager2-setgcstartuplimitsex-method.md) pour définir la taille d’un segment garbage collection et la taille maximale de la génération 0 du système garbage collection sur des valeurs supérieures à la `DWORD` limite imposée par la méthode [SetGCStartupLimits (](iclrgcmanager-setgcstartuplimits-method.md) .</span><span class="sxs-lookup"><span data-stu-id="0253d-104">Starting with the .NET Framework 4.5, you can use the [ICLRGCManager2::SetGCStartupLimitsEx](iclrgcmanager2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](iclrgcmanager-setgcstartuplimits-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0253d-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="0253d-105">Methods</span></span>  
  
|<span data-ttu-id="0253d-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="0253d-106">Method</span></span>|<span data-ttu-id="0253d-107">Description</span><span class="sxs-lookup"><span data-stu-id="0253d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0253d-108">Collect, méthode</span><span class="sxs-lookup"><span data-stu-id="0253d-108">Collect Method</span></span>](iclrgcmanager-collect-method.md)|<span data-ttu-id="0253d-109">Force une garbage collection pour la génération spécifiée.</span><span class="sxs-lookup"><span data-stu-id="0253d-109">Forces a garbage collection for the specified generation.</span></span>|  
|[<span data-ttu-id="0253d-110">GetStats (méthode)</span><span class="sxs-lookup"><span data-stu-id="0253d-110">GetStats Method</span></span>](iclrgcmanager-getstats-method.md)|<span data-ttu-id="0253d-111">Obtient un ensemble de statistiques actuelles sur le système de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="0253d-111">Gets a set of current statistics about the garbage collection system.</span></span>|  
|[<span data-ttu-id="0253d-112">SetGCStartupLimits, méthode</span><span class="sxs-lookup"><span data-stu-id="0253d-112">SetGCStartupLimits Method</span></span>](iclrgcmanager-setgcstartuplimits-method.md)|<span data-ttu-id="0253d-113">Définit la taille d’un segment de garbage collection et la taille maximale de la génération 0 du système garbage collection.</span><span class="sxs-lookup"><span data-stu-id="0253d-113">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0253d-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="0253d-114">Remarks</span></span>  

 <span data-ttu-id="0253d-115">Le common language runtime (CLR) implémente son mécanisme de garbage collection avec le <xref:System.GC> type managé.</span><span class="sxs-lookup"><span data-stu-id="0253d-115">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="0253d-116">Pour plus d’informations sur le système de garbage collection, consultez [garbage collection](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="0253d-116">For more information about the garbage collection system, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0253d-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0253d-117">Requirements</span></span>  

 <span data-ttu-id="0253d-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0253d-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0253d-119">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0253d-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0253d-120">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0253d-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0253d-121">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0253d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0253d-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0253d-122">See also</span></span>

- [<span data-ttu-id="0253d-123">Gestion automatique de la mémoire</span><span class="sxs-lookup"><span data-stu-id="0253d-123">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="0253d-124">COR_GC_STATS, structure</span><span class="sxs-lookup"><span data-stu-id="0253d-124">COR_GC_STATS Structure</span></span>](cor-gc-stats-structure.md)
- [<span data-ttu-id="0253d-125">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="0253d-125">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="0253d-126">Interfaces d'hébergement du CLR</span><span class="sxs-lookup"><span data-stu-id="0253d-126">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="0253d-127">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="0253d-127">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="0253d-128">Hébergement</span><span class="sxs-lookup"><span data-stu-id="0253d-128">Hosting</span></span>](index.md)
