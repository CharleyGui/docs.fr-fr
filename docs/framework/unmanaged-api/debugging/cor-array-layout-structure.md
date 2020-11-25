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
ms.openlocfilehash: 2ca6c89a671c4d7882e7cefdb820d07ac5636530
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727404"
---
# <a name="cor_array_layout-structure"></a>COR_ARRAY_LAYOUT, structure

Fournit des informations sur la disposition d'un objet Array en mémoire.  
  
## <a name="syntax"></a>Syntaxe  
  
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
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`componentID`|Identificateur du type d’objets contenu dans le tableau.|  
|`componentType`|Valeur d’énumération CorElementType qui indique si le composant est une référence garbage collection, une classe value ou une primitive.|  
|`firstElementOffset`|Offset du premier élément dans le tableau.|  
|`elementSize`|Taille de chaque élément.|  
|`countOffset`|Offset du nombre d’éléments dans le tableau.|  
|`rankSize`|Taille du rang, en octets.|  
|`numRanks`|Nombre de rangs dans le tableau.|  
|`rankOffset`|Décalage à partir duquel les rangs commencent.|  
  
## <a name="remarks"></a>Remarques  

 Le `rankSize` champ spécifie la taille d’un rang dans un tableau multidimensionnel. Il est également exact pour les tableaux unidimensionnels.  
  
 La valeur de `numRanks` est 1 pour un tableau unidimensionnel et `N` pour un tableau multidimensionnel de `N` dimensions.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de débogage](debugging-structures.md)
- [Débogage](index.md)
