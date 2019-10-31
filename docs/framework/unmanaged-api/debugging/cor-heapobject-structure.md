---
title: COR_HEAPOBJECT, structure
ms.date: 03/30/2017
api_name:
- COR_HEAPOBJECT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_HEAPOBJECT
helpviewer_keywords:
- COR_HEAPOBJECT structure [.NET Framework debugging]
ms.assetid: a92fdf95-492b-49ae-a741-2186e5c1d7c5
topic_type:
- apiref
ms.openlocfilehash: 270360a8950197eca14e02a60554659e5ac7b91c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099080"
---
# <a name="cor_heapobject-structure"></a>COR_HEAPOBJECT, structure
Fournit des informations à propos d’un objet sur le tas managé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _COR_HEAPOBJECT {  
    CORDB_ADDRESS address;    
    ULONG64 size;             
    COR_TYPEID type;          
} COR_HEAPOBJECT;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`address`|Adresse de l’objet en mémoire.|  
|`size`|Taille totale de l’objet, en octets.|  
|`type`|Jeton [COR_TYPEID](cor-typeid-structure.md) qui représente le type de l’objet.|  
  
## <a name="remarks"></a>Notes  
 `COR_HEAPOBJECT` instances peuvent être récupérées en énumérant un objet d’interface [icordebugheapenum,](icordebugheapenum-interface.md) rempli par l’appel de la méthode [ICorDebugProcess5 :: enumerateheap,](icordebugprocess5-enumerateheap-method.md) .  
  
 Une instance `COR_HEAPOBJECT` fournit des informations sur un objet actif sur le tas managé, ou sur un objet qui n’est associé à aucun objet, mais qui n’a pas encore été collecté par le garbage collector.  
  
 Pour de meilleures performances, le champ `COR_HEAPOBJECT.address` est une valeur `CORDB_ADDRESS` plutôt que la valeur d’interface ICorDebugValue utilisée dans la plupart de l’API de débogage. Pour obtenir un objet ICorDebugValue pour une adresse d’objet donnée, vous pouvez passer la valeur `CORDB_ADDRESS` à la méthode [ICorDebugProcess5 :: GetObject](icordebugprocess5-getobject-method.md) .  
  
 Pour de meilleures performances, le champ `COR_HEAPOBJECT.type` est une valeur `COR_TYPEID` plutôt que la valeur d’interface ICorDebugType utilisée dans la plupart de l’API de débogage. Pour obtenir un objet ICorDebugType pour un ID de type donné, vous pouvez passer la valeur `COR_TYPEID` à la méthode [ICorDebugProcess5 :: gettypefortypeid,](icordebugprocess5-gettypefortypeid-method.md) .  
  
 La structure `COR_HEAPOBJECT` comprend une interface COM avec comptage des références. Si vous récupérez une instance de `COR_HEAPOBJECT` à partir de l’énumérateur en appelant la méthode [icordebugheapenum, :: Next](icordebugheapenum-next-method.md) , vous devez libérer ultérieurement la référence.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de débogage](debugging-structures.md)
- [Débogage](index.md)
