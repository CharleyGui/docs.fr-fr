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
ms.openlocfilehash: 9485e3ca657ab108d2bcc9d00b1c475f8ee3c086
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703952"
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
  
## <a name="parameters"></a>Paramètres  

 `objectId`  
 dans ID de l’objet qui référence des objets.  
  
 `classId`  
 dans ID de la classe dont l’objet spécifié est une instance de.  
  
 `cObjectRefs`  
 dans Nombre d’objets référencés par l’objet spécifié (autrement dit, le nombre d’éléments dans le `objectRefIds` tableau).  
  
 `objectRefIds`  
 dans Tableau d’ID des objets référencés par `objectId` .  
  
## <a name="remarks"></a>Remarques  

 La `ObjectReferences` méthode est appelée pour chaque objet restant dans le tas à la fin d’une garbage collection. Si le profileur retourne une erreur à partir de ce rappel, les services de profilage ne continueront pas à appeler ce rappel jusqu’à la garbage collection suivante.  
  
 Le `ObjectReferences` rappel peut être utilisé conjointement avec le rappel [ICorProfilerCallback :: RootReferences](icorprofilercallback-rootreferences-method.md) pour créer un graphique de référence d’objet complet pour le Runtime. Le common language runtime (CLR) s’assure que chaque référence d’objet est signalée une seule fois par la `ObjectReferences` méthode.  
  
 Les ID d’objet retournés par `ObjectReferences` ne sont pas valides pendant le rappel lui-même, car le garbage collection peut être en train de déplacer des objets. Par conséquent, les profileurs ne doivent pas tenter d’inspecter les objets pendant un `ObjectReferences` appel. Quand [ICorProfilerCallback2 :: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) est appelé, le garbage collection est terminé et l’inspection peut être effectuée en toute sécurité.  
  
 Une valeur null `ClassId` indique que `objectId` a un type qui décharge.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](icorprofilercallback-interface.md)
