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
# <a name="cor_type_layout-structure"></a>COR_TYPE_LAYOUT, structure

Fournit des informations sur la disposition d'un objet en mémoire.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct COR_TYPE_LAYOUT {  
    COR_TYPEID parentID;  
    ULONG32 objectSize;  
    ULONG32 numFields;  
    ULONG32 boxOffset;  
    CorElementType type;  
} COR_TYPE_LAYOUT;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`parentID`|Identificateur du type parent à ce type. Il s’agit de l’ID de type NULL (TOKEN1 = 0, Token2 = 0) si l’ID de type correspond à <xref:System.Object?displayProperty=nameWithType> .|  
|`objectSize`|Taille de base d’un objet de ce type. Il s’agit de la taille totale des objets de taille non variable.|  
|`numFields`|Nombre de champs inclus dans les objets de ce type.|  
|`boxOffset`|Si ce type est boxed, il s’agit du décalage de début des champs d’un objet. Ce champ est valide uniquement pour les types de valeur tels que les primitives et les structures.|  
|`type`|CorElementType auquel ce type appartient.|  
  
## <a name="remarks"></a>Remarques  

 Si `numFields` est supérieur à zéro, vous pouvez appeler la méthode [ICorDebugProcess5 :: gettypefields,](icordebugprocess5-gettypefields-method.md) pour obtenir des informations sur les champs de ce type. Si `type` est `ELEMENT_TYPE_STRING` , `ELEMENT_TYPE_ARRAY` ou `ELEMENT_TYPE_SZARRAY` , la taille des objets de ce type est variable, et vous pouvez passer la structure [COR_TYPEID](cor-typeid-structure.md) à la méthode [ICorDebugProcess5 :: getarraylayout,](icordebugprocess5-getarraylayout-method.md) .  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de débogage](debugging-structures.md)
- [Débogage](index.md)
