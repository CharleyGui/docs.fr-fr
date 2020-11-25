---
title: COR_TYPE_LAYOUT, structure
ms.date: 03/30/2017
api_name:
- COR_TYPE_LAYOUT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_TYPE_LAYOUT
helpviewer_keywords:
- COR_TYPE_LAYOUT structure [.NET Framework debugging]
ms.assetid: 43a7addd-f25a-4049-9907-abec3eb17af2
topic_type:
- apiref
ms.openlocfilehash: f33c8f5cf218979404063342d9b1cc5123839f83
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726325"
---
# <a name="cor_type_layout-structure"></a><span data-ttu-id="fc0b3-102">COR_TYPE_LAYOUT, structure</span><span class="sxs-lookup"><span data-stu-id="fc0b3-102">COR_TYPE_LAYOUT Structure</span></span>

<span data-ttu-id="fc0b3-103">Fournit des informations sur la disposition d'un objet en mémoire.</span><span class="sxs-lookup"><span data-stu-id="fc0b3-103">Provides information about the layout of an object in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc0b3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fc0b3-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_TYPE_LAYOUT {  
    COR_TYPEID parentID;  
    ULONG32 objectSize;  
    ULONG32 numFields;  
    ULONG32 boxOffset;  
    CorElementType type;  
} COR_TYPE_LAYOUT;  
```  
  
## <a name="members"></a><span data-ttu-id="fc0b3-105">Membres</span><span class="sxs-lookup"><span data-stu-id="fc0b3-105">Members</span></span>  
  
|<span data-ttu-id="fc0b3-106">Membre</span><span class="sxs-lookup"><span data-stu-id="fc0b3-106">Member</span></span>|<span data-ttu-id="fc0b3-107">Description</span><span class="sxs-lookup"><span data-stu-id="fc0b3-107">Description</span></span>|  
|------------|-----------------|  
|`parentID`|<span data-ttu-id="fc0b3-108">Identificateur du type parent à ce type.</span><span class="sxs-lookup"><span data-stu-id="fc0b3-108">The identifier of the parent type to this type.</span></span> <span data-ttu-id="fc0b3-109">Il s’agit de l’ID de type NULL (TOKEN1 = 0, Token2 = 0) si l’ID de type correspond à <xref:System.Object?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fc0b3-109">This will be the NULL type id (token1= 0, token2 = 0) if the type id corresponds to <xref:System.Object?displayProperty=nameWithType>.</span></span>|  
|`objectSize`|<span data-ttu-id="fc0b3-110">Taille de base d’un objet de ce type.</span><span class="sxs-lookup"><span data-stu-id="fc0b3-110">The base size of an object of this type.</span></span> <span data-ttu-id="fc0b3-111">Il s’agit de la taille totale des objets de taille non variable.</span><span class="sxs-lookup"><span data-stu-id="fc0b3-111">This is the total size for non-variable sized objects.</span></span>|  
|`numFields`|<span data-ttu-id="fc0b3-112">Nombre de champs inclus dans les objets de ce type.</span><span class="sxs-lookup"><span data-stu-id="fc0b3-112">The number of fields included in objects of this type.</span></span>|  
|`boxOffset`|<span data-ttu-id="fc0b3-113">Si ce type est boxed, il s’agit du décalage de début des champs d’un objet.</span><span class="sxs-lookup"><span data-stu-id="fc0b3-113">If this type is boxed, the beginning offset of an object's fields.</span></span> <span data-ttu-id="fc0b3-114">Ce champ est valide uniquement pour les types de valeur tels que les primitives et les structures.</span><span class="sxs-lookup"><span data-stu-id="fc0b3-114">This field is valid only for value types such as primitives and structures.</span></span>|  
|`type`|<span data-ttu-id="fc0b3-115">CorElementType auquel ce type appartient.</span><span class="sxs-lookup"><span data-stu-id="fc0b3-115">The CorElementType to which this type belongs.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc0b3-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="fc0b3-116">Remarks</span></span>  

 <span data-ttu-id="fc0b3-117">Si `numFields` est supérieur à zéro, vous pouvez appeler la méthode [ICorDebugProcess5 :: gettypefields,](icordebugprocess5-gettypefields-method.md) pour obtenir des informations sur les champs de ce type.</span><span class="sxs-lookup"><span data-stu-id="fc0b3-117">If `numFields` is greater than zero, you can call the [ICorDebugProcess5::GetTypeFields](icordebugprocess5-gettypefields-method.md) method to obtain information about the fields in this type.</span></span> <span data-ttu-id="fc0b3-118">Si `type` est `ELEMENT_TYPE_STRING` , `ELEMENT_TYPE_ARRAY` ou `ELEMENT_TYPE_SZARRAY` , la taille des objets de ce type est variable, et vous pouvez passer la structure [COR_TYPEID](cor-typeid-structure.md) à la méthode [ICorDebugProcess5 :: getarraylayout,](icordebugprocess5-getarraylayout-method.md) .</span><span class="sxs-lookup"><span data-stu-id="fc0b3-118">If `type` is `ELEMENT_TYPE_STRING`, `ELEMENT_TYPE_ARRAY`, or `ELEMENT_TYPE_SZARRAY`, the size of objects of this type is variable, and you can pass the [COR_TYPEID](cor-typeid-structure.md) structure to the [ICorDebugProcess5::GetArrayLayout](icordebugprocess5-getarraylayout-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc0b3-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="fc0b3-119">Requirements</span></span>  

 <span data-ttu-id="fc0b3-120">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc0b3-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc0b3-121">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fc0b3-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fc0b3-122">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc0b3-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc0b3-123">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc0b3-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc0b3-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fc0b3-124">See also</span></span>

- [<span data-ttu-id="fc0b3-125">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="fc0b3-125">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="fc0b3-126">Débogage</span><span class="sxs-lookup"><span data-stu-id="fc0b3-126">Debugging</span></span>](index.md)
