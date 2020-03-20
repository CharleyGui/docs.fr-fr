---
title: COR_GC_THREAD_STATS, structure
ms.date: 03/30/2017
api_name:
- COR_GC_THREAD_STATS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_THREAD_STATS
helpviewer_keywords:
- COR_GC_THREAD_STATS structure [.NET Framework hosting]
ms.assetid: 01f9a59b-7679-4d42-9ced-4a8981625c3d
topic_type:
- apiref
ms.openlocfilehash: 64e0c466edcd8863244e6ed184c18422b5f66875
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178264"
---
# <a name="cor_gc_thread_stats-structure"></a><span data-ttu-id="325a1-102">COR_GC_THREAD_STATS, structure</span><span class="sxs-lookup"><span data-stu-id="325a1-102">COR_GC_THREAD_STATS Structure</span></span>
<span data-ttu-id="325a1-103">Contient des statistiques par fil concernant la collecte des ordures.</span><span class="sxs-lookup"><span data-stu-id="325a1-103">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="325a1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="325a1-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;
    ULONG      Flags;
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="325a1-105">Membres</span><span class="sxs-lookup"><span data-stu-id="325a1-105">Members</span></span>  
  
|<span data-ttu-id="325a1-106">Membre</span><span class="sxs-lookup"><span data-stu-id="325a1-106">Member</span></span>|<span data-ttu-id="325a1-107">Description</span><span class="sxs-lookup"><span data-stu-id="325a1-107">Description</span></span>|  
|------------|-----------------|  
|`PerThreadAllocation`|<span data-ttu-id="325a1-108">Le nombre d’octets de mémoire alloués sur `COR_GC_THREAD_STATS` le fil qui est associé à l’instance actuelle.</span><span class="sxs-lookup"><span data-stu-id="325a1-108">The number of bytes of memory allocated on the thread that is associated with the current `COR_GC_THREAD_STATS` instance.</span></span> <span data-ttu-id="325a1-109">Ce nombre est effacé à zéro chaque fois qu’une collecte d’ordures de génération zéro se produit.</span><span class="sxs-lookup"><span data-stu-id="325a1-109">This number is cleared to zero each time a generation-zero garbage collection occurs.</span></span>|  
|`Flags`|<span data-ttu-id="325a1-110">Le nombre d’octets promus à une génération supérieure à la plus récente collecte des ordures.</span><span class="sxs-lookup"><span data-stu-id="325a1-110">The number of bytes promoted to a higher generation at the most recent garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="325a1-111">Notes </span><span class="sxs-lookup"><span data-stu-id="325a1-111">Remarks</span></span>  
 <span data-ttu-id="325a1-112">[ICLRTask::GetMemStats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) prend un paramètre de sortie de type `COR_GC_THREAD_STATS`.</span><span class="sxs-lookup"><span data-stu-id="325a1-112">[ICLRTask::GetMemStats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) takes an output parameter of type `COR_GC_THREAD_STATS`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="325a1-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="325a1-113">Requirements</span></span>  
 <span data-ttu-id="325a1-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="325a1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="325a1-115">**En-tête:** GCHost.idl</span><span class="sxs-lookup"><span data-stu-id="325a1-115">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="325a1-116">**Bibliothèque:** Inclus comme une ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="325a1-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="325a1-117">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="325a1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="325a1-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="325a1-118">See also</span></span>

- [<span data-ttu-id="325a1-119">Structures d'hébergement</span><span class="sxs-lookup"><span data-stu-id="325a1-119">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="325a1-120">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="325a1-120">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
