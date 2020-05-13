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
ms.openlocfilehash: 5650a7e6e6cb0108f0d043914ea94debe2b703bf
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213099"
---
# <a name="icordebuggcreferenceenum-interface"></a>ICorDebugGCReferenceEnum, interface
Fournit un énumérateur pour les objets qui sont récupérés par le récupérateur de mémoire.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Next, méthode](icordebuggcreferenceenum-next-method.md)|Obtient le nombre spécifié d’instances de [COR_GC_REFERENCE](cor-gc-reference-structure.md) qui contiennent des informations sur les objets qui feront l’objet d’un garbage collection.|  
  
## <a name="remarks"></a>Remarks  
 L' `ICorDebugGCReferenceEnum` interface implémente l’interface « ICorDebugEnum ».  
  
 Une `ICorDebugGCReferenceEnum` instance est remplie avec [COR_GC_REFERENCE](cor-gc-reference-structure.md) instances en appelant la méthode [ICorDebugProcess5 :: enumerategcreferences,](icordebugprocess5-enumerategcreferences-method.md) . Les objets [COR_GC_REFERENCE](cor-gc-reference-structure.md) peuvent être énumérés en appelant la méthode [ICorDebugGCReference :: Next](icordebuggcreferenceenum-next-method.md) .  
  
 Les objets [COR_GC_REFERENCE](cor-gc-reference-structure.md) dans la collection remplie par cette méthode représentent trois types d’objets :  
  
- Objets de toutes les piles managées. Cela comprend les références dynamiques en code managé, ainsi que les objets créés par l’common language runtime.  
  
- Objets de la table de handles. Cela comprend des références fortes ( `HNDTYPE_STRONG` et `HNDTYPE_REFCOUNT` ) et des variables statiques dans un module.  
  
- Objets de la file d’attente du finaliseur. Le finaliseur met les objets racine en file d’attente jusqu’à l’exécution du finaliseur.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
