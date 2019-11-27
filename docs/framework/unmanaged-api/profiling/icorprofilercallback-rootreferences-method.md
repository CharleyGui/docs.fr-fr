---
title: ICorProfilerCallback::RootReferences, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RootReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RootReferences
helpviewer_keywords:
- RootReferences method [.NET Framework profiling]
- ICorProfilerCallback::RootReferences method [.NET Framework profiling]
ms.assetid: dbdf853b-d1a4-4828-8ef7-53d121d8e6ae
topic_type:
- apiref
ms.openlocfilehash: 9c96cacf508ef5c056a1ff4469247393fdfb9e9e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444474"
---
# <a name="icorprofilercallbackrootreferences-method"></a>ICorProfilerCallback::RootReferences, méthode
Notifie le profileur des informations sur les références racines après garbage collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT RootReferences(  
    [in] ULONG    cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[] );  
```  
  
## <a name="parameters"></a>Paramètres  
 `cRootRefs`  
 dans Nombre de références dans le tableau de `rootRefIds`.  
  
 `rootRefIds`  
 dans Tableau d’ID d’objet qui référencent un objet statique ou un objet sur la pile.  
  
## <a name="remarks"></a>Notes  
 `RootReferences` et [ICorProfilerCallback2 :: RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) sont appelés pour avertir le profileur. Les profileurs implémentent normalement l’un ou l’autre, mais pas les deux à la fois, car les informations transmises `RootReferences2` sont un sur-ensemble de celles passées dans `RootReferences`.  
  
 Il est possible que le tableau `rootRefIds` contienne un objet null. Par exemple, toutes les références d’objets déclarées sur la pile sont traitées comme des racines par le garbage collector et sont toujours signalées.  
  
 Les ID d’objet retournés par `RootReferences` ne sont pas valides pendant le rappel lui-même, car le garbage collection peut être en train de déplacer des objets d’anciennes adresses vers de nouvelles adresses. Par conséquent, les profileurs ne doivent pas tenter d’inspecter les objets pendant un appel de `RootReferences`. Quand [ICorProfilerCallback2 :: GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) est appelé, tous les objets ont été déplacés vers leurs nouveaux emplacements et peuvent être inspectés en toute sécurité.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
