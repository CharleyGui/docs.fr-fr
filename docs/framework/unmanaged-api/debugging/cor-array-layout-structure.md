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
|`componentID`|L’identifiant du type d’objets que contient le tableau.|  
|`componentType`|Une valeur d’énumération De CorElementType qui indique si le composant est une référence de collecte d’ordures, une classe de valeur, ou un primitif.|  
|`firstElementOffset`|Le décalage au premier élément du tableau.|  
|`elementSize`|La taille de chaque élément.|  
|`countOffset`|Le décalage au nombre d’éléments dans le tableau.|  
|`rankSize`|La taille du rang, dans les octets.|  
|`numRanks`|Le nombre de rangs dans le tableau.|  
|`rankOffset`|Le décalage auquel les rangs commencent.|  
  
## <a name="remarks"></a>Notes   
 Le `rankSize` champ spécifie la taille d’un rang dans un tableau multidimensionnel. Il est également exact pour les tableaux unidimensionnels.  
  
 La valeur `numRanks` de 1 pour un `N` tableau unidimensionnel et `N` pour un éventail multidimensionnel de dimensions.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de débogage](debugging-structures.md)
- [Débogage](index.md)
