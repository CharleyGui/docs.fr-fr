---
title: ICorProfilerCallback::ObjectReferences, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectReferences
helpviewer_keywords:
- ObjectReferences method [.NET Framework profiling]
- ICorProfilerCallback::ObjectReferences method [.NET Framework profiling]
ms.assetid: dd5e9b64-b4a3-4ba6-9be6-ddb540f4ffcf
topic_type:
- apiref
ms.openlocfilehash: 6e6cc44c2f9028c0e26c4f933242cad93e3a98c3
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866089"
---
# <a name="icorprofilercallbackobjectreferences-method"></a>ICorProfilerCallback::ObjectReferences, méthode
Notifie le profileur des objets en mémoire qui sont référencés par l’objet spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ObjectReferences(  
    [in]  ObjectID objectId,  
    [in]  ClassID  classId,  
    [in]  ULONG    cObjectRefs,  
    [in, size_is(cObjectRefs)] ObjectID objectRefIds[] );  
```  
  
## <a name="parameters"></a>Parameters  
 `objectId`  
 dans ID de l’objet qui référence des objets.  
  
 `classId`  
 dans ID de la classe dont l’objet spécifié est une instance de.  
  
 `cObjectRefs`  
 dans Nombre d’objets référencés par l’objet spécifié (autrement dit, le nombre d’éléments contenus dans le tableau `objectRefIds`).  
  
 `objectRefIds`  
 dans Tableau d’ID des objets référencés par `objectId`.  
  
## <a name="remarks"></a>Notes  
 La méthode `ObjectReferences` est appelée pour chaque objet restant dans le tas après la fin d’une garbage collection. Si le profileur retourne une erreur à partir de ce rappel, les services de profilage ne continueront pas à appeler ce rappel jusqu’à la garbage collection suivante.  
  
 Le rappel `ObjectReferences` peut être utilisé conjointement avec le rappel [ICorProfilerCallback :: RootReferences](icorprofilercallback-rootreferences-method.md) pour créer un graphique de référence d’objet complet pour le Runtime. Le common language runtime (CLR) s’assure que chaque référence d’objet est signalée une seule fois par la méthode `ObjectReferences`.  
  
 Les ID d’objet retournés par `ObjectReferences` ne sont pas valides pendant le rappel lui-même, car le garbage collection peut être en train de déplacer des objets. Par conséquent, les profileurs ne doivent pas tenter d’inspecter les objets pendant un appel de `ObjectReferences`. Quand [ICorProfilerCallback2 :: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) est appelé, le garbage collection est terminé et l’inspection peut être effectuée en toute sécurité.  
  
 Une `ClassId` null indique que `objectId` a un type qui décharge.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](icorprofilercallback-interface.md)
