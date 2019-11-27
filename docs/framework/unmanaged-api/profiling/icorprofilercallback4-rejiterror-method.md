---
title: ICorProfilerCallback4::ReJITError, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITError
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITError
helpviewer_keywords:
- ReJITError method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITError method [.NET Framework profiling]
ms.assetid: d7888aa9-dfaa-420f-9f99-e06ab35ca482
topic_type:
- apiref
ms.openlocfilehash: 6ea9dee6e83870d1f2e0fdccffa53f16e6f18dba
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430109"
---
# <a name="icorprofilercallback4rejiterror-method"></a>ICorProfilerCallback4::ReJITError, méthode
Notifie le profileur que le compilateur juste-à-temps (JIT) a rencontré une erreur dans le processus de recompilation.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ReJITError(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodId,  
    [in] FunctionID  functionId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a>Paramètres  
 `moduleID`  
 dans `ModuleID` dans lequel la tentative de recompilation a échoué.  
  
 `methodId`  
 dans `MethodDef` de la méthode sur laquelle la tentative de recompilation a échoué.  
  
 `functionId`  
 dans Instance de fonction qui est recompilée ou marquée pour la recompilation. Cette valeur peut être `NULL` si l’échec s’est produit par méthode au lieu d’une base par instanciation (par exemple, si le profileur a spécifié un jeton de métadonnées non valide pour la méthode à recompiler).  
  
 `hrStatus`  
 dans HRESULT qui indique la nature de l’échec. Pour obtenir la liste des valeurs, consultez la section HRESULT d’État.  
  
## <a name="return-value"></a>Valeur de retour  
 Les valeurs retournées depuis ce rappel sont ignorées.  
  
## <a name="status-hresults"></a>HRESULT d'état  
  
|HRESULT du tableau d'états|Description|  
|--------------------------|-----------------|  
|E_INVALIDARG|Le jeton `moduleID` ou `methodDef` est `NULL`.|  
|CORPROF_E_DATAINCOMPLETE|Le module n'est pas encore totalement chargé ou il est en cours de déchargement.|  
|CORPROF_E_MODULE_IS_DYNAMIC|Le module spécifié a été généré dynamiquement (par exemple, par `Reflection.Emit`) et n’est donc pas pris en charge par cette méthode.|  
|CORPROF_E_FUNCTION_IS_COLLECTIBLE|La méthode est instanciée dans un assembly pouvant être collecté et ne peut donc pas être recompilée. Notez que les types et les fonctions définis dans un contexte non réfléchissant (par exemple, `List<MyCollectibleStruct>`) peuvent être instanciés dans un assembly pouvant être collecté.|  
|E_OUTOFMEMORY|La mémoire du CLR est insuffisante lors de la tentative de marquage de la méthode spécifiée pour la recompilation JIT.|  
|Autres|Le système d'exploitation a retourné un échec en dehors du contrôle du CLR. Par exemple, si un appel système pour modifier la protection d’accès d’une page de mémoire échoue, l’erreur du système d’exploitation s’affiche.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback4, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
