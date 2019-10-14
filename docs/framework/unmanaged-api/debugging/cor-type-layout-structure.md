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
ms.openlocfilehash: 6bd274b1eb14532629580e777288317186544912
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274162"
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
|`parentID`|Identificateur du type parent à ce type. Il s’agit de l’ID de type NULL (TOKEN1 = 0, Token2 = 0) si l’ID de <xref:System.Object?displayProperty=nameWithType>type correspond à.|  
|`objectSize`|Taille de base d’un objet de ce type. Il s’agit de la taille totale des objets de taille non variable.|  
|`numFields`|Nombre de champs inclus dans les objets de ce type.|  
|`boxOffset`|Si ce type est boxed, il s’agit du décalage de début des champs d’un objet. Ce champ est valide uniquement pour les types de valeur tels que les primitives et les structures.|  
|`type`|CorElementType auquel ce type appartient.|  
  
## <a name="remarks"></a>Notes  
 Si `numFields` est supérieur à zéro, vous pouvez appeler la méthode [ICorDebugProcess5 :: gettypefields,](icordebugprocess5-gettypefields-method.md) pour obtenir des informations sur les champs de ce type. Si `type` est `ELEMENT_TYPE_STRING`, `ELEMENT_TYPE_ARRAY` ou `ELEMENT_TYPE_SZARRAY`, la taille des objets de ce type est variable, et vous pouvez passer la structure [COR_TYPEID](cor-typeid-structure.md) à la méthode [ICorDebugProcess5 :: getarraylayout](icordebugprocess5-getarraylayout-method.md).  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug. idl, CorDebug. h  
  
 **Bibliothèque** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de débogage](debugging-structures.md)
- [Débogage](index.md)
