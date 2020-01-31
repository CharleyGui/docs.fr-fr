---
title: ICorProfilerCallback3, interface
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3
helpviewer_keywords:
- ICorProfilerCallback3 interface [.NET Framework profiling]
ms.assetid: be83af41-3dec-4c77-8529-9dd6b8042af6
topic_type:
- apiref
ms.openlocfilehash: ad9c5445cbef0be7919570db64b027556d923752
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865569"
---
# <a name="icorprofilercallback3-interface"></a>ICorProfilerCallback3, interface
Fournit des méthodes de rappel que le common language runtime (CLR) utilise pour communiquer les informations d’état d’attachement et de détachement au profileur.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[InitializeForAttach, méthode](icorprofilercallback3-initializeforattach-method.md)|Appelée par le CLR pour permettre au profileur d’initialiser son état après une opération d’attachement.|  
|[ProfilerAttachComplete, méthode](icorprofilercallback3-profilerattachcomplete-method.md)|Appelée par le CLR pour indiquer que le profileur peut maintenant appeler les méthodes de rattrapage.|  
|[ProfilerDetachSucceeded, méthode](icorprofilercallback3-profilerdetachsucceeded-method.md)|Indique au profileur que le Common Language Runtime (CLR) est sur le point de décharger sa DLL.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de profilage](profiling-interfaces.md)
- [ICorProfilerInfo, interface](icorprofilerinfo-interface.md)
- [ICorProfilerCallback2, interface](icorprofilercallback2-interface.md)
- [ICorProfilerCallback4, interface](icorprofilercallback4-interface.md)
