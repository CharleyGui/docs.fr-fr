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
ms.openlocfilehash: 0eb1f57e3505f9ce5bb8b831d30c3891e51097c3
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158565"
---
# <a name="cor_prf_gc_generation-enumeration"></a><span data-ttu-id="c9b4d-102">COR_PRF_GC_GENERATION, énumération</span><span class="sxs-lookup"><span data-stu-id="c9b4d-102">COR_PRF_GC_GENERATION Enumeration</span></span>
<span data-ttu-id="c9b4d-103">Identifie une génération de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="c9b4d-103">Identifies a garbage-collection generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9b4d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9b4d-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_GEN_0 = 0,  
    COR_PRF_GC_GEN_1 = 1,  
    COR_PRF_GC_GEN_2 = 2,  
    COR_PRF_GC_LARGE_OBJECT_HEAP = 3,
    COR_PRF_GC_PINNED_OBJECT_HEAP= 4
} COR_PRF_GC_GENERATION;  
```  
  
## <a name="members"></a><span data-ttu-id="c9b4d-105">Membres</span><span class="sxs-lookup"><span data-stu-id="c9b4d-105">Members</span></span>  
  
|<span data-ttu-id="c9b4d-106">Membre</span><span class="sxs-lookup"><span data-stu-id="c9b4d-106">Member</span></span>|<span data-ttu-id="c9b4d-107">Description</span><span class="sxs-lookup"><span data-stu-id="c9b4d-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_GEN_0`|<span data-ttu-id="c9b4d-108">L’objet est stocké en tant que génération 0.</span><span class="sxs-lookup"><span data-stu-id="c9b4d-108">The object is stored as generation 0.</span></span>|  
|`COR_PRF_GC_GEN_1`|<span data-ttu-id="c9b4d-109">L’objet est stocké en tant que génération 1.</span><span class="sxs-lookup"><span data-stu-id="c9b4d-109">The object is stored as generation 1.</span></span>|  
|`COR_PRF_GC_GEN_2`|<span data-ttu-id="c9b4d-110">L’objet est stocké en tant que génération 2.</span><span class="sxs-lookup"><span data-stu-id="c9b4d-110">The object is stored as generation 2.</span></span>|  
|`COR_PRF_GC_LARGE_OBJECT_HEAP`|<span data-ttu-id="c9b4d-111">L’objet est stocké dans le tas d’objets volumineux.</span><span class="sxs-lookup"><span data-stu-id="c9b4d-111">The object is stored in the large-object heap.</span></span>|  
|`COR_PRF_GC_PINNED_OBJECT_HEAP`|<span data-ttu-id="c9b4d-112">L’objet est stocké dans le tas d’objets épinglés.</span><span class="sxs-lookup"><span data-stu-id="c9b4d-112">The object is stored in the pinned-object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9b4d-113">Notes </span><span class="sxs-lookup"><span data-stu-id="c9b4d-113">Remarks</span></span>  
 <span data-ttu-id="c9b4d-114">Le garbage collector améliore les performances de gestion de la mémoire en divisant les objets en générations en fonction de leur âge.</span><span class="sxs-lookup"><span data-stu-id="c9b4d-114">The garbage collector improves memory management performance by dividing objects into generations based on age.</span></span> <span data-ttu-id="c9b4d-115">Le « garbage collector » utilise actuellement trois générations, numérotées 0, 1 et 2, et deux segments de tas spéciaux, un pour les objets volumineux et un pour les objets épinglés.</span><span class="sxs-lookup"><span data-stu-id="c9b4d-115">The garbage collector currently uses three generations, numbered 0, 1, and 2, and two special heap segments, one for large objects and one for pinned objects.</span></span>
  
 <span data-ttu-id="c9b4d-116">Les objets dont la taille est supérieure à une valeur de seuil sont stockés dans le tas d’objets volumineux.</span><span class="sxs-lookup"><span data-stu-id="c9b4d-116">Objects whose size is larger than a threshold value are stored in the large-object heap.</span></span> <span data-ttu-id="c9b4d-117">Les objets épinglés peuvent être alloués au tas d’objets épinglés afin d’éviter les coûts de performance liés à leur allocation sur les tas normaux.</span><span class="sxs-lookup"><span data-stu-id="c9b4d-117">Pinned objects can be allocated to the pinned-object heap to avoid the performance cost of allocating them on the normal heaps.</span></span> <span data-ttu-id="c9b4d-118">Les autres objets alloués commencent à appartenir à la génération 0.</span><span class="sxs-lookup"><span data-stu-id="c9b4d-118">Other allocated objects start out belonging to generation 0.</span></span> <span data-ttu-id="c9b4d-119">Tous les objets qui existent après garbage collection se produisent dans la génération 0 sont promus à la génération 1.</span><span class="sxs-lookup"><span data-stu-id="c9b4d-119">All objects that exist after garbage collection occurs in generation 0 are promoted to generation 1.</span></span> <span data-ttu-id="c9b4d-120">Les objets qui existent après garbage collection se produisent dans la génération 1 sont déplacés dans la génération 2.</span><span class="sxs-lookup"><span data-stu-id="c9b4d-120">Objects that exist after garbage collection occurs in generation 1 move into generation 2.</span></span>  
  
 <span data-ttu-id="c9b4d-121">L’utilisation de générations signifie que le garbage collector ne doit utiliser qu’un sous-ensemble des objets alloués à un moment donné.</span><span class="sxs-lookup"><span data-stu-id="c9b4d-121">The use of generations means that the garbage collector has to work with only a subset of the allocated objects at any one time.</span></span>  
  
 <span data-ttu-id="c9b4d-122">L' `COR_PRF_GC_GENERATION` énumération est utilisée par la structure [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="c9b4d-122">The `COR_PRF_GC_GENERATION` enumeration is used by the [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9b4d-123">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c9b4d-123">Requirements</span></span>  
 <span data-ttu-id="c9b4d-124">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9b4d-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9b4d-125">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c9b4d-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c9b4d-126">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c9b4d-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9b4d-127">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9b4d-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9b4d-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c9b4d-128">See also</span></span>

- [<span data-ttu-id="c9b4d-129">Énumérations de profilage</span><span class="sxs-lookup"><span data-stu-id="c9b4d-129">Profiling Enumerations</span></span>](profiling-enumerations.md)
