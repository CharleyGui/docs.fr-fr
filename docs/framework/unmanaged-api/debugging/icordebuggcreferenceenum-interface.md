---
title: ICorDebugGCReferenceEnum, interface
ms.date: 03/30/2017
api_name:
- ICorDebugGCReferenceEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGCReferenceEnum
helpviewer_keywords:
- ICorDebugGCReferenceEnum interface [.NET Framework debugging]
ms.assetid: 5f3c91c9-c035-454f-96cc-011cab1ea06b
topic_type:
- apiref
ms.openlocfilehash: 49f89f7d36e74b1fa5921230d7dc6d271d4c0883
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134631"
---
# <a name="icordebuggcreferenceenum-interface"></a>ICorDebugGCReferenceEnum, interface
Fournit un énumérateur pour les objets qui sont récupérés par le récupérateur de mémoire.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Next, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md)|Obtient le nombre spécifié d’instances [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) qui contiennent des informations sur les objets qui seront récupérés par le garbage collector.|  
  
## <a name="remarks"></a>Notes  
 L’interface `ICorDebugGCReferenceEnum` implémente l’interface « ICorDebugEnum ».  
  
 Une instance de `ICorDebugGCReferenceEnum` est remplie avec des instances [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) en appelant la méthode [ICorDebugProcess5 :: enumerategcreferences,](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) . Les objets [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) peuvent être énumérés en appelant la méthode [ICorDebugGCReference :: Next](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md) .  
  
 Les objets [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) de la collection remplie par cette méthode représentent trois types d’objets :  
  
- Objets de toutes les piles managées. Cela comprend les références dynamiques en code managé, ainsi que les objets créés par l’common language runtime.  
  
- Objets de la table de handles. Cela comprend des références fortes (`HNDTYPE_STRONG` et `HNDTYPE_REFCOUNT`) et des variables statiques dans un module.  
  
- Objets de la file d’attente du finaliseur. Le finaliseur met les objets racine en file d’attente jusqu’à l’exécution du finaliseur.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
