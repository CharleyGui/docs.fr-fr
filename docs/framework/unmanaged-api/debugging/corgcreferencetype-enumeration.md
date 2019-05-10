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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 690d556eb3991747d1627bae63b9c59ca68daaaa
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64616217"
---
# <a name="corgcreferencetype-enumeration"></a>CorGCReferenceType, énumération
Identifie la source d'un objet pour lequel l'espace occupé en mémoire peut être récupéré.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
## <a name="members"></a>Membres  
  
|Nom de membre|Description|  
|-----------------|-----------------|  
|`CorHandleStrong`|Handle à une référence forte tiré de la table de handles d'objets.|  
|`CorHandleStrongPinning`|Handle vers une référence forte épinglée à partir de la table de handles d’objet.|  
|`CorHandleWeakShort`|Handle vers une référence faible à partir de la table de handles d’objet.|  
|`CorHandleWeakRefCount`|Handle vers un objet contenant des références faible à partir de la table de handles d’objet.|  
|`CorHandleStrongRefCount`|Handle vers un objet contenant des références à partir de la table de handles d’objet.|  
|`CorHandleStrongDependent`|Handle vers un objet dépendant à partir de la table de handles d’objet.|  
|`CorHandleStrongAsyncPinned`|Objet épinglé asynchrone tiré de la table de handles d'objets.|  
|`CorHandleStrongSizedByref`|Handle fort qui conserve une taille approximative de la fermeture collective de tous les objets et racines d’objets au moment du Garbage Collection.|  
|`CorReferenceStack`|Une référence à partir de la pile gérée.|  
|`CorReferenceFinalizer`|Une référence à partir de la file d’attente du finaliseur.|  
|CorHandleStrongOnly|Retourner uniquement les références fortes à partir de la table de handles. Cette valeur est utilisée par le [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) méthode uniquement.|  
|`CorHandleWeakOnly`|Retourner uniquement les références faibles à partir de la table de handles. Cette valeur est utilisée par le [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) méthode uniquement.|  
|`CorHandleAll`|Retourner toutes les références à partir de la table de handles. Cette valeur est utilisée par le [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) méthode uniquement.|  
  
## <a name="remarks"></a>Notes  
 Le `CorGCReferenceType` énumération est utilisée comme suit :  
  
- En tant que la valeur de la `type` champ la [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) structure, il indique la source d’une référence ou un handle.  
  
- Comme le `types` l’argument de la [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) méthode, il spécifie les types de handles à inclure dans l’énumération.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
