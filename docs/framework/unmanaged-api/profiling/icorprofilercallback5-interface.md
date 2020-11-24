---
title: ICorProfilerCallback5, interface
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback5
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback5
helpviewer_keywords:
- ICorProfilerCallback5 interface [.NET Framework profiling]
ms.assetid: 61d2e9ef-5f1f-4771-8847-239616e35d84
topic_type:
- apiref
ms.openlocfilehash: 8e94aebc489fff1c81593e54b17c471e7228d810
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689288"
---
# <a name="icorprofilercallback5-interface"></a>ICorProfilerCallback5, interface

Complète les informations pour aider un profileur à identifier la fermeture complète d’objets actifs, lorsqu’il est utilisé avec la méthode [ICorProfilerCallback :: RootReferences](icorprofilercallback-rootreferences-method.md) ou [ICorProfilerCallback2 :: RootReferences2](icorprofilercallback2-rootreferences2-method.md) avec les méthodes [ICorProfilerCallback :: ObjectReferences](icorprofilercallback-objectreferences-method.md) et [conditionalweaktableelementreferences,](icorprofilercallback5-conditionalweaktableelementreferences-method.md) .  
  
 `ICorProfilerCallback5` doit être implémentée par un profileur de mémoire managée pour s'abonner aux notifications relatives aux handles dépendants.  
  
## <a name="remarks"></a>Remarques  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[ConditionalWeakTableElementReferences, méthode](icorprofilercallback5-conditionalweaktableelementreferences-method.md)|Identifie la fermeture transitive des objets référencés par ces racines via les références des champs des membres directs et via les dépendances de `ConditionalWeakTable`.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de profilage](profiling-interfaces.md)
- [ICorProfilerCallback2, interface](icorprofilercallback2-interface.md)
