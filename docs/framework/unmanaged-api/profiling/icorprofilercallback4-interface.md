---
title: ICorProfilerCallback4, interface
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4
helpviewer_keywords:
- ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 665f3cfc-cd6f-4880-906c-ea65ad384783
topic_type:
- apiref
ms.openlocfilehash: 295d3d440529623f4569fd6c5f4debe7e4558990
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499439"
---
# <a name="icorprofilercallback4-interface"></a>ICorProfilerCallback4, interface
Fournit des méthodes de rappel que le common language runtime (CLR) utilise pour communiquer des informations au profileur.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetReJITParameters, méthode](icorprofilercallback4-getrejitparameters-method.md)|Permet au profileur de code de définir d’autres indicateurs de génération de code pour un nouveau corps de méthode recompilée.|  
|[MovedReferences2, méthode](icorprofilercallback4-movedreferences2-method.md)|Signale la nouvelle disposition d’objets dans le tas à la suite d’un compactage garbage collection.|  
|[ReJITCompilationFinished, méthode](icorprofilercallback4-rejitcompilationfinished-method.md)|Notifie le profileur que le compilateur juste-à-temps (JIT) a terminé la recompilation d’une fonction.|  
|[ReJITCompilationStarted, méthode](icorprofilercallback4-rejitcompilationstarted-method.md)|Notifie le profileur que le compilateur juste-à-temps (JIT) a commencé à recompiler une fonction.|  
|[ReJITError, méthode](icorprofilercallback4-rejiterror-method.md)|Signale une erreur rencontrée lors du traitement d’une demande de recompilation.|  
|[SurvivingReferences2, méthode](icorprofilercallback4-survivingreferences2-method.md)|Signale la disposition d'objets dans le tas suite à un garbage collection de non-compactage.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback2, interface](icorprofilercallback2-interface.md)
- [Interfaces de profilage](profiling-interfaces.md)
- [ICorProfilerInfo, interface](icorprofilerinfo-interface.md)
