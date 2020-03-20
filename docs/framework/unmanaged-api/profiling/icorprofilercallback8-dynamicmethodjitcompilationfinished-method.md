---
title: ICorProfilerCallback8::DynamicMethodJITCompilationLa méthode
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationFinished
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: c2e9489654a0fe5fa65ec638ed0f991a6c01415a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175107"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a>ICorProfilerCallback8::DynamicMethodJITCompilationLa méthode
[Soutenu dans le cadre .NET 4.7 et les versions ultérieures]  
  
Informe le profileur chaque fois que la compilation JIT d’une méthode dynamique est terminée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,
     [in]  BOOL        hrStatus,
     [in]  BOOL        fIsSafeToBlock
);  
```  
  
## <a name="parameters"></a>Paramètres  
[in] `functionId`  
L’identifiant de la fonction mémoire pour laquelle la compilation JIT est commencée.

[dans] `hrStatus` Une valeur qui indique si la compilation JIT a été couronnée de succès.

[dans] `fIsSafeToBlock` pour indiquer que le blocage peut faire attendre le temps d’exécution pour que le fil d’appel revienne de ce 
 `true` rappel; `false` pour indiquer que le blocage n’affectera pas le fonctionnement de l’exécution.  

## <a name="remarks"></a>Notes   

Ce rappel est déclenché chaque fois que la compilation JIT d’une méthode dynamique est terminée. Cela comprend divers talons IL et méthodes LCG. Son objectif est de fournir aux auteurs de profileur suffisamment d’informations pour identifier la méthode compilée aux utilisateurs.

> [!NOTE]
> `functionId`les valeurs ne peuvent pas être utilisées pour résoudre leurs jetons de métadonnées, parce que les méthodes dynamiques n’ont pas de métadonnées.

## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [DynamicMethodJITCompilationStarted, méthode](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [ICorProfilerCallback8, interface](icorprofilercallback8-interface.md)
