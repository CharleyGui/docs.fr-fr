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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4141c79502dae89ec228e4e39da121615f292786
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782972"
---
# <a name="icorprofilercallbackobjectreferences-method"></a>ICorProfilerCallback::ObjectReferences, méthode
Notifie le profileur sur les objets en mémoire qui sont référencés par l’objet spécifié.  
  
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
 [in] L’ID de l’objet qui fait référence à des objets.  
  
 `classId`  
 [in] L’ID de la classe de l’objet spécifié est une instance de.  
  
 `cObjectRefs`  
 [in] Le nombre d’objets référencés par l’objet spécifié (autrement dit, le nombre d’éléments dans le `objectRefIds` tableau).  
  
 `objectRefIds`  
 [in] Un tableau des ID des objets qui sont référencés par `objectId`.  
  
## <a name="remarks"></a>Notes  
 Le `ObjectReferences` méthode est appelée pour chaque objet reste dans le tas après l’exécution d’un garbage collection. Si le profileur retourne une erreur à partir de ce rappel, les services de profilage cessent d’appeler ce rappel jusqu'à ce que le garbage collection suivant.  
  
 Le `ObjectReferences` rappel peut être utilisé conjointement avec le [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) rappel pour créer un graphique de référence d’objet complet pour le runtime. Le common language runtime (CLR) garantit que chaque référence d’objet est signalé qu’une seule fois par le `ObjectReferences` (méthode).  
  
 Les ID d’objet retourné par `ObjectReferences` ne sont pas valides pendant le rappel lui-même, car le garbage collection peut être occupé à déplacer des objets. Par conséquent, les profileurs ne doivent pas essayer d’inspecter les objets pendant un `ObjectReferences` appeler. Lorsque [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) est appelée, le garbage collection est terminé et l’inspection peut être effectuée en toute sécurité.  
  
 Une valeur null `ClassId` indique que `objectId` a un type qui est déchargement.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
