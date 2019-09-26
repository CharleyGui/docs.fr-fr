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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d76fa4b2352da18b5ef0e547ebc4e2e99d980b8
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71273994"
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
  
## <a name="remarks"></a>Notes  
 La `COR_TYPEID` structure est retournée par un certain nombre de méthodes de débogage qui fournissent des informations sur les objets qui doivent être récupérés par le garbage collector. Il peut ensuite être passé comme argument à d’autres méthodes de débogage qui fournissent des informations supplémentaires sur cet élément. Par exemple, en énumérant un objet [icordebugheapenum,](icordebugheapenum-interface.md) , vous pouvez récupérer des objets [COR_HEAPOBJECT](cor-heapobject-structure.md) individuels qui représentent des objets individuels sur le tas managé. Vous pouvez ensuite passer la `COR_TYPEID` valeur `COR_HEAPOBJECT.type` du champ à la méthode [ICorDebugProcess5 :: gettypefortypeid,](icordebugprocess5-gettypefortypeid-method.md) pour récupérer un objet ICorDebugType qui fournit des informations de type sur l’objet.  
  
 Un `COR_TYPEID` objet est destiné à être opaque. Ses champs individuels ne doivent pas être accessibles ou manipulés. Son unique utilisation est l’identificateur qui est fourni en tant `out` que paramètre dans un appel de méthode et qui peut, à son tour, être passé à d’autres méthodes pour fournir des informations supplémentaires.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug. idl, CorDebug. h  
  
 **Bibliothèque** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de débogage](debugging-structures.md)
- [Débogage](index.md)
