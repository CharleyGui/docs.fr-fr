---
title: IGCHost, interface
ms.date: 03/30/2017
api_name:
- IGCHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost
helpviewer_keywords:
- IGCHost interface [.NET Framework hosting]
ms.assetid: 9ad70ffd-6963-4ab2-8c84-3d86c3fb8deb
topic_type:
- apiref
ms.openlocfilehash: 9d6c9d22f4e50c21e2f41b7efd402907ff5843db
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805219"
---
# <a name="igchost-interface"></a><span data-ttu-id="f4540-102">IGCHost, interface</span><span class="sxs-lookup"><span data-stu-id="f4540-102">IGCHost Interface</span></span>
<span data-ttu-id="f4540-103">Fournit des méthodes pour obtenir des informations sur le système de garbage collection et pour contrôler certains aspects de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="f4540-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f4540-104">À partir de la .NET Framework 4,5, vous pouvez utiliser la méthode [IGCHost2 :: setgcstartuplimitsex,](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) pour définir la taille d’un segment garbage collection et la taille maximale de la génération 0 du système garbage collection sur des valeurs supérieures à la `DWORD` limite imposée par la méthode [SetGCStartupLimits (](igchost-setgcstartuplimits-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f4540-104">Starting with the .NET Framework 4.5, you can use the [IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](igchost-setgcstartuplimits-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f4540-105">Cette interface n’est destinée qu’à une utilisation par des experts.</span><span class="sxs-lookup"><span data-stu-id="f4540-105">This interface is for expert usage only.</span></span> <span data-ttu-id="f4540-106">Cela peut affecter les performances d’une application si elle est utilisée de manière incorrecte.</span><span class="sxs-lookup"><span data-stu-id="f4540-106">It can affect the performance of an application if used improperly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f4540-107">Méthodes</span><span class="sxs-lookup"><span data-stu-id="f4540-107">Methods</span></span>  
  
|<span data-ttu-id="f4540-108">Méthode</span><span class="sxs-lookup"><span data-stu-id="f4540-108">Method</span></span>|<span data-ttu-id="f4540-109">Description</span><span class="sxs-lookup"><span data-stu-id="f4540-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f4540-110">Collect, méthode</span><span class="sxs-lookup"><span data-stu-id="f4540-110">Collect Method</span></span>](igchost-collect-method.md)|<span data-ttu-id="f4540-111">Force une collection à se produire pour la génération donnée, quel que soit l’état du garbage collection actuel.</span><span class="sxs-lookup"><span data-stu-id="f4540-111">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>|  
|[<span data-ttu-id="f4540-112">GetStats, méthode</span><span class="sxs-lookup"><span data-stu-id="f4540-112">GetStats Method</span></span>](igchost-getstats-method.md)|<span data-ttu-id="f4540-113">Obtient les statistiques de l’état actuel du système de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="f4540-113">Gets the statistics for the current state of the garbage collection system.</span></span>|  
|[<span data-ttu-id="f4540-114">GetThreadStats, méthode</span><span class="sxs-lookup"><span data-stu-id="f4540-114">GetThreadStats Method</span></span>](igchost-getthreadstats-method.md)|<span data-ttu-id="f4540-115">Obtient les statistiques par thread pour garbage collection.</span><span class="sxs-lookup"><span data-stu-id="f4540-115">Gets the per-thread statistics for garbage collection.</span></span>|  
|[<span data-ttu-id="f4540-116">SetGCStartupLimits, méthode</span><span class="sxs-lookup"><span data-stu-id="f4540-116">SetGCStartupLimits Method</span></span>](igchost-setgcstartuplimits-method.md)|<span data-ttu-id="f4540-117">Définit la taille du segment et la taille maximale de la génération 0.</span><span class="sxs-lookup"><span data-stu-id="f4540-117">Sets the segment size and the maximum size for generation 0.</span></span>|  
|[<span data-ttu-id="f4540-118">SetVirtualMemLimit, méthode</span><span class="sxs-lookup"><span data-stu-id="f4540-118">SetVirtualMemLimit Method</span></span>](igchost-setvirtualmemlimit-method.md)|<span data-ttu-id="f4540-119">Définit la taille maximale de la mémoire virtuelle du Runtime.</span><span class="sxs-lookup"><span data-stu-id="f4540-119">Sets the maximum size of the runtime's virtual memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f4540-120">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f4540-120">Requirements</span></span>  
 <span data-ttu-id="f4540-121">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4540-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4540-122">**En-tête :** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="f4540-122">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="f4540-123">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f4540-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f4540-124">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4540-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4540-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f4540-125">See also</span></span>

- [<span data-ttu-id="f4540-126">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="f4540-126">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="f4540-127">CorRuntimeHost, coclasse</span><span class="sxs-lookup"><span data-stu-id="f4540-127">CorRuntimeHost Coclass</span></span>](corruntimehost-coclass.md)
