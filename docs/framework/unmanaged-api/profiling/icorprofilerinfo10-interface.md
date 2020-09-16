---
title: Interface ICorProfilerInfo10
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 7e483bae9b7898e25c376fa92d0449fc49c6f9ee
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548683"
---
# <a name="icorprofilerinfo10-interface"></a>Interface ICorProfilerInfo10

Une sous-classe de [ICorProfilerInfo9](icorprofilerinfo9-interface.md) qui fournit des méthodes pour modifier la fonction il, les informations de requête du runtime, et interrompre et reprendre le Runtime.

## <a name="methods"></a>Méthodes  

| Méthode|Description|  
| ------------|-----------------|  
|[Méthode EnumerateObjectReferences](icorprofilerinfo10-enumerateobjectreferences-method.md)|À partir d’un ObjectID, callback et ClientData :, énumère chaque référence d’objet (le cas échéant). |
|[Méthode IsFrozenObject](icorprofilerinfo10-isfrozenobject-method.md)|À partir d’un ObjectID, détermine si l’objet se trouve dans un segment en lecture seule. |
|[Méthode GetLOHObjectSizeThreshold](icorprofilerinfo10-getlohobjectsizethreshold-method.md)|Obtient la valeur du seuil LOH configuré. |
|[Méthode RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md)| ReJITs les méthodes demandées, ainsi que les Inlines des méthodes demandées.  |
|[Méthode SuspendRuntime](icorprofilerinfo10-suspendruntime-method.md)| Interrompt le runtime sans exécuter de GC. |
|[Méthode ResumeRuntime](icorprofilerinfo10-resumeruntime-method.md)| Reprend le runtime sans exécuter de GC. |

## <a name="requirements"></a>Spécifications  
**Plateformes :** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/install/windows.md?pivots=os-windows).  
**En-tête :** CorProf.idl, CorProf.h  
**Versions de .net :**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>Voir aussi

- [Interfaces de profilage](profiling-interfaces.md)
