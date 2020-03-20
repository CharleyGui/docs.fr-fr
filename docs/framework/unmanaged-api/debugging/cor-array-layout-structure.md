---
title: COR_ARRAY_LAYOUT, structure
ms.date: 03/30/2017
api_name:
- COR_ARRAY_LAYOUT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_ARRAY_LAYOUT
helpviewer_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP structure [.NET Framework debugging]
ms.assetid: aa20ac3d-6f60-4aa2-91c5-f3a86f82eba8
topic_type:
- apiref
ms.openlocfilehash: ca2d00611a7530dfb0d1c2a27123947bdf69820d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179349"
---
# <a name="cor_array_layout-structure"></a><span data-ttu-id="6be6b-102">COR_ARRAY_LAYOUT, structure</span><span class="sxs-lookup"><span data-stu-id="6be6b-102">COR_ARRAY_LAYOUT Structure</span></span>
<span data-ttu-id="6be6b-103">Fournit des informations sur la disposition d'un objet Array en mémoire.</span><span class="sxs-lookup"><span data-stu-id="6be6b-103">Provides information about the layout of an array object in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6be6b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6be6b-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_ARRAY_LAYOUT {  
    COR_TYPEID componentID;  
    CorElementType componentType;  
    ULONG32 firstElementOffset;  
    ULONG32 elementSize;  
    ULONG32 countOffset;
    ULONG32 rankSize;
    ULONG32 numRanks;
    ULONG32 rankOffset;
} COR_ARRAY_LAYOUT;  
```  
  
## <a name="members"></a><span data-ttu-id="6be6b-105">Membres</span><span class="sxs-lookup"><span data-stu-id="6be6b-105">Members</span></span>  
  
|<span data-ttu-id="6be6b-106">Membre</span><span class="sxs-lookup"><span data-stu-id="6be6b-106">Member</span></span>|<span data-ttu-id="6be6b-107">Description</span><span class="sxs-lookup"><span data-stu-id="6be6b-107">Description</span></span>|  
|------------|-----------------|  
|`componentID`|<span data-ttu-id="6be6b-108">L’identifiant du type d’objets que contient le tableau.</span><span class="sxs-lookup"><span data-stu-id="6be6b-108">The identifier of the type of objects that the array contains.</span></span>|  
|`componentType`|<span data-ttu-id="6be6b-109">Une valeur d’énumération De CorElementType qui indique si le composant est une référence de collecte d’ordures, une classe de valeur, ou un primitif.</span><span class="sxs-lookup"><span data-stu-id="6be6b-109">A CorElementType enumeration value that indicates whether the component is a garbage collection reference, a value class, or a primitive.</span></span>|  
|`firstElementOffset`|<span data-ttu-id="6be6b-110">Le décalage au premier élément du tableau.</span><span class="sxs-lookup"><span data-stu-id="6be6b-110">The offset to the first element in the array.</span></span>|  
|`elementSize`|<span data-ttu-id="6be6b-111">La taille de chaque élément.</span><span class="sxs-lookup"><span data-stu-id="6be6b-111">The size of each element.</span></span>|  
|`countOffset`|<span data-ttu-id="6be6b-112">Le décalage au nombre d’éléments dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="6be6b-112">The offset to the number of elements in the array.</span></span>|  
|`rankSize`|<span data-ttu-id="6be6b-113">La taille du rang, dans les octets.</span><span class="sxs-lookup"><span data-stu-id="6be6b-113">The size of the rank, in bytes.</span></span>|  
|`numRanks`|<span data-ttu-id="6be6b-114">Le nombre de rangs dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="6be6b-114">The number of ranks in the array.</span></span>|  
|`rankOffset`|<span data-ttu-id="6be6b-115">Le décalage auquel les rangs commencent.</span><span class="sxs-lookup"><span data-stu-id="6be6b-115">The offset at which the ranks start.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6be6b-116">Notes </span><span class="sxs-lookup"><span data-stu-id="6be6b-116">Remarks</span></span>  
 <span data-ttu-id="6be6b-117">Le `rankSize` champ spécifie la taille d’un rang dans un tableau multidimensionnel.</span><span class="sxs-lookup"><span data-stu-id="6be6b-117">The `rankSize` field specifies the size of a rank in a multi-dimensional array.</span></span> <span data-ttu-id="6be6b-118">Il est également exact pour les tableaux unidimensionnels.</span><span class="sxs-lookup"><span data-stu-id="6be6b-118">It is accurate for single-dimensional arrays as well.</span></span>  
  
 <span data-ttu-id="6be6b-119">La valeur `numRanks` de 1 pour un `N` tableau unidimensionnel et `N` pour un éventail multidimensionnel de dimensions.</span><span class="sxs-lookup"><span data-stu-id="6be6b-119">The value of `numRanks` is 1 for a single-dimensional array and `N` for a multi-dimensional array of `N` dimensions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6be6b-120">Spécifications</span><span class="sxs-lookup"><span data-stu-id="6be6b-120">Requirements</span></span>  
 <span data-ttu-id="6be6b-121">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6be6b-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6be6b-122">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6be6b-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6be6b-123">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6be6b-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6be6b-124">**.NET Versions-cadre:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6be6b-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6be6b-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6be6b-125">See also</span></span>

- [<span data-ttu-id="6be6b-126">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="6be6b-126">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="6be6b-127">Débogage</span><span class="sxs-lookup"><span data-stu-id="6be6b-127">Debugging</span></span>](index.md)
