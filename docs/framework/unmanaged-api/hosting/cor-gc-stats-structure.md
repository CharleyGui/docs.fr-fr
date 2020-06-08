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
ms.openlocfilehash: 7a6553de31d4f9627809af7691218c39dc734c6f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501662"
---
# <a name="cor_gc_stats-structure"></a><span data-ttu-id="92188-102">COR_GC_STATS, structure</span><span class="sxs-lookup"><span data-stu-id="92188-102">COR_GC_STATS Structure</span></span>
<span data-ttu-id="92188-103">Fournit des statistiques sur le mécanisme de garbage collection du common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="92188-103">Provides statistics about the garbage collection mechanism of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92188-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="92188-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="92188-105">Membres</span><span class="sxs-lookup"><span data-stu-id="92188-105">Members</span></span>  
  
|<span data-ttu-id="92188-106">Membre</span><span class="sxs-lookup"><span data-stu-id="92188-106">Member</span></span>|<span data-ttu-id="92188-107">Description</span><span class="sxs-lookup"><span data-stu-id="92188-107">Description</span></span>|  
|------------|-----------------|  
|`Flags`|<span data-ttu-id="92188-108">Indique les valeurs de champ qui doivent être calculées et retournées.</span><span class="sxs-lookup"><span data-stu-id="92188-108">Indicates which field values should be calculated and returned.</span></span>|  
|`ExplicitGCCount`|<span data-ttu-id="92188-109">Indique le nombre de garbage collection qui ont été forcés par une requête externe.</span><span class="sxs-lookup"><span data-stu-id="92188-109">Indicates the number of garbage collections that were forced by external request.</span></span>|  
|`GenCollectionsTaken`|<span data-ttu-id="92188-110">Indique le nombre de garbage collection effectués pour chaque génération.</span><span class="sxs-lookup"><span data-stu-id="92188-110">Indicates the number of garbage collections performed for each generation.</span></span>|  
|`CommittedKBytes`|<span data-ttu-id="92188-111">Nombre total de kilo-octets validés dans tous les tas.</span><span class="sxs-lookup"><span data-stu-id="92188-111">The total number of kilobytes committed in all heaps.</span></span>|  
|`ReservedKBytes`|<span data-ttu-id="92188-112">Nombre total de kilo-octets réservés dans tous les tas.</span><span class="sxs-lookup"><span data-stu-id="92188-112">The total number of kilobytes reserved in all heaps.</span></span>|  
|`Gen0HeapSizeKBytes`|<span data-ttu-id="92188-113">Taille, en kilo-octets, du tas de génération zéro.</span><span class="sxs-lookup"><span data-stu-id="92188-113">The size, in kilobytes, of the generation-zero heap.</span></span>|  
|`Gen1HeapSizeKBytes`|<span data-ttu-id="92188-114">Taille, en kilo-octets, du tas de génération-un.</span><span class="sxs-lookup"><span data-stu-id="92188-114">The size, in kilobytes, of the generation-one heap.</span></span>|  
|`Gen2HeapSizeKBytes`|<span data-ttu-id="92188-115">Taille, en kilo-octets, du tas de la génération-2.</span><span class="sxs-lookup"><span data-stu-id="92188-115">The size, in kilobytes, of the generation-two heap.</span></span>|  
|`LargeObjectHeapSizeKBytes`|<span data-ttu-id="92188-116">Taille, en kilo-octets, du tas d’objets volumineux.</span><span class="sxs-lookup"><span data-stu-id="92188-116">The size, in kilobytes, of the large object heap.</span></span>|  
|`KBytesPromotedFromGen0`|<span data-ttu-id="92188-117">Taille, en kilo-octets, des objets promus de la génération zéro à la génération 1.</span><span class="sxs-lookup"><span data-stu-id="92188-117">The size, in kilobytes, of the objects promoted from generation zero to generation one.</span></span>|  
|`KBytesPromotedFromGen1`|<span data-ttu-id="92188-118">Taille, en kilo-octets, des objets promus de la génération 1 à la génération 2.</span><span class="sxs-lookup"><span data-stu-id="92188-118">The size, in kilobytes, of the objects promoted from generation one to generation two.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92188-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="92188-119">Remarks</span></span>  
 <span data-ttu-id="92188-120">La méthode [ICLRGCManager :: GetStats](iclrgcmanager-getstats-method.md) exige que le `Flags` champ de la `COR_GC_STATS` structure soit défini sur une ou plusieurs valeurs de l’énumération [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) pour spécifier les statistiques à définir.</span><span class="sxs-lookup"><span data-stu-id="92188-120">The [ICLRGCManager::GetStats](iclrgcmanager-getstats-method.md) method requires the `Flags` field of the `COR_GC_STATS` structure to be set to one or more values of the [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) enumeration to specify which statistics are to be set.</span></span>  
  
 <span data-ttu-id="92188-121">Le tableau suivant mappe les statistiques fournies par cette structure aux deux [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) valeurs d’énumération, `COR_GC_COUNTS` et `COR_GC_MEMORYUSAGE` .</span><span class="sxs-lookup"><span data-stu-id="92188-121">The following table maps the statistics provided by this structure to the two [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) enumeration values, `COR_GC_COUNTS` and `COR_GC_MEMORYUSAGE`.</span></span>  
  
|<span data-ttu-id="92188-122">Spécifié par COR_GC_COUNTS</span><span class="sxs-lookup"><span data-stu-id="92188-122">Specified by COR_GC_COUNTS</span></span>|<span data-ttu-id="92188-123">Spécifié par COR_GC_MEMORYUSAGE</span><span class="sxs-lookup"><span data-stu-id="92188-123">Specified by COR_GC_MEMORYUSAGE</span></span>|  
|----------------------------------|---------------------------------------|  
|`ExplicitGCCount`<br /><br /> `GenCollectionsTaken`|`CommittedKBytes`<br /><br /> `ReservedKBytes`<br /><br /> `Gen0HeapSizeKBytes`<br /><br /> `Gen1HeapSizeKBytes`<br /><br /> `Gen2HeapSizeKBytes`<br /><br /> `LargeObjectHeapSizeKBytes`<br /><br /> `KBytesPromotedFromGen0`<br /><br /> `KBytesPromotedFromGen1`|  
  
 <span data-ttu-id="92188-124">Voici un exemple d’utilisation :</span><span class="sxs-lookup"><span data-stu-id="92188-124">An example of the usage is as follows:</span></span>  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="92188-125">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="92188-125">Requirements</span></span>  
 <span data-ttu-id="92188-126">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92188-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92188-127">**En-tête :** GCHost. idl</span><span class="sxs-lookup"><span data-stu-id="92188-127">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="92188-128">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="92188-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="92188-129">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92188-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92188-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="92188-130">See also</span></span>

- [<span data-ttu-id="92188-131">Structures d'hébergement</span><span class="sxs-lookup"><span data-stu-id="92188-131">Hosting Structures</span></span>](hosting-structures.md)
- [<span data-ttu-id="92188-132">Gestion automatique de la mémoire</span><span class="sxs-lookup"><span data-stu-id="92188-132">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="92188-133">Garbage collection</span><span class="sxs-lookup"><span data-stu-id="92188-133">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
