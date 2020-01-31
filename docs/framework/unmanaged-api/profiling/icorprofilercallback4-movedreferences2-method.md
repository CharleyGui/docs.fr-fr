---
title: ICorProfilerCallback4::MovedReferences2, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.MovedReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::MovedReferences2
helpviewer_keywords:
- MovedReferences2 method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::MovedReferences2 method [.NET Framework profiling]
ms.assetid: d17a065b-5bc6-4817-b3e1-1e413fcb33a8
topic_type:
- apiref
ms.openlocfilehash: 2f305852ae218417aa1f4d4fe9d2076c0163fd60
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865270"
---
# <a name="icorprofilercallback4movedreferences2-method"></a>ICorProfilerCallback4::MovedReferences2, méthode
Appelée pour signaler la nouvelle disposition d'objets dans le tas suite à un garbage collection de compactage. Cette méthode est appelée si le profileur a implémenté l’interface [ICorProfilerCallback4](icorprofilercallback4-interface.md) . Ce rappel remplace la méthode [ICorProfilerCallback :: MovedReferences](icorprofilercallback-movedreferences-method.md) , car il peut signaler des plages plus larges d’objets dont les longueurs dépassent ce qui peut être exprimé dans un ulong.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT MovedReferences2(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] SIZE_T    cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a>Parameters  
 `cMovedObjectIDRanges`  
 [in] Nombre de blocs d’objets contigus qui ont été déplacés à la suite du garbage collection de compactage. Autrement dit, la valeur de `cMovedObjectIDRanges` est la taille totale des tableaux `oldObjectIDRangeStart`, `newObjectIDRangeStart` et `cObjectIDRangeLength`.  
  
 Les trois arguments suivants de `MovedReferences2` sont des tableaux parallèles. En d'autres termes, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]` et `cObjectIDRangeLength[i]` concernent un bloc unique d'objets contigus.  
  
 `oldObjectIDRangeStart`  
 [in] Tableau de valeurs `ObjectID`, chacune d'elles étant l'ancienne adresse de début (avant le garbage collection) d'un bloc d'objets actifs contigus dans la mémoire.  
  
 `newObjectIDRangeStart`  
 [in] Tableau de valeurs `ObjectID`, chacune d’elles étant la nouvelle adresse de début (après le garbage collection) d’un bloc d’objets actifs contigus dans la mémoire.  
  
 `cObjectIDRangeLength`  
 [in] Tableau d'entiers, chacun d'eux correspondant à la taille d'un bloc d'objets contigus dans la mémoire.  
  
 Une taille est spécifiée pour chaque bloc référencé dans les tableaux `oldObjectIDRangeStart` et `newObjectIDRangeStart`.  
  
## <a name="remarks"></a>Notes  
 Un garbage collection de compactage récupère la mémoire occupée par des objets morts et compacte cet espace libéré. Par conséquent, les objets actifs peuvent être déplacés dans le tas, et les valeurs `ObjectID` distribuées par des notifications précédentes peuvent changer.  
  
 Supposons qu'une valeur `ObjectID` existante (`oldObjectID`) se trouve dans la plage suivante :  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 Dans ce cas, l'offset du début de la plage au début de l'objet est le suivant :  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 Pour toute valeur d'`i` se trouvant dans la plage suivante :  
  
 0 <= `i` < `cMovedObjectIDRanges`  
  
 Vous pouvez calculer le nouvel `ObjectID` comme suit :  
  
 `newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)  
  
 Aucune des valeurs `ObjectID` passées par `MovedReferences2` n'est valide pendant le rappel lui-même, car le garbage collector peut être occupé à déplacer des objets depuis des anciens emplacements vers des nouveaux. Les profileurs ne doivent donc pas essayer d'inspecter des objets pendant un appel de `MovedReferences2`. Un rappel [ICorProfilerCallback2 :: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) indique que tous les objets ont été déplacés vers leurs nouveaux emplacements et que l’inspection peut être effectuée.  
  
 Si le profileur implémente à la fois les interfaces [ICorProfilerCallback](icorprofilercallback-interface.md) et [ICorProfilerCallback4](icorprofilercallback4-interface.md) , la méthode `MovedReferences2` est appelée avant la méthode [ICorProfilerCallback :: MovedReferences](icorprofilercallback-movedreferences-method.md) , mais uniquement si la méthode `MovedReferences2` est correctement retournée. Les profileurs peuvent retourner un HRESULT qui indique un échec de la méthode `MovedReferences2` pour éviter d'appeler la seconde méthode.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](icorprofilercallback-interface.md)
- [MovedReferences, méthode](icorprofilercallback-movedreferences-method.md)
- [ICorProfilerCallback4, interface](icorprofilercallback4-interface.md)
- [Interfaces de profilage](profiling-interfaces.md)
- [Profilage](index.md)
