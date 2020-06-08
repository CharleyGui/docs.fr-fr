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
ms.openlocfilehash: f878e2f1f86bc42c0ff5abada8d7df4feb9ed228
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504184"
---
# <a name="iclrgcmanager-interface"></a><span data-ttu-id="34734-102">ICLRGCManager, interface</span><span class="sxs-lookup"><span data-stu-id="34734-102">ICLRGCManager Interface</span></span>
<span data-ttu-id="34734-103">Fournit des méthodes qui permettent à un hôte d’interagir avec le système de garbage collection du common language runtime.</span><span class="sxs-lookup"><span data-stu-id="34734-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="34734-104">À partir de la .NET Framework 4,5, vous pouvez utiliser la méthode [ICLRGCManager2 :: setgcstartuplimitsex,](iclrgcmanager2-setgcstartuplimitsex-method.md) pour définir la taille d’un segment garbage collection et la taille maximale de la génération 0 du système garbage collection sur des valeurs supérieures à la `DWORD` limite imposée par la méthode [SetGCStartupLimits (](iclrgcmanager-setgcstartuplimits-method.md) .</span><span class="sxs-lookup"><span data-stu-id="34734-104">Starting with the .NET Framework 4.5, you can use the [ICLRGCManager2::SetGCStartupLimitsEx](iclrgcmanager2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](iclrgcmanager-setgcstartuplimits-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="34734-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="34734-105">Methods</span></span>  
  
|<span data-ttu-id="34734-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="34734-106">Method</span></span>|<span data-ttu-id="34734-107">Description</span><span class="sxs-lookup"><span data-stu-id="34734-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="34734-108">Collect, méthode</span><span class="sxs-lookup"><span data-stu-id="34734-108">Collect Method</span></span>](iclrgcmanager-collect-method.md)|<span data-ttu-id="34734-109">Force une garbage collection pour la génération spécifiée.</span><span class="sxs-lookup"><span data-stu-id="34734-109">Forces a garbage collection for the specified generation.</span></span>|  
|[<span data-ttu-id="34734-110">GetStats, méthode</span><span class="sxs-lookup"><span data-stu-id="34734-110">GetStats Method</span></span>](iclrgcmanager-getstats-method.md)|<span data-ttu-id="34734-111">Obtient un ensemble de statistiques actuelles sur le système de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="34734-111">Gets a set of current statistics about the garbage collection system.</span></span>|  
|[<span data-ttu-id="34734-112">SetGCStartupLimits, méthode</span><span class="sxs-lookup"><span data-stu-id="34734-112">SetGCStartupLimits Method</span></span>](iclrgcmanager-setgcstartuplimits-method.md)|<span data-ttu-id="34734-113">Définit la taille d’un segment de garbage collection et la taille maximale de la génération 0 du système garbage collection.</span><span class="sxs-lookup"><span data-stu-id="34734-113">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34734-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="34734-114">Remarks</span></span>  
 <span data-ttu-id="34734-115">Le common language runtime (CLR) implémente son mécanisme de garbage collection avec le <xref:System.GC> type managé.</span><span class="sxs-lookup"><span data-stu-id="34734-115">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="34734-116">Pour plus d’informations sur le système de garbage collection, consultez [garbage collection](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="34734-116">For more information about the garbage collection system, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34734-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="34734-117">Requirements</span></span>  
 <span data-ttu-id="34734-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34734-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34734-119">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="34734-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="34734-120">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="34734-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="34734-121">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34734-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34734-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="34734-122">See also</span></span>

- [<span data-ttu-id="34734-123">Gestion automatique de la mémoire</span><span class="sxs-lookup"><span data-stu-id="34734-123">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="34734-124">COR_GC_STATS, structure</span><span class="sxs-lookup"><span data-stu-id="34734-124">COR_GC_STATS Structure</span></span>](cor-gc-stats-structure.md)
- [<span data-ttu-id="34734-125">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="34734-125">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="34734-126">Interfaces d'hébergement du CLR</span><span class="sxs-lookup"><span data-stu-id="34734-126">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="34734-127">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="34734-127">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="34734-128">Hosting</span><span class="sxs-lookup"><span data-stu-id="34734-128">Hosting</span></span>](index.md)
