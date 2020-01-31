---
title: CorGCReferenceType, énumération
ms.date: 03/30/2017
api_name:
- CorGCReferenceType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorGCReferenceType
helpviewer_keywords:
- CorGCReferenceType
ms.assetid: d9f16439-5a36-4474-8ffd-4f0b2c2bb686
topic_type:
- apiref
ms.openlocfilehash: 17d47b6242bb12ff5ca3cfbde3e4ec183b9c19fc
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793875"
---
# <a name="corgcreferencetype-enumeration"></a>CorGCReferenceType, énumération
Identifie la source d'un objet pour lequel l'espace occupé en mémoire peut être récupéré.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    CorHandleStrong = 1,  
    CorHandleStrongPinning = 2,  
    CorHandleWeakShort = 4,  
    CorHandleWeakRefCount = 8,  
    CorHandleStrongRefCount = 32,  
    CorHandleStrongDependent = 64,  
    CorHandleStrongAsyncPinned = 128,  
    CorHandleStrongSizedByref = 256,  
  
    CorReferenceStack = 0x80000001,  
    CorReferenceFinalizer = 0x80000002,  
  
    CorHandleStrongOnly = 0x1E3,  
    CorHandleWeakOnly = 0xC,  
    CorHandleAll = 0x7FFFFFFF  
} CorGCReferenceType  
```  
  
## <a name="members"></a>Members  
  
|Nom du membre|Description|  
|-----------------|-----------------|  
|`CorHandleStrong`|Handle à une référence forte tiré de la table de handles d'objets.|  
|`CorHandleStrongPinning`|Handle d’une référence forte épinglée de la table de handles d’objets.|  
|`CorHandleWeakShort`|Handle d’une référence faible à partir de la table de handles d’objets.|  
|`CorHandleWeakRefCount`|Handle d’un objet de référence faible à partir de la table de handles d’objets.|  
|`CorHandleStrongRefCount`|Handle d’un objet compté en référence à partir de la table de handles d’objets.|  
|`CorHandleStrongDependent`|Handle vers un objet dépendant de la table de handles d’objets.|  
|`CorHandleStrongAsyncPinned`|Objet épinglé asynchrone tiré de la table de handles d'objets.|  
|`CorHandleStrongSizedByref`|Handle fort qui conserve une taille approximative de la fermeture collective de tous les objets et racines d’objets au moment du Garbage Collection.|  
|`CorReferenceStack`|Référence à partir de la pile managée.|  
|`CorReferenceFinalizer`|Référence à partir de la file d’attente du finaliseur.|  
|CorHandleStrongOnly|Retourne uniquement les références fortes de la table de handles. Cette valeur est utilisée uniquement par la méthode [ICorDebugProcess5 :: enumeratehandles,](icordebugprocess5-enumeratehandles-method.md) .|  
|`CorHandleWeakOnly`|Retourne uniquement les références faibles de la table de handles. Cette valeur est utilisée uniquement par la méthode [ICorDebugProcess5 :: enumeratehandles,](icordebugprocess5-enumeratehandles-method.md) .|  
|`CorHandleAll`|Retourne toutes les références de la table de handles. Cette valeur est utilisée uniquement par la méthode [ICorDebugProcess5 :: enumeratehandles,](icordebugprocess5-enumeratehandles-method.md) .|  
  
## <a name="remarks"></a>Notes  
 L’énumération `CorGCReferenceType` est utilisée comme suit :  
  
- En tant que valeur du champ `type` de la structure [COR_GC_REFERENCE](cor-gc-reference-structure.md) , elle indique la source d’une référence ou d’un handle.  
  
- En tant qu’argument `types` de la méthode [ICorDebugProcess5 :: enumeratehandles,](icordebugprocess5-enumeratehandles-method.md) , il spécifie les types de handles à inclure dans l’énumération.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de débogage](debugging-enumerations.md)
