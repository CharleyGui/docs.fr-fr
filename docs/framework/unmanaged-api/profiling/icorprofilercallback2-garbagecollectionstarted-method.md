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
ms.openlocfilehash: 63a8d212a61bd73f44995f0e057eeff96f9a5554
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731943"
---
# <a name="icorprofilercallback2garbagecollectionstarted-method"></a>ICorProfilerCallback2::GarbageCollectionStarted, méthode

Notifie le profileur de code que garbage collection a démarré.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GarbageCollectionStarted(  
    [in] int cGenerations,  
    [in, size_is(cGenerations), length_is(cGenerations)] BOOL generationCollected[],  
    [in] COR_PRF_GC_REASON reason);  
```  
  
## <a name="parameters"></a>Paramètres  

 `cGenerations`  
 dans Nombre total d’entrées dans le `generationCollected` tableau.  
  
 `generationCollected`  
 dans Tableau de valeurs booléennes, qui sont `true` si la génération qui correspond à l’index de tableau est collectée par cette garbage collection ; sinon, `false` .  
  
 Le tableau est indexé par une valeur de l’énumération [COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md) , qui indique la génération.  
  
 `reason`  
 dans Valeur de l’énumération [COR_PRF_GC_REASON](cor-prf-gc-reason-enumeration.md) qui indique la raison pour laquelle l’garbage collection a été induite.  
  
## <a name="remarks"></a>Remarques  

 Tous les rappels relatifs à cet garbage collection se produisent entre le `GarbageCollectionStarted` rappel et le rappel [ICorProfilerCallback2 :: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) correspondant. Ces rappels n’ont pas besoin de se produire sur le même thread.  
  
 Le profileur peut inspecter en toute sécurité les objets dans leurs emplacements d’origine pendant le `GarbageCollectionStarted` rappel. Le garbage collector commence à déplacer les objets après le retour de `GarbageCollectionStarted` . Une fois que le profileur a retourné à partir de ce rappel, le profileur doit considérer tous les ID d’objet comme non valides jusqu’à ce qu’il reçoive un `ICorProfilerCallback2::GarbageCollectionFinished` rappel.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](icorprofilercallback-interface.md)
- [ICorProfilerCallback2, interface](icorprofilercallback2-interface.md)
