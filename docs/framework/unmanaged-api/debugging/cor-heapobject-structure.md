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
ms.openlocfilehash: 54af02b48dabdf2042763954805f0d454323ac89
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726364"
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
  
## <a name="remarks"></a>Remarques  

 `COR_HEAPOBJECT` les instances peuvent être récupérées en énumérant un objet d’interface [icordebugheapenum,](icordebugheapenum-interface.md) rempli par l’appel de la méthode [ICorDebugProcess5 :: enumerateheap,](icordebugprocess5-enumerateheap-method.md) .  
  
 Une `COR_HEAPOBJECT` instance de fournit des informations sur un objet actif sur le tas managé, ou sur un objet qui n’est associé à aucun objet, mais qui n’a pas encore été collecté par le garbage collector.  
  
 Pour de meilleures performances, le `COR_HEAPOBJECT.address` champ est une `CORDB_ADDRESS` valeur plutôt que la valeur d’interface ICorDebugValue utilisée dans la plupart de l’API de débogage. Pour obtenir un objet ICorDebugValue pour une adresse d’objet donnée, vous pouvez passer la `CORDB_ADDRESS` valeur à la méthode [ICorDebugProcess5 :: GetObject](icordebugprocess5-getobject-method.md) .  
  
 Pour de meilleures performances, le `COR_HEAPOBJECT.type` champ est une `COR_TYPEID` valeur plutôt que la valeur d’interface ICorDebugType utilisée dans la plupart de l’API de débogage. Pour obtenir un objet ICorDebugType pour un ID de type donné, vous pouvez passer la `COR_TYPEID` valeur à la méthode [ICorDebugProcess5 :: gettypefortypeid,](icordebugprocess5-gettypefortypeid-method.md) .  
  
 La `COR_HEAPOBJECT` structure comprend une interface com avec comptage des références. Si vous récupérez une `COR_HEAPOBJECT` instance de l’énumérateur en appelant la méthode [icordebugheapenum, :: Next](icordebugheapenum-next-method.md) , vous devez libérer ultérieurement la référence.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de débogage](debugging-structures.md)
- [Débogage](index.md)
