---
title: ICorProfilerCallback2::GarbageCollectionStarted, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.GarbageCollectionStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::GarbageCollectionStarted
helpviewer_keywords:
- GarbageCollectionStarted method [.NET Framework profiling]
- ICorProfilerCallback2::GarbageCollectionStarted method [.NET Framework profiling]
ms.assetid: 44eef087-f21f-4fe2-b481-f8a0ee022e7d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f4f639f9794002748e1019821514c546e4f4429f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746871"
---
# <a name="icorprofilercallback2garbagecollectionstarted-method"></a>ICorProfilerCallback2::GarbageCollectionStarted, méthode
Notifie le profileur de code que le garbage collection a démarré.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GarbageCollectionStarted(  
    [in] int cGenerations,  
    [in, size_is(cGenerations), length_is(cGenerations)] BOOL generationCollected[],  
    [in] COR_PRF_GC_REASON reason);  
```  
  
## <a name="parameters"></a>Paramètres  
 `cGenerations`  
 [in] Le nombre total d’entrées dans le `generationCollected` tableau.  
  
 `generationCollected`  
 [in] Un tableau de valeurs booléennes, qui sont `true` si la génération qui correspond à l’index de tableau est collecté par ce garbage collection ; sinon, `false`.  
  
 Le tableau est indexé par une valeur de la [COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) énumération, qui indique la génération.  
  
 `reason`  
 [in] Une valeur de la [COR_PRF_GC_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md) énumération qui indique la raison pour laquelle le garbage collection a été INDUITE.  
  
## <a name="remarks"></a>Notes  
 Tous les rappels qui se rapportent à ce garbage collection seront produit entre le `GarbageCollectionStarted` rappel et le correspondantes [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) rappel. Ces rappels ne doivent pas se produire sur le même thread.  
  
 Il est possible que le profileur inspecter les objets dans leurs emplacements d’origine pendant le `GarbageCollectionStarted` rappel. Le garbage collector commencera à déplacer les objets après le retour de `GarbageCollectionStarted`. Une fois que le profileur a retourné à partir de ce rappel, le profileur doit considérer tous les ID d’objet est non valide jusqu'à ce qu’il reçoive un `ICorProfilerCallback2::GarbageCollectionFinished` rappel.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback2, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
