---
title: ICorDebugHeapEnum, interface
ms.date: 03/30/2017
api_name:
- ICorDebugHeapEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapEnum
helpviewer_keywords:
- ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 99cbc1eb-d539-4f76-a0d8-b93348112f14
topic_type:
- apiref
ms.openlocfilehash: 312052fcd683acbccb9ca616992bd635490aa2a5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724362"
---
# <a name="icordebugheapenum-interface"></a>ICorDebugHeapEnum, interface

Fournit un énumérateur pour les objets sur le tas managé. Cette interface est une sous-classe de l'interface ICorDebugEnum.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Next, méthode](icordebugheapenum-next-method.md)|Obtient le nombre spécifié d’instances [COR_HEAPOBJECT](cor-heapobject-structure.md) qui contiennent des informations sur les objets sur le tas managé.|  
  
## <a name="remarks"></a>Remarques  

 L' `ICorDebugHeapEnum` interface implémente l’interface ICorDebugEnum.  
  
 Une `ICorDebugHeapEnum` instance est remplie avec [COR_HEAPOBJECT](cor-heapobject-structure.md) instances en appelant la méthode [ICorDebugProcess5 :: enumerateheap,](icordebugprocess5-enumerateheap-method.md) . Chaque [COR_HEAPOBJECT](cor-heapobject-structure.md) instance de la collection représente soit un objet actif sur le tas, soit un objet qui n’est associé à aucun objet, mais n’a pas encore été collecté par le récupérateur de mémoire. Les objets [COR_HEAPOBJECT](cor-heapobject-structure.md) de la collection peuvent être énumérés en appelant la méthode [Icordebugheapenum, :: Next](icordebugheapenum-next-method.md) .  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
