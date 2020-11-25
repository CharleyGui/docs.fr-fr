---
title: COR_TYPEID, structure
ms.date: 03/30/2017
api_name:
- COR_TYPEID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_TYPEID
helpviewer_keywords:
- COR_TYPEID structure [.NET Framework debugging]
ms.assetid: 1e172b14-ee22-4943-b3b8-3740e7bdcd2e
topic_type:
- apiref
ms.openlocfilehash: 5eeb5aef7edaa23385190a309144e1477da741e8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697439"
---
# <a name="cor_typeid-structure"></a>COR_TYPEID, structure

Contient un identificateur de type.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct COR_TYPEID{  
    UINT64 token1;  
    UINT64 token2;  
} COR_TYPEID;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`token1`|Premier jeton.|  
|`token2`|Deuxième jeton.|  
  
## <a name="remarks"></a>Remarques  

 La `COR_TYPEID` structure est retournée par un certain nombre de méthodes de débogage qui fournissent des informations sur les objets qui doivent être récupérés par le garbage collector. Il peut ensuite être passé comme argument à d’autres méthodes de débogage qui fournissent des informations supplémentaires sur cet élément. Par exemple, en énumérant un objet [icordebugheapenum,](icordebugheapenum-interface.md) , vous pouvez récupérer des objets [COR_HEAPOBJECT](cor-heapobject-structure.md) individuels qui représentent des objets individuels sur le tas managé. Vous pouvez ensuite passer la `COR_TYPEID` valeur du `COR_HEAPOBJECT.type` champ à la méthode [ICorDebugProcess5 :: gettypefortypeid,](icordebugprocess5-gettypefortypeid-method.md) pour récupérer un objet ICorDebugType qui fournit des informations de type sur l’objet.  
  
 Un `COR_TYPEID` objet est destiné à être opaque. Ses champs individuels ne doivent pas être accessibles ou manipulés. Son unique utilisation est l’identificateur qui est fourni en tant que `out` paramètre dans un appel de méthode et qui peut, à son tour, être passé à d’autres méthodes pour fournir des informations supplémentaires.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de débogage](debugging-structures.md)
- [Débogage](index.md)
