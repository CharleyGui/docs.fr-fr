---
title: ICorProfilerCallback8, interface
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 617b27923e96d9abc62ccbf158b076c6e45b20a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175094"
---
# <a name="icorprofilercallback8-interface"></a>ICorProfilerCallback8, interface
[Soutenu dans le cadre .NET 4.7 et les versions ultérieures]  

 Une sous-classe [d’ICorProfilerCallback7](icorprofilercallback7-interface.md) qui fournit des méthodes de rappel utilisées par l’heure courante de l’exécution de la langue pour informer le profileur que la compilation JIT d’une méthode dynamique a commencé et terminé.
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[DynamicMethodJITCompilationStarted, méthode](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|Informe le profileur que la compilation JIT d’une méthode dynamique a commencé.|  
|[DynamicMethodJITCompilationFinished, méthode](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|Informe le profileur que la compilation JIT d’une méthode dynamique est terminée.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
**.NET Versions-cadre:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Voir aussi

- [Interfaces de profilage](profiling-interfaces.md)
- [ICorProfilerCallback9, interface](icorprofilercallback9-interface.md)
