---
title: ICorProfilerCallback2, interface
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2
helpviewer_keywords:
- ICorProfilerCallback2 interface [.NET Framework profiling]
ms.assetid: 4a261dba-450d-4f1f-8d98-865b58bfc992
topic_type:
- apiref
ms.openlocfilehash: 597a3dfecd42e206c98974093fa2417eba570f6a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729462"
---
# <a name="icorprofilercallback2-interface"></a>ICorProfilerCallback2, interface

Fournit des méthodes qui sont utilisées par le common language runtime (CLR) pour notifier un profileur de code lorsque les événements auxquels le profileur s’est abonné se produisent. L' `ICorProfilerCallback2` interface est une extension de l’interface [ICorProfilerCallback](icorprofilercallback-interface.md) . Autrement dit, il fournit de nouveaux rappels introduits dans la version 2,0 de .NET Framework.  
  
> [!NOTE]
> Chaque implémentation de méthode doit retourner un HRESULT ayant la valeur S_OK en cas de réussite ou E_FAIL en cas d’échec. Actuellement, le CLR ignore le HRESULT retourné par chaque rappel, à l’exception de [ICorProfilerCallback :: ObjectReferences](icorprofilercallback-objectreferences-method.md).  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[FinalizeableObjectQueued, méthode](icorprofilercallback2-finalizeableobjectqueued-method.md)|Notifie le profileur de code qu’un objet avec un finaliseur a été mis en file d’attente dans le thread finaliseur pour l’exécution de sa `Finalize` méthode.|  
|[GarbageCollectionFinished, méthode](icorprofilercallback2-garbagecollectionfinished-method.md)|Notifie le profileur qu’un garbage collection est terminé et que tous les rappels de garbage collection ont été émis pour celui-ci.|  
|[GarbageCollectionStarted, méthode](icorprofilercallback2-garbagecollectionstarted-method.md)|Notifie le profileur de code qu’un garbage collection a démarré.|  
|[HandleCreated, méthode](icorprofilercallback2-handlecreated-method.md)|Notifie le profileur de code qu’un handle de garbage collection a été créé.|  
|[HandleDestroyed, méthode](icorprofilercallback2-handledestroyed-method.md)|Notifie le profileur de code qu’un handle de garbage collection a été détruit.|  
|[RootReferences2, méthode](icorprofilercallback2-rootreferences2-method.md)|Notifie le profileur des références racines après qu’un garbage collection s’est produit. Cette méthode est une extension de la méthode [ICorProfilerCallback :: RootReferences](icorprofilercallback-rootreferences-method.md) .|  
|[SurvivingReferences, méthode](icorprofilercallback2-survivingreferences-method.md)|Notifie le profileur des références d’objet qui ont survécu à un garbage collection.|  
|[ThreadNameChanged, méthode](icorprofilercallback2-threadnamechanged-method.md)|Notifie le profileur de code que le nom d’un thread a changé.|  
  
## <a name="remarks"></a>Remarques  

 Le CLR appelle une méthode dans l' `ICorProfilerCallback` interface (ou `ICorProfilerCallback2` ) pour notifier le profileur lorsqu’un événement auquel le profileur s’est abonné se produit. Il s’agit de l’interface de rappel principale par le biais de laquelle le CLR communique avec le profileur de code.  
  
 Un profileur de code doit implémenter les méthodes de l' `ICorProfilerCallback` interface. Pour le .NET Framework 2,0 et les versions ultérieures, le profileur doit également implémenter les `ICorProfilerCallback2` méthodes. Chaque implémentation de méthode doit retourner un HRESULT ayant la valeur S_OK en cas de réussite ou E_FAIL en cas d’échec. Actuellement, le CLR ignore le HRESULT retourné par chaque rappel, à l’exception de [ICorProfilerCallback :: ObjectReferences](icorprofilercallback-objectreferences-method.md).  
  
 Un profileur de code doit s’inscrire dans le Registre Microsoft Windows, son objet COM qui implémente les `ICorProfilerCallback` `ICorProfilerCallback2` interfaces et. Un profileur de code s’abonne aux événements pour lesquels il souhaite recevoir une notification en appelant [ICorProfilerInfo :: SetEventMask](icorprofilerinfo-seteventmask-method.md). Cela se fait généralement dans l’implémentation de [ICorProfilerCallback :: Initialize](icorprofilercallback-initialize-method.md)du profileur. Le profileur est ensuite en mesure de recevoir une notification de la part du runtime lorsqu’un événement est sur le ou s’est produit dans un processus du runtime en cours d’exécution.  
  
> [!NOTE]
> Le profileur inscrit un objet COM unique. Si le profileur cible .NET Framework version 1,0 ou 1,1, cet objet COM n’a besoin que d’implémenter les méthodes de `ICorProfilerCallback` . Si elle cible .NET Framework version 2,0 et les versions ultérieures, l’objet COM doit également implémenter les méthodes de `ICorProfilerCallback2` .  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de profilage](profiling-interfaces.md)
- [ICorProfilerCallback, interface](icorprofilercallback-interface.md)
- [ICorProfilerCallback3, interface](icorprofilercallback3-interface.md)
- [ICorProfilerCallback4, interface](icorprofilercallback4-interface.md)
