---
title: ICorProfilerCallback::MovedReferences, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.MovedReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::MovedReferences
helpviewer_keywords:
- MovedReferences method [.NET Framework profiling]
- ICorProfilerCallback::MovedReferences method [.NET Framework profiling]
ms.assetid: 996c71ae-0676-4616-a085-84ebf507649d
topic_type:
- apiref
ms.openlocfilehash: 1214182c95f7d0304ec920a2ea7dae91b1f4a790
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503332"
---
# <a name="icorprofilercallbackmovedreferences-method"></a>ICorProfilerCallback::MovedReferences, méthode
Appelée pour signaler la nouvelle disposition d'objets dans le tas suite à un garbage collection de compactage.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT MovedReferences(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ULONG    cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a>Paramètres  
 `cMovedObjectIDRanges`  
 [in] Nombre de blocs d’objets contigus qui ont été déplacés à la suite du garbage collection de compactage. Autrement dit, la valeur de `cMovedObjectIDRanges` est la taille totale des tableaux `oldObjectIDRangeStart`, `newObjectIDRangeStart` et `cObjectIDRangeLength`.  
  
 Les trois arguments suivants de `MovedReferences` sont des tableaux parallèles. En d'autres termes, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]` et `cObjectIDRangeLength[i]` concernent un bloc unique d'objets contigus.  
  
 `oldObjectIDRangeStart`  
 [in] Tableau de valeurs `ObjectID`, chacune d'elles étant l'ancienne adresse de début (avant le garbage collection) d'un bloc d'objets actifs contigus dans la mémoire.  
  
 `newObjectIDRangeStart`  
 [in] Tableau de valeurs `ObjectID`, chacune d’elles étant la nouvelle adresse de début (après le garbage collection) d’un bloc d’objets actifs contigus dans la mémoire.  
  
 `cObjectIDRangeLength`  
 [in] Tableau d'entiers, chacun d'eux correspondant à la taille d'un bloc d'objets contigus dans la mémoire.  
  
 Une taille est spécifiée pour chaque bloc référencé dans les tableaux `oldObjectIDRangeStart` et `newObjectIDRangeStart`.  
  
## <a name="remarks"></a>Remarques  
  
> [!IMPORTANT]
> Cette méthode signale les tailles en tant que `MAX_ULONG` pour les objets qui sont supérieurs à 4 Go sur les plateformes 64 bits. Pour récupérer la taille des objets qui sont supérieurs à 4 Go, utilisez la méthode [ICorProfilerCallback4 :: MovedReferences2](icorprofilercallback4-movedreferences2-method.md) à la place.  
  
 Un garbage collection de compactage récupère la mémoire occupée par des objets morts et compacte cet espace libéré. Par conséquent, les objets actifs peuvent être déplacés dans le tas, et les valeurs `ObjectID` distribuées par des notifications précédentes peuvent changer.  
  
 Supposons qu'une valeur `ObjectID` existante (`oldObjectID`) se trouve dans la plage suivante :  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 Dans ce cas, l'offset du début de la plage au début de l'objet est le suivant :  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 Pour toute valeur d'`i` se trouvant dans la plage suivante :  
  
 0 <=`i` < `cMovedObjectIDRanges`  
  
 Vous pouvez calculer le nouvel `ObjectID` comme suit :  
  
 `newObjectID` = `newObjectIDRangeStart[i]`+ ( `oldObjectID` – `oldObjectIDRangeStart[i]` )  
  
 Aucune des valeurs `ObjectID` passées par `MovedReferences` n'est valide pendant le rappel lui-même, car le garbage collector peut être occupé à déplacer des objets depuis des anciens emplacements vers des nouveaux. Les profileurs ne doivent donc pas essayer d'inspecter des objets pendant un appel de `MovedReferences`. Un rappel [ICorProfilerCallback2 :: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) indique que tous les objets ont été déplacés vers leurs nouveaux emplacements et que l’inspection peut être effectuée.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](icorprofilercallback-interface.md)
- [MovedReferences2, méthode](icorprofilercallback4-movedreferences2-method.md)
- [Interfaces de profilage](profiling-interfaces.md)
- [Profilage](index.md)
