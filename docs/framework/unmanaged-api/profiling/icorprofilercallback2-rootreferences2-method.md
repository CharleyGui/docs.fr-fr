---
title: ICorProfilerCallback2::RootReferences2, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.RootReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::RootReferences2
helpviewer_keywords:
- RootReferences2 method [.NET Framework profiling]
- ICorProfilerCallback2::RootReferences2 method [.NET Framework profiling]
ms.assetid: 55a2f907-d216-42eb-8f2f-e5d59c2eebd6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 563a2e19c9c254870b3e767253a276a201e631a6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779302"
---
# <a name="icorprofilercallback2rootreferences2-method"></a>ICorProfilerCallback2::RootReferences2, méthode
Informe le profileur sur les références racine après qu’un garbage collection s’est produite. Cette méthode est une extension de la [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) (méthode).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT RootReferences2(  
    [in] ULONG  cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_KIND rootKinds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_FLAGS rootFlags[],  
    [in, size_is(cRootRefs)] UINT_PTR rootIds[]);  
```  
  
## <a name="parameters"></a>Paramètres  
 `cRootRefs`  
 [in] Le nombre d’éléments dans le `rootRefIds`, `rootKinds`, `rootFlags`, et `rootIds` tableaux.  
  
 `rootRefIds`  
 [in] Tableau d’ID d’objet, chacun d'entre eux fait référence à un objet statique ou un objet sur la pile. Éléments dans le `rootKinds` tableau fournissent des informations pour classer les éléments correspondants dans le `rootRefIds` tableau.  
  
 `rootKinds`  
 [in] Un tableau de [COR_PRF_GC_ROOT_KIND](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md) valeurs qui indiquent le type de la racine de garbage collection.  
  
 `rootFlags`  
 [in] Un tableau de [COR_PRF_GC_ROOT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md) valeurs qui décrivent les propriétés d’une racine de garbage collection.  
  
 `rootIds`  
 [in] Un tableau de valeurs UINT_PTR qui pointent vers un entier qui contient des informations supplémentaires sur la racine de garbage collection, selon la valeur de la `rootKinds` paramètre.  
  
 Si le type de la racine est une pile, l’ID de la racine est pour la fonction qui contient la variable. Si cet ID racine est 0, la fonction est une fonction sans nom qui est interne au CLR. Si le type de la racine est un handle, l’ID de la racine est pour le handle de garbage collection. Pour les autres types racine, l’ID est une valeur opaque et doit être ignorée.  
  
## <a name="remarks"></a>Notes  
 Le `rootRefIds`, `rootKinds`, `rootFlags`, et `rootIds` tableaux sont des tableaux parallèles. Autrement dit, `rootRefIds[i]`, `rootKinds[i]`, `rootFlags[i]`, et `rootIds[i]` concernent la même racine.  
  
 Les deux `RootReferences` et `RootReferences2` sont appelées pour notifier le profileur. Les profileurs normalement implémenteront l’un ou l’autre méthode, mais pas les deux, car les informations passées dans `RootReferences2` est un sur-ensemble de celles passées dans `RootReferences`.  
  
 Il est possible pour les entrées dans `rootRefIds` à zéro, ce qui implique que la référence de racine correspondante est null et ne fait pas référence à un objet sur le tas managé.  
  
 Les ID d’objet retourné par `RootReferences2` ne sont pas valides pendant le rappel lui-même, car le garbage collection peut être occupé à déplacer les objets des anciennes adresses vers de nouvelles adresses. Les profileurs ne doivent donc pas essayer d'inspecter des objets pendant un appel de `RootReferences2`. Lorsque [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) est appelée, tous les objets ont été déplacés vers leurs nouveaux emplacements et peuvent être inspectés sans risque.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback2, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
