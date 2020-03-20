---
title: COR_GC_STATS, structure
ms.date: 03/30/2017
api_name:
- COR_GC_STATS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_STATS
helpviewer_keywords:
- COR_GC_STATS structure [.NET Framework hosting]
ms.assetid: 8d4ff73e-739b-40f6-9349-359fbc99c2f9
topic_type:
- apiref
ms.openlocfilehash: 2ab0c38645a8e5fbd9e71b3c1787e88bfe2c0604
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176524"
---
# <a name="cor_gc_stats-structure"></a><span data-ttu-id="3fff6-102">COR_GC_STATS, structure</span><span class="sxs-lookup"><span data-stu-id="3fff6-102">COR_GC_STATS Structure</span></span>
<span data-ttu-id="3fff6-103">Fournit des statistiques sur le mécanisme de collecte des ordures de l’heure courante de course de langue (CLR).</span><span class="sxs-lookup"><span data-stu-id="3fff6-103">Provides statistics about the garbage collection mechanism of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fff6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3fff6-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_GC_STATS {  
    ULONG   Flags;
    SIZE_T  ExplicitGCCount;  
    SIZE_T  GenCollectionsTaken[3];  
    SIZE_T  CommittedKBytes;
    SIZE_T  ReservedKBytes;  
    SIZE_T  Gen0HeapSizeKBytes;  
    SIZE_T  Gen1HeapSizeKBytes;  
    SIZE_T  Gen2HeapSizeKBytes;  
    SIZE_T  LargeObjectHeapSizeKBytes;  
    SIZE_T  KBytesPromotedFromGen0;  
    SIZE_T  KBytesPromotedFromGen1;  
} COR_GC_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="3fff6-105">Membres</span><span class="sxs-lookup"><span data-stu-id="3fff6-105">Members</span></span>  
  
|<span data-ttu-id="3fff6-106">Membre</span><span class="sxs-lookup"><span data-stu-id="3fff6-106">Member</span></span>|<span data-ttu-id="3fff6-107">Description</span><span class="sxs-lookup"><span data-stu-id="3fff6-107">Description</span></span>|  
|------------|-----------------|  
|`Flags`|<span data-ttu-id="3fff6-108">Indique quelles valeurs de champ doivent être calculées et retournées.</span><span class="sxs-lookup"><span data-stu-id="3fff6-108">Indicates which field values should be calculated and returned.</span></span>|  
|`ExplicitGCCount`|<span data-ttu-id="3fff6-109">Indique le nombre de collectes d’ordures qui ont été forcées à la demande externe.</span><span class="sxs-lookup"><span data-stu-id="3fff6-109">Indicates the number of garbage collections that were forced by external request.</span></span>|  
|`GenCollectionsTaken`|<span data-ttu-id="3fff6-110">Indique le nombre de collectes d’ordures effectuées pour chaque génération.</span><span class="sxs-lookup"><span data-stu-id="3fff6-110">Indicates the number of garbage collections performed for each generation.</span></span>|  
|`CommittedKBytes`|<span data-ttu-id="3fff6-111">Le nombre total de kilooctets commis dans tous les tas.</span><span class="sxs-lookup"><span data-stu-id="3fff6-111">The total number of kilobytes committed in all heaps.</span></span>|  
|`ReservedKBytes`|<span data-ttu-id="3fff6-112">Le nombre total de kilooctets réservés dans tous les tas.</span><span class="sxs-lookup"><span data-stu-id="3fff6-112">The total number of kilobytes reserved in all heaps.</span></span>|  
|`Gen0HeapSizeKBytes`|<span data-ttu-id="3fff6-113">La taille, en kilooctets, du tas de génération zéro.</span><span class="sxs-lookup"><span data-stu-id="3fff6-113">The size, in kilobytes, of the generation-zero heap.</span></span>|  
|`Gen1HeapSizeKBytes`|<span data-ttu-id="3fff6-114">La taille, en kilooctets, du tas de génération un.</span><span class="sxs-lookup"><span data-stu-id="3fff6-114">The size, in kilobytes, of the generation-one heap.</span></span>|  
|`Gen2HeapSizeKBytes`|<span data-ttu-id="3fff6-115">La taille, en kilooctets, du tas de génération-deux.</span><span class="sxs-lookup"><span data-stu-id="3fff6-115">The size, in kilobytes, of the generation-two heap.</span></span>|  
|`LargeObjectHeapSizeKBytes`|<span data-ttu-id="3fff6-116">La taille, en kilooctets, du grand tas d’objets.</span><span class="sxs-lookup"><span data-stu-id="3fff6-116">The size, in kilobytes, of the large object heap.</span></span>|  
|`KBytesPromotedFromGen0`|<span data-ttu-id="3fff6-117">La taille, en kilooctets, des objets promus de la génération zéro à la première génération.</span><span class="sxs-lookup"><span data-stu-id="3fff6-117">The size, in kilobytes, of the objects promoted from generation zero to generation one.</span></span>|  
|`KBytesPromotedFromGen1`|<span data-ttu-id="3fff6-118">La taille, en kilooctets, des objets promus de la première génération à la deuxième génération.</span><span class="sxs-lookup"><span data-stu-id="3fff6-118">The size, in kilobytes, of the objects promoted from generation one to generation two.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3fff6-119">Notes </span><span class="sxs-lookup"><span data-stu-id="3fff6-119">Remarks</span></span>  
 <span data-ttu-id="3fff6-120">La méthode [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) méthode exige que le `Flags` champ de la `COR_GC_STATS` structure doit être mis à une ou plusieurs valeurs de [l’énumération COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) pour spécifier quelles statistiques doivent être définies.</span><span class="sxs-lookup"><span data-stu-id="3fff6-120">The [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) method requires the `Flags` field of the `COR_GC_STATS` structure to be set to one or more values of the [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration to specify which statistics are to be set.</span></span>  
  
 <span data-ttu-id="3fff6-121">Le tableau suivant dresse la carte des statistiques fournies par cette `COR_GC_COUNTS` `COR_GC_MEMORYUSAGE`structure aux deux [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) valeurs d’énumération, et .</span><span class="sxs-lookup"><span data-stu-id="3fff6-121">The following table maps the statistics provided by this structure to the two [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration values, `COR_GC_COUNTS` and `COR_GC_MEMORYUSAGE`.</span></span>  
  
|<span data-ttu-id="3fff6-122">Spécifié par COR_GC_COUNTS</span><span class="sxs-lookup"><span data-stu-id="3fff6-122">Specified by COR_GC_COUNTS</span></span>|<span data-ttu-id="3fff6-123">Spécifié par COR_GC_MEMORYUSAGE</span><span class="sxs-lookup"><span data-stu-id="3fff6-123">Specified by COR_GC_MEMORYUSAGE</span></span>|  
|----------------------------------|---------------------------------------|  
|`ExplicitGCCount`<br /><br /> `GenCollectionsTaken`|`CommittedKBytes`<br /><br /> `ReservedKBytes`<br /><br /> `Gen0HeapSizeKBytes`<br /><br /> `Gen1HeapSizeKBytes`<br /><br /> `Gen2HeapSizeKBytes`<br /><br /> `LargeObjectHeapSizeKBytes`<br /><br /> `KBytesPromotedFromGen0`<br /><br /> `KBytesPromotedFromGen1`|  
  
 <span data-ttu-id="3fff6-124">Un exemple de l’utilisation est le suivant :</span><span class="sxs-lookup"><span data-stu-id="3fff6-124">An example of the usage is as follows:</span></span>  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="3fff6-125">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3fff6-125">Requirements</span></span>  
 <span data-ttu-id="3fff6-126">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3fff6-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fff6-127">**En-tête:** GCHost.idl</span><span class="sxs-lookup"><span data-stu-id="3fff6-127">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="3fff6-128">**Bibliothèque:** Inclus comme une ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3fff6-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3fff6-129">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fff6-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fff6-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3fff6-130">See also</span></span>

- [<span data-ttu-id="3fff6-131">Structures d'hébergement</span><span class="sxs-lookup"><span data-stu-id="3fff6-131">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="3fff6-132">Gestion automatique de la mémoire</span><span class="sxs-lookup"><span data-stu-id="3fff6-132">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="3fff6-133">Garbage collection</span><span class="sxs-lookup"><span data-stu-id="3fff6-133">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
