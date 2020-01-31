---
title: COR_PRF_GC_GENERATION, énumération
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_GENERATION
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_GENERATION
helpviewer_keywords:
- COR_GC_GENERATION_FLAGS enumeration [.NET Framework profiling]
ms.assetid: d6ece160-26ad-4d39-abd7-05acd6f78c48
topic_type:
- apiref
ms.openlocfilehash: 4eff8472e353c4e5fd2505b281cc9efc89f013fc
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867208"
---
# <a name="cor_prf_gc_generation-enumeration"></a><span data-ttu-id="d9aa3-102">COR_PRF_GC_GENERATION, énumération</span><span class="sxs-lookup"><span data-stu-id="d9aa3-102">COR_PRF_GC_GENERATION Enumeration</span></span>
<span data-ttu-id="d9aa3-103">Identifie une génération de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="d9aa3-103">Identifies a garbage-collection generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9aa3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d9aa3-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_GEN_0 = 0,  
    COR_PRF_GC_GEN_1 = 1,  
    COR_PRF_GC_GEN_2 = 2,  
    COR_PRF_GC_LARGE_OBJECT_HEAP = 3  
} COR_PRF_GC_GENERATION;  
```  
  
## <a name="members"></a><span data-ttu-id="d9aa3-105">Members</span><span class="sxs-lookup"><span data-stu-id="d9aa3-105">Members</span></span>  
  
|<span data-ttu-id="d9aa3-106">Member</span><span class="sxs-lookup"><span data-stu-id="d9aa3-106">Member</span></span>|<span data-ttu-id="d9aa3-107">Description</span><span class="sxs-lookup"><span data-stu-id="d9aa3-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_GEN_0`|<span data-ttu-id="d9aa3-108">L’objet est stocké en tant que génération 0.</span><span class="sxs-lookup"><span data-stu-id="d9aa3-108">The object is stored as generation 0.</span></span>|  
|`COR_PRF_GC_GEN_1`|<span data-ttu-id="d9aa3-109">L’objet est stocké en tant que génération 1.</span><span class="sxs-lookup"><span data-stu-id="d9aa3-109">The object is stored as generation 1.</span></span>|  
|`COR_PRF_GC_GEN_2`|<span data-ttu-id="d9aa3-110">L’objet est stocké en tant que génération 2.</span><span class="sxs-lookup"><span data-stu-id="d9aa3-110">The object is stored as generation 2.</span></span>|  
|`COR_PRF_GC_LARGE_OBJECT_HEAP`|<span data-ttu-id="d9aa3-111">L’objet est stocké dans le tas d’objets volumineux.</span><span class="sxs-lookup"><span data-stu-id="d9aa3-111">The object is stored in the large-object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9aa3-112">Notes</span><span class="sxs-lookup"><span data-stu-id="d9aa3-112">Remarks</span></span>  
 <span data-ttu-id="d9aa3-113">Le garbage collector améliore les performances de gestion de la mémoire en divisant les objets en générations en fonction de leur âge.</span><span class="sxs-lookup"><span data-stu-id="d9aa3-113">The garbage collector improves memory management performance by dividing objects into generations based on age.</span></span> <span data-ttu-id="d9aa3-114">Le « garbage collector » utilise actuellement trois générations, numérotées 0, 1 et 2, ainsi qu’un segment de tas spécial utilisé pour les objets volumineux.</span><span class="sxs-lookup"><span data-stu-id="d9aa3-114">The garbage collector currently uses three generations, numbered 0, 1, and 2, plus a special heap segment that is used for large objects.</span></span> <span data-ttu-id="d9aa3-115">Les objets dont la taille est supérieure à une valeur particulière sont stockés dans le tas d’objets volumineux.</span><span class="sxs-lookup"><span data-stu-id="d9aa3-115">Objects whose size is larger than a particular value are stored in the large-object heap.</span></span> <span data-ttu-id="d9aa3-116">Les autres objets alloués commencent à appartenir à la génération 0.</span><span class="sxs-lookup"><span data-stu-id="d9aa3-116">Other allocated objects start out belonging to generation 0.</span></span> <span data-ttu-id="d9aa3-117">Tous les objets qui existent après garbage collection se produisent dans la génération 0 sont promus à la génération 1.</span><span class="sxs-lookup"><span data-stu-id="d9aa3-117">All objects that exist after garbage collection occurs in generation 0 are promoted to generation 1.</span></span> <span data-ttu-id="d9aa3-118">Les objets qui existent après garbage collection se produisent dans la génération 1 sont déplacés dans la génération 2.</span><span class="sxs-lookup"><span data-stu-id="d9aa3-118">Objects that exist after garbage collection occurs in generation 1 move into generation 2.</span></span>  
  
 <span data-ttu-id="d9aa3-119">L’utilisation de générations signifie que le garbage collector ne doit utiliser qu’un sous-ensemble des objets alloués à un moment donné.</span><span class="sxs-lookup"><span data-stu-id="d9aa3-119">The use of generations means that the garbage collector has to work with only a subset of the allocated objects at any one time.</span></span>  
  
 <span data-ttu-id="d9aa3-120">L’énumération `COR_PRF_GC_GENERATION` est utilisée par la structure [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="d9aa3-120">The `COR_PRF_GC_GENERATION` enumeration is used by the [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9aa3-121">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="d9aa3-121">Requirements</span></span>  
 <span data-ttu-id="d9aa3-122">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9aa3-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9aa3-123">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d9aa3-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d9aa3-124">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d9aa3-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d9aa3-125">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9aa3-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9aa3-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d9aa3-126">See also</span></span>

- [<span data-ttu-id="d9aa3-127">Énumérations de profilage</span><span class="sxs-lookup"><span data-stu-id="d9aa3-127">Profiling Enumerations</span></span>](profiling-enumerations.md)
