---
title: ICorDebugHeapSegmentEnum, interface
ms.date: 03/30/2017
api_name:
- ICorDebugHealRegionEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapSegmentEnum
helpviewer_keywords:
- ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 20fc1b9d-e228-4107-bd76-53934c1724b9
topic_type:
- apiref
ms.openlocfilehash: 42126d15c64175f35bba89a1ab6abacc64128012
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704628"
---
# <a name="icordebugheapsegmentenum-interface"></a>ICorDebugHeapSegmentEnum, interface

Fournit un énumérateur pour les régions de mémoire du tas managé. Cette interface est une sous-classe de l'interface ICorDebugEnum.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Next, méthode](icordebugheapsegmentenum-next-method.md)|Obtient le nombre spécifié d’instances de [COR_SEGMENT](cor-segment-structure.md) qui contiennent des informations sur les régions du tas managé.|  
  
## <a name="remarks"></a>Remarques  

 L' `ICorDebugHeapSegmentEnum` interface implémente l’interface ICorDebugEnum.  
  
 Une `ICorDebugHeapSegmentEnum` instance est remplie avec [COR_SEGMENT](cor-segment-structure.md) instances en appelant la méthode [ICorDebugProcess5 :: enumerateheapregions,](icordebugprocess5-enumerateheapregions-method.md) . Les objets [COR_SEGMENT](cor-segment-structure.md) de la collection peuvent être énumérés en appelant la méthode [Icordebugheapsegmentenum, :: Next](icordebugheapsegmentenum-next-method.md) .  
  
 Un `ICorDebugHeapSegmentEnum` objet collection énumère toutes les régions de mémoire qui peuvent contenir des objets managés, mais il ne garantit pas que les objets managés résident réellement dans ces régions. Elle peut inclure des informations sur les régions de mémoire vides ou réservées.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
