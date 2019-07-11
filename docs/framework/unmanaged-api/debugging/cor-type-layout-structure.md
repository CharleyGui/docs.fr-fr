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
# <a name="cortypelayout-structure"></a>COR_TYPE_LAYOUT, structure
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
|`parentID`|Identificateur de type parent pour ce type. Il s’agit de l’id de type NULL (token1 = 0, token2 = 0) si l’id de type correspond à <xref:System.Object?displayProperty=nameWithType>.|  
|`objectSize`|La taille de base d’un objet de ce type. Il s’agit de la taille totale des objets de taille non variable.|  
|`numFields`|Le nombre de champs inclus dans les objets de ce type.|  
|`boxOffset`|Si ce type est boxed, le début du décalage de champs d’un objet. Ce champ est valide uniquement pour les types valeur tels que des primitives et des structures.|  
|`type`|CorElementType auquel appartient ce type.|  
  
## <a name="remarks"></a>Notes  
 Si `numFields` est supérieure à zéro, vous pouvez appeler la [ICorDebugProcess5::GetTypeFields](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md) méthode pour obtenir des informations sur les champs de ce type. Si `type` est `ELEMENT_TYPE_STRING`, `ELEMENT_TYPE_ARRAY`, ou `ELEMENT_TYPE_SZARRAY`, la taille des objets de ce type est variable, et vous pouvez passer le [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) structure le [ICorDebugProcess5::GetArrayLayout ](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md) (méthode).  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Débogage](../../../../docs/framework/unmanaged-api/debugging/index.md)
