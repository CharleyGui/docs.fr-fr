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
ms.openlocfilehash: b587f30a01623c6e9806bcd9d01058a0880be239
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499907"
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
 dans Nombre de références dans le `rootRefIds` tableau.  
  
 `rootRefIds`  
 dans Tableau d’ID d’objet qui référencent un objet statique ou un objet sur la pile.  
  
## <a name="remarks"></a>Remarques  
 `RootReferences`Et [ICorProfilerCallback2 :: RootReferences2](icorprofilercallback2-rootreferences2-method.md) sont appelés pour avertir le profileur. Les profileurs implémentent normalement l’un ou l’autre, mais pas les deux, car les informations transmises `RootReferences2` sont un sur-ensemble de qui est passé `RootReferences` .  
  
 Il est possible que le `rootRefIds` tableau contienne un objet null. Par exemple, toutes les références d’objets déclarées sur la pile sont traitées comme des racines par le garbage collector et sont toujours signalées.  
  
 Les ID d’objet retournés par `RootReferences` ne sont pas valides pendant le rappel lui-même, car le garbage collection peut être en train de déplacer des objets d’anciennes adresses vers de nouvelles adresses. Par conséquent, les profileurs ne doivent pas tenter d’inspecter les objets pendant un `RootReferences` appel. Quand [ICorProfilerCallback2 :: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) est appelé, tous les objets ont été déplacés vers leurs nouveaux emplacements et peuvent être inspectés en toute sécurité.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](icorprofilercallback-interface.md)
