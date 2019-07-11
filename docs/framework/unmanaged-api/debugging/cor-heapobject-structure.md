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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a236103b8ca1501ae4c9109c1fd9e78865ab9c9c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740603"
---
# <a name="corheapobject-structure"></a>COR_HEAPOBJECT, structure
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
|`size`|La taille totale de l’objet, en octets.|  
|`type`|Un [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) jeton qui représente le type de l’objet.|  
  
## <a name="remarks"></a>Notes  
 `COR_HEAPOBJECT` instances peuvent être récupérées en énumérant un [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) objet d’interface qui est remplie en appelant le [ICorDebugProcess5::EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) (méthode).  
  
 Un `COR_HEAPOBJECT` instance fournit des informations sur un objet dynamique sur le tas managé, ou sur un objet qui est associé à aucune racine par n’importe quel objet, mais n’a pas encore été collecté par le garbage collector.  
  
 Pour de meilleures performances, le `COR_HEAPOBJECT.address` champ est un `CORDB_ADDRESS` valeur plutôt que ICorDebugValue interface valeur utilisée dans une grande partie de l’API de débogage. Pour obtenir un objet ICorDebugValue pour une adresse de l’objet donné, vous pouvez passer le `CORDB_ADDRESS` valeur pour le [ICorDebugProcess5::GetObject](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md) (méthode).  
  
 Pour de meilleures performances, le `COR_HEAPOBJECT.type` champ est un `COR_TYPEID` valeur plutôt que de ICorDebugType interface valeur utilisée dans une grande partie de l’API de débogage. Pour obtenir un objet ICorDebugType à un ID de type donné, vous pouvez passer le `COR_TYPEID` valeur pour le [ICorDebugProcess5::GetTypeForTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md) (méthode).  
  
 Le `COR_HEAPOBJECT` structure inclut une interface COM contenant des références. Si vous récupérez un `COR_HEAPOBJECT` instance à partir de l’énumérateur en appelant le [ICorDebugHeapEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) (méthode), vous devez libérer par la suite de la référence.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Débogage](../../../../docs/framework/unmanaged-api/debugging/index.md)
