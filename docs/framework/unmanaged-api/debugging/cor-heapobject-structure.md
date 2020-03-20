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
ms.openlocfilehash: efb3d913e1d8ef0c486d7e5e1d9777ae7d88bc71
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179336"
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
|`address`|L’adresse de l’objet en mémoire.|  
|`size`|La taille totale de l’objet, dans les octets.|  
|`type`|Un [COR_TYPEID](cor-typeid-structure.md) jeton qui représente le type de l’objet.|  
  
## <a name="remarks"></a>Notes   
 `COR_HEAPOBJECT`les instances peuvent être récupérées en énumérant un objet d’interface [ICorDebugHeapEnum](icordebugheapenum-interface.md) qui est peuplé en appelant le [ICorDebugProcess5::Méthode D’énumérationheap.](icordebugprocess5-enumerateheap-method.md)  
  
 Une `COR_HEAPOBJECT` instance fournit des informations soit sur un objet en direct sur le tas géré, soit sur un objet qui n’est pas enraciné par un objet mais qui n’a pas encore été recueilli par le collecteur d’ordures.  
  
 Pour de meilleures `COR_HEAPOBJECT.address` performances, `CORDB_ADDRESS` le champ est une valeur plutôt que la valeur iCorDebugValue interface utilisée dans une grande partie de l’API débogage. Pour obtenir un objet ICorDebugValue pour une adresse `CORDB_ADDRESS` d’objet donnée, vous pouvez transmettre la valeur à la méthode [ICorDebugProcess5::GetObject.](icordebugprocess5-getobject-method.md)  
  
 Pour de meilleures `COR_HEAPOBJECT.type` performances, `COR_TYPEID` le champ est une valeur plutôt que la valeur iCorDebugType interface utilisée dans une grande partie de l’API débogage. Pour obtenir un objet ICorDebugType pour un ID `COR_TYPEID` de type donné, vous pouvez transmettre la valeur à la méthode [ICorDebugProcess5::GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) méthode.  
  
 La `COR_HEAPOBJECT` structure comprend une interface COM comptée de référence. Si vous `COR_HEAPOBJECT` récupérez une instance de l’enumérateur en appelant [l’ICorDebugHeapEnum: :Méthode suivante,](icordebugheapenum-next-method.md) vous devez par la suite libérer la référence.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de débogage](debugging-structures.md)
- [Débogage](index.md)
