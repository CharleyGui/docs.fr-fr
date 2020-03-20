---
title: Interface ICorProfilerInfo10
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 4c5d553744008734037975d6e63e1b07b89cf886
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175068"
---
# <a name="icorprofilerinfo10-interface"></a>Interface ICorProfilerInfo10

Une sous-classe [d’ICorProfilerInfo9](icorprofilerinfo9-interface.md) qui fournit des méthodes pour modifier la fonction IL, interroger les informations à partir du temps d’exécution, et suspendre et reprendre l’heure d’exécution.

## <a name="methods"></a>Méthodes  

| Méthode|Description|  
| ------------|-----------------|  
|[Méthode EnumerateObjectReferences](icorprofilerinfo10-enumerateobjectreferences-method.md)|Compte tenu d’un ObjectID, de rappel et de clientData, énumère chaque référence d’objet (le cas échéant). |
|[Méthode IsFrozenObject](icorprofilerinfo10-isfrozenobject-method.md)|Compte tenu d’un ObjectID, détermine si l’objet se trouve dans un segment de lecture seulement. |
|[Méthode GetLOHObjectSizeThreshold](icorprofilerinfo10-getlohobjectsizethreshold-method.md)|Obtient la valeur du seuil LOH configuré. |
|[Méthode RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md)| ReJITs les méthodes demandées, ainsi que tous les inliners des méthodes demandées.  |
|[Méthode SuspendRuntime](icorprofilerinfo10-suspendruntime-method.md)| Suspend le temps d’exécution sans effectuer un GC. |
|[Méthode ResumeRuntime](icorprofilerinfo10-resumeruntime-method.md)| Reprend le temps d’exécution sans effectuer un GC. |

## <a name="requirements"></a>Spécifications  
**Plates-formes:** Voir [.NET Core systèmes d’exploitation pris en charge](../../../core/install/dependencies.md?pivots=os-windows).  
**En-tête :** CorProf.idl, CorProf.h  
**Versions .NET:**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>Voir aussi

- [Interfaces de profilage](profiling-interfaces.md)
