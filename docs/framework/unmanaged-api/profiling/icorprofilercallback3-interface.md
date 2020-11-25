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
ms.openlocfilehash: fd482bfe8e95a53cafd1530c88f09df146a1b150
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729432"
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
  
## <a name="requirements"></a>Spécifications  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de profilage](profiling-interfaces.md)
- [ICorProfilerInfo, interface](icorprofilerinfo-interface.md)
- [ICorProfilerCallback2, interface](icorprofilercallback2-interface.md)
- [ICorProfilerCallback4, interface](icorprofilercallback4-interface.md)
