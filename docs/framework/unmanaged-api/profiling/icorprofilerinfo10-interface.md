---
title: Interface ICorProfilerInfo10
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: f2bc716110c14972e5b2c32bceb3123b16e87c61
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449843"
---
# <a name="icorprofilerinfo10-interface"></a>Interface ICorProfilerInfo10

Une sous-classe de [ICorProfilerInfo9](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md) qui fournit des méthodes pour modifier la fonction il, les informations de requête du runtime, et interrompre et reprendre le Runtime.

## <a name="methods"></a>Méthodes  

| Méthode|Description|  
| ------------|-----------------|  
|[Méthode EnumerateObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-enumerateobjectreferences-method.md)|À partir d’un ObjectID, callback et ClientData :, énumère chaque référence d’objet (le cas échéant). |
|[Méthode IsFrozenObject](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-isfrozenobject-method.md)|À partir d’un ObjectID, détermine si l’objet se trouve dans un segment en lecture seule. |
|[Méthode GetLOHObjectSizeThreshold](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-getlohobjectsizethreshold-method.md)|Obtient la valeur du seuil LOH configuré. |
|[Méthode RequestReJITWithInliners](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-requestrejitwithinliners-method.md)| ReJITs les méthodes demandées, ainsi que les Inlines des méthodes demandées.  |
|[Méthode SuspendRuntime](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-suspendruntime-method.md)| Interrompt le runtime sans exécuter de GC. |
|[Méthode ResumeRuntime](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-resumeruntime-method.md)| Reprend le runtime sans exécuter de GC. |

## <a name="requirements"></a>Configuration requise  
**Plateformes :** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).  
**En-tête :** CorProf.idl, CorProf.h  
**Versions de .net :** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)] 

## <a name="see-also"></a>Voir aussi

- [Interfaces de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
