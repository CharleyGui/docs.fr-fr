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
ms.openlocfilehash: 88e81779fc9c20c506f3b0aa11ac2da3958dfe86
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616695"
---
# <a name="cor_gc_thread_stats-structure"></a><span data-ttu-id="532e0-102">COR_GC_THREAD_STATS, structure</span><span class="sxs-lookup"><span data-stu-id="532e0-102">COR_GC_THREAD_STATS Structure</span></span>
<span data-ttu-id="532e0-103">Contient des statistiques par thread relatives à garbage collection.</span><span class="sxs-lookup"><span data-stu-id="532e0-103">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="532e0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="532e0-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;
    ULONG      Flags;
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="532e0-105">Membres</span><span class="sxs-lookup"><span data-stu-id="532e0-105">Members</span></span>  
  
|<span data-ttu-id="532e0-106">Membre</span><span class="sxs-lookup"><span data-stu-id="532e0-106">Member</span></span>|<span data-ttu-id="532e0-107">Description</span><span class="sxs-lookup"><span data-stu-id="532e0-107">Description</span></span>|  
|------------|-----------------|  
|`PerThreadAllocation`|<span data-ttu-id="532e0-108">Nombre d’octets de mémoire alloués sur le thread associé à l’instance actuelle `COR_GC_THREAD_STATS` .</span><span class="sxs-lookup"><span data-stu-id="532e0-108">The number of bytes of memory allocated on the thread that is associated with the current `COR_GC_THREAD_STATS` instance.</span></span> <span data-ttu-id="532e0-109">Ce nombre est effacé à zéro chaque fois qu’un garbage collection de génération zéro se produit.</span><span class="sxs-lookup"><span data-stu-id="532e0-109">This number is cleared to zero each time a generation-zero garbage collection occurs.</span></span>|  
|`Flags`|<span data-ttu-id="532e0-110">Nombre d’octets promus à une génération supérieure au garbage collection le plus récent.</span><span class="sxs-lookup"><span data-stu-id="532e0-110">The number of bytes promoted to a higher generation at the most recent garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="532e0-111">Notes</span><span class="sxs-lookup"><span data-stu-id="532e0-111">Remarks</span></span>  
 <span data-ttu-id="532e0-112">[ICLRTask :: GetMemStats,](iclrtask-getmemstats-method.md) accepte un paramètre de sortie de type `COR_GC_THREAD_STATS` .</span><span class="sxs-lookup"><span data-stu-id="532e0-112">[ICLRTask::GetMemStats](iclrtask-getmemstats-method.md) takes an output parameter of type `COR_GC_THREAD_STATS`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="532e0-113">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="532e0-113">Requirements</span></span>  
 <span data-ttu-id="532e0-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="532e0-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="532e0-115">**En-tête :** GCHost. idl</span><span class="sxs-lookup"><span data-stu-id="532e0-115">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="532e0-116">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="532e0-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="532e0-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="532e0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="532e0-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="532e0-118">See also</span></span>

- [<span data-ttu-id="532e0-119">Structures d'hébergement</span><span class="sxs-lookup"><span data-stu-id="532e0-119">Hosting Structures</span></span>](hosting-structures.md)
- [<span data-ttu-id="532e0-120">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="532e0-120">IHostTask Interface</span></span>](ihosttask-interface.md)
