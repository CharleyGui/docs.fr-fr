---
title: ICorProfilerCallback8::DynamicMethodJITCompilationLa méthode
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationStarted
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: e8b1a243b691d8d5eb364fd16821fd9156505c60
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177044"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a>ICorProfilerCallback8::DynamicMethodJITCompilationLa méthode
[Soutenu dans le cadre .NET 4.7 et les versions ultérieures]  
  
Informe le profileur chaque fois que la compilation JIT d’une méthode dynamique a commencé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,
     [in]  BOOL        fIsSafeToBlock,
     [in]  LPCBYTE     pILHeader,
     [in]  LONG        cbILHeader
);  
```  
  
## <a name="parameters"></a>Paramètres  
[in] `functionId`  
L’identifiant de la fonction mémoire pour laquelle la compilation JIT est commencée.

[dans] `fIsSafeToBlock` pour indiquer que le blocage peut faire attendre le temps d’exécution pour que le fil d’appel revienne de ce 
 `true` rappel; `false` pour indiquer que le blocage n’affectera pas le fonctionnement de l’exécution.  

[dans] `pILHeader` Un pointeur au premier byte de l’en-tête il de la méthode.

[dans] `cbILHeader` Le nombre d’octets dans l’en-tête de l’IL.

## <a name="remarks"></a>Notes   

Ce rappel est déclenché chaque fois qu’une méthode dynamique est compilée par JIT. Cela comprend divers talons IL et méthodes LCG. Son objectif est de fournir aux auteurs de profileur suffisamment d’informations pour identifier la méthode compilée aux utilisateurs.

> [!NOTE]
> `functionId`les valeurs ne peuvent pas être utilisées pour résoudre leurs jetons de métadonnées, parce que les méthodes dynamiques n’ont pas de métadonnées.

Le `pILHeader` pointeur n’est valable que pendant le rappel.

## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [DynamicMethodJITCompilationFinished, méthode](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [ICorProfilerCallback8, interface](icorprofilercallback8-interface.md)
