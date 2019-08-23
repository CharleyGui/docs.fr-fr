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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d36d8ef3bfdbd6a1acf787a91003e2ff3139a4d9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963970"
---
# <a name="icorprofilercallback2-interface"></a>ICorProfilerCallback2, interface
Fournit des méthodes qui sont utilisées par le common language runtime (CLR) pour notifier un profileur de code lorsque les événements auxquels le profileur s’est abonné se produisent. L' `ICorProfilerCallback2` interface est une extension de l’interface [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) . Autrement dit, il fournit de nouveaux rappels introduits dans la version 2,0 de .NET Framework.  
  
> [!NOTE]
> Chaque implémentation de méthode doit retourner un HRESULT dont la valeur est S_OK en cas de réussite ou E_FAIL en cas d’échec. Actuellement, le CLR ignore le HRESULT retourné par chaque rappel, à l’exception de [ICorProfilerCallback:: ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md).  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[FinalizeableObjectQueued, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md)|Notifie le profileur de code qu’un objet avec un finaliseur a été mis en file d’attente dans le thread finaliseur pour l’exécution de sa `Finalize` méthode.|  
|[GarbageCollectionFinished, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)|Notifie le profileur qu’un garbage collection est terminé et que tous les rappels de garbage collection ont été émis pour celui-ci.|  
|[GarbageCollectionStarted, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)|Notifie le profileur de code qu’un garbage collection a démarré.|  
|[HandleCreated, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handlecreated-method.md)|Notifie le profileur de code qu’un handle de garbage collection a été créé.|  
|[HandleDestroyed, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handledestroyed-method.md)|Notifie le profileur de code qu’un handle de garbage collection a été détruit.|  
|[RootReferences2, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)|Notifie le profileur des références racines après qu’un garbage collection s’est produit. Cette méthode est une extension de la méthode [ICorProfilerCallback:: RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) .|  
|[SurvivingReferences, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md)|Notifie le profileur des références d’objet qui ont survécu à un garbage collection.|  
|[ThreadNameChanged, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-threadnamechanged-method.md)|Notifie le profileur de code que le nom d’un thread a changé.|  
  
## <a name="remarks"></a>Notes  
 Le CLR appelle une méthode dans l' `ICorProfilerCallback` interface ( `ICorProfilerCallback2`ou) pour notifier le profileur lorsqu’un événement auquel le profileur s’est abonné se produit. Il s’agit de l’interface de rappel principale par le biais de laquelle le CLR communique avec le profileur de code.  
  
 Un profileur de code doit implémenter les `ICorProfilerCallback` méthodes de l’interface. Pour le .NET Framework 2,0 et les versions ultérieures, le profileur doit `ICorProfilerCallback2` également implémenter les méthodes. Chaque implémentation de méthode doit retourner un HRESULT dont la valeur est S_OK en cas de réussite ou E_FAIL en cas d’échec. Actuellement, le CLR ignore le HRESULT retourné par chaque rappel, à l’exception de [ICorProfilerCallback:: ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md).  
  
 Un profileur de code doit s’inscrire dans le Registre Microsoft Windows, son objet com qui `ICorProfilerCallback` implémente les interfaces et `ICorProfilerCallback2` . Un profileur de code s’abonne aux événements pour lesquels il souhaite recevoir une notification en appelant [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md). Cela se fait généralement dans l’implémentation de [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)du profileur. Le profileur est ensuite en mesure de recevoir une notification de la part du runtime lorsqu’un événement est sur le ou s’est produit dans un processus du runtime en cours d’exécution.  
  
> [!NOTE]
> Le profileur inscrit un objet COM unique. Si le profileur cible .NET Framework version 1,0 ou 1,1, cet objet COM n’a besoin que d’implémenter les méthodes de `ICorProfilerCallback`. Si elle cible .NET Framework version 2,0 et les versions ultérieures, l’objet COM doit également implémenter `ICorProfilerCallback2`les méthodes de.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf. idl, CorProf. h  
  
 **Bibliothèque** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerCallback, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback3, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)
- [ICorProfilerCallback4, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
