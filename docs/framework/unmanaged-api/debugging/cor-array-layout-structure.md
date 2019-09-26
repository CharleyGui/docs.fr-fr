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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ec9c4f3afb8f3b7e75e22874996d57d29ce8cf16
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274215"
---
# <a name="cor_array_layout-structure"></a><span data-ttu-id="73877-102">COR_ARRAY_LAYOUT, structure</span><span class="sxs-lookup"><span data-stu-id="73877-102">COR_ARRAY_LAYOUT Structure</span></span>
<span data-ttu-id="73877-103">Fournit des informations sur la disposition d'un objet Array en mémoire.</span><span class="sxs-lookup"><span data-stu-id="73877-103">Provides information about the layout of an array object in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73877-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73877-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="73877-105">Membres</span><span class="sxs-lookup"><span data-stu-id="73877-105">Members</span></span>  
  
|<span data-ttu-id="73877-106">Membre</span><span class="sxs-lookup"><span data-stu-id="73877-106">Member</span></span>|<span data-ttu-id="73877-107">Description</span><span class="sxs-lookup"><span data-stu-id="73877-107">Description</span></span>|  
|------------|-----------------|  
|`componentID`|<span data-ttu-id="73877-108">Identificateur du type d’objets contenu dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="73877-108">The identifier of the type of objects that the array contains.</span></span>|  
|`componentType`|<span data-ttu-id="73877-109">Valeur d’énumération CorElementType qui indique si le composant est une référence garbage collection, une classe value ou une primitive.</span><span class="sxs-lookup"><span data-stu-id="73877-109">A CorElementType enumeration value that indicates whether the component is a garbage collection reference, a value class, or a primitive.</span></span>|  
|`firstElementOffset`|<span data-ttu-id="73877-110">Offset du premier élément dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="73877-110">The offset to the first element in the array.</span></span>|  
|`elementSize`|<span data-ttu-id="73877-111">Taille de chaque élément.</span><span class="sxs-lookup"><span data-stu-id="73877-111">The size of each element.</span></span>|  
|`countOffset`|<span data-ttu-id="73877-112">Offset du nombre d’éléments dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="73877-112">The offset to the number of elements in the array.</span></span>|  
|`rankSize`|<span data-ttu-id="73877-113">Taille du rang, en octets.</span><span class="sxs-lookup"><span data-stu-id="73877-113">The size of the rank, in bytes.</span></span>|  
|`numRanks`|<span data-ttu-id="73877-114">Nombre de rangs dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="73877-114">The number of ranks in the array.</span></span>|  
|`rankOffset`|<span data-ttu-id="73877-115">Décalage à partir duquel les rangs commencent.</span><span class="sxs-lookup"><span data-stu-id="73877-115">The offset at which the ranks start.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73877-116">Notes</span><span class="sxs-lookup"><span data-stu-id="73877-116">Remarks</span></span>  
 <span data-ttu-id="73877-117">Le `rankSize` champ spécifie la taille d’un rang dans un tableau multidimensionnel.</span><span class="sxs-lookup"><span data-stu-id="73877-117">The `rankSize` field specifies the size of a rank in a multi-dimensional array.</span></span> <span data-ttu-id="73877-118">Il est également exact pour les tableaux unidimensionnels.</span><span class="sxs-lookup"><span data-stu-id="73877-118">It is accurate for single-dimensional arrays as well.</span></span>  
  
 <span data-ttu-id="73877-119">La valeur de `numRanks` est 1 pour un tableau unidimensionnel et `N` pour un tableau multidimensionnel de `N` dimensions.</span><span class="sxs-lookup"><span data-stu-id="73877-119">The value of `numRanks` is 1 for a single-dimensional array and `N` for a multi-dimensional array of `N` dimensions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73877-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="73877-120">Requirements</span></span>  
 <span data-ttu-id="73877-121">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73877-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73877-122">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="73877-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73877-123">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73877-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73877-124">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73877-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73877-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="73877-125">See also</span></span>

- [<span data-ttu-id="73877-126">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="73877-126">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="73877-127">Débogage</span><span class="sxs-lookup"><span data-stu-id="73877-127">Debugging</span></span>](index.md)
