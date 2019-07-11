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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1793547cfc0d9637352b62ff47beee41e9f5ac5c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740510"
---
# <a name="cortypelayout-structure"></a><span data-ttu-id="51317-102">COR_TYPE_LAYOUT, structure</span><span class="sxs-lookup"><span data-stu-id="51317-102">COR_TYPE_LAYOUT Structure</span></span>
<span data-ttu-id="51317-103">Fournit des informations sur la disposition d'un objet en mémoire.</span><span class="sxs-lookup"><span data-stu-id="51317-103">Provides information about the layout of an object in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51317-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51317-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_TYPE_LAYOUT {  
    COR_TYPEID parentID;  
    ULONG32 objectSize;  
    ULONG32 numFields;  
    ULONG32 boxOffset;  
    CorElementType type;  
} COR_TYPE_LAYOUT;  
```  
  
## <a name="members"></a><span data-ttu-id="51317-105">Membres</span><span class="sxs-lookup"><span data-stu-id="51317-105">Members</span></span>  
  
|<span data-ttu-id="51317-106">Membre</span><span class="sxs-lookup"><span data-stu-id="51317-106">Member</span></span>|<span data-ttu-id="51317-107">Description</span><span class="sxs-lookup"><span data-stu-id="51317-107">Description</span></span>|  
|------------|-----------------|  
|`parentID`|<span data-ttu-id="51317-108">Identificateur de type parent pour ce type.</span><span class="sxs-lookup"><span data-stu-id="51317-108">The identifier of the parent type to this type.</span></span> <span data-ttu-id="51317-109">Il s’agit de l’id de type NULL (token1 = 0, token2 = 0) si l’id de type correspond à <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="51317-109">This will be the NULL type id (token1= 0, token2 = 0) if the type id corresponds to <xref:System.Object?displayProperty=nameWithType>.</span></span>|  
|`objectSize`|<span data-ttu-id="51317-110">La taille de base d’un objet de ce type.</span><span class="sxs-lookup"><span data-stu-id="51317-110">The base size of an object of this type.</span></span> <span data-ttu-id="51317-111">Il s’agit de la taille totale des objets de taille non variable.</span><span class="sxs-lookup"><span data-stu-id="51317-111">This is the total size for non-variable sized objects.</span></span>|  
|`numFields`|<span data-ttu-id="51317-112">Le nombre de champs inclus dans les objets de ce type.</span><span class="sxs-lookup"><span data-stu-id="51317-112">The number of fields included in objects of this type.</span></span>|  
|`boxOffset`|<span data-ttu-id="51317-113">Si ce type est boxed, le début du décalage de champs d’un objet.</span><span class="sxs-lookup"><span data-stu-id="51317-113">If this type is boxed, the beginning offset of an object's fields.</span></span> <span data-ttu-id="51317-114">Ce champ est valide uniquement pour les types valeur tels que des primitives et des structures.</span><span class="sxs-lookup"><span data-stu-id="51317-114">This field is valid only for value types such as primitives and structures.</span></span>|  
|`type`|<span data-ttu-id="51317-115">CorElementType auquel appartient ce type.</span><span class="sxs-lookup"><span data-stu-id="51317-115">The CorElementType to which this type belongs.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51317-116">Notes</span><span class="sxs-lookup"><span data-stu-id="51317-116">Remarks</span></span>  
 <span data-ttu-id="51317-117">Si `numFields` est supérieure à zéro, vous pouvez appeler la [ICorDebugProcess5::GetTypeFields](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md) méthode pour obtenir des informations sur les champs de ce type.</span><span class="sxs-lookup"><span data-stu-id="51317-117">If `numFields` is greater than zero, you can call the [ICorDebugProcess5::GetTypeFields](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md) method to obtain information about the fields in this type.</span></span> <span data-ttu-id="51317-118">Si `type` est `ELEMENT_TYPE_STRING`, `ELEMENT_TYPE_ARRAY`, ou `ELEMENT_TYPE_SZARRAY`, la taille des objets de ce type est variable, et vous pouvez passer le [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) structure le [ICorDebugProcess5::GetArrayLayout ](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="51317-118">If `type` is `ELEMENT_TYPE_STRING`, `ELEMENT_TYPE_ARRAY`, or `ELEMENT_TYPE_SZARRAY`, the size of objects of this type is variable, and you can pass the [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) structure to the [ICorDebugProcess5::GetArrayLayout](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51317-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="51317-119">Requirements</span></span>  
 <span data-ttu-id="51317-120">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51317-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51317-121">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="51317-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="51317-122">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="51317-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51317-123">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51317-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51317-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="51317-124">See also</span></span>

- [<span data-ttu-id="51317-125">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="51317-125">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="51317-126">Débogage</span><span class="sxs-lookup"><span data-stu-id="51317-126">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
