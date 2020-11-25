---
title: COR_GC_STAT_TYPES (énumération)
ms.date: 03/30/2017
api_name:
- COR_GC_STAT_TYPES
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_STAT_TYPES
helpviewer_keywords:
- COR_GC_STAT_TYPES enumeration [.NET Framework hosting]
ms.assetid: fc51d6db-f7f8-408b-b93d-c166fc712c99
topic_type:
- apiref
ms.openlocfilehash: c14e27b67fc600e2684f8c967af30bb9a5cee126
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716737"
---
# <a name="cor_gc_stat_types-enumeration"></a><span data-ttu-id="86f60-102">COR_GC_STAT_TYPES (énumération)</span><span class="sxs-lookup"><span data-stu-id="86f60-102">COR_GC_STAT_TYPES Enumeration</span></span>

<span data-ttu-id="86f60-103">Spécifie les statistiques à enregistrer pour un garbage collection.</span><span class="sxs-lookup"><span data-stu-id="86f60-103">Specifies the statistics to be recorded for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86f60-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="86f60-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_GC_COUNTS                 = 0x00000001  
    COR_GC_MEMORYUSAGE            = 0x00000002  
} COR_GC_STAT_TYPES;  
```  
  
## <a name="remarks"></a><span data-ttu-id="86f60-105">Notes</span><span class="sxs-lookup"><span data-stu-id="86f60-105">Remarks</span></span>  

 <span data-ttu-id="86f60-106">Cette énumération spécifie les statistiques de la structure [COR_GC_STATS](cor-gc-stats-structure.md) qui doivent être définies par la méthode [ICLRGCManager :: GetStats](iclrgcmanager-getstats-method.md) .</span><span class="sxs-lookup"><span data-stu-id="86f60-106">This enumeration specifies which statistics in the [COR_GC_STATS](cor-gc-stats-structure.md) structure are to be set by [ICLRGCManager::GetStats](iclrgcmanager-getstats-method.md) method.</span></span>  
  
## <a name="members"></a><span data-ttu-id="86f60-107">Membres</span><span class="sxs-lookup"><span data-stu-id="86f60-107">Members</span></span>  
  
|<span data-ttu-id="86f60-108">Membre</span><span class="sxs-lookup"><span data-stu-id="86f60-108">Member</span></span>|<span data-ttu-id="86f60-109">Description</span><span class="sxs-lookup"><span data-stu-id="86f60-109">Description</span></span>|  
|------------|-----------------|  
|`COR_GC_COUNTS`|<span data-ttu-id="86f60-110">Enregistre le nombre de garbage collection effectués pour chaque génération.</span><span class="sxs-lookup"><span data-stu-id="86f60-110">Records the number of garbage collections performed for each generation.</span></span>|  
|`COR_GC_MEMORYUSAGE`|<span data-ttu-id="86f60-111">Enregistre l’utilisation de la mémoire et les statistiques de taille de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="86f60-111">Records memory usage and garbage collection size statistics.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="86f60-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="86f60-112">Requirements</span></span>  

 <span data-ttu-id="86f60-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86f60-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86f60-114">**En-tête :** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="86f60-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="86f60-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86f60-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86f60-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="86f60-116">See also</span></span>

- [<span data-ttu-id="86f60-117">COR_GC_STATS, structure</span><span class="sxs-lookup"><span data-stu-id="86f60-117">COR_GC_STATS Structure</span></span>](cor-gc-stats-structure.md)
- [<span data-ttu-id="86f60-118">Énumérations d'hébergement</span><span class="sxs-lookup"><span data-stu-id="86f60-118">Hosting Enumerations</span></span>](hosting-enumerations.md)
