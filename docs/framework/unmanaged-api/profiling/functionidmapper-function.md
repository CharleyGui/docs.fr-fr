---
title: FunctionIDMapper (fonction)
ms.date: 03/30/2017
api_name:
- FunctionIDMapper
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionIDMapper
helpviewer_keywords:
- FunctionIDMapper function [.NET Framework profiling]
ms.assetid: b8205b60-1893-4303-8cff-7ac5a00892aa
topic_type:
- apiref
ms.openlocfilehash: 0cf2014d7007593c51868eff0b488fdab136e362
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175172"
---
# <a name="functionidmapper-function"></a>FunctionIDMapper (fonction)
Informe le profileur que l’identifiant donné d’une fonction peut être remapped à un ID alternatif à utiliser dans le [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md), et [FunctionTailcall2](functiontailcall2-function.md) rappels pour cette fonction. `FunctionIDMapper` permet également au profileur d'indiquer s'il souhaite recevoir des rappels pour cette fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a>Paramètres

- `funcId`

  \[dans] L’identifiant de fonction à remapped.

- `pbHookFunction`

  \[out] Un pointeur à une valeur `true` que le `FunctionEnter2`profileur fixe à s’il veut recevoir , `FunctionLeave2`, et `FunctionTailcall2` les rappels; autrement, il définit `false`cette valeur à .

## <a name="return-value"></a>Valeur de retour  
 Le profileur retourne une valeur que le moteur d'exécution utilise comme autre identificateur de fonction. La valeur de retour ne peut pas être null, sauf si `false` est retourné dans `pbHookFunction`. Dans le cas contraire, une valeur de rendement nul produira des résultats imprévisibles, y compris peut-être arrêter le processus.  
  
## <a name="remarks"></a>Notes   
 La `FunctionIDMapper` fonction est un rappel. Il est implémenté par le profileur pour remap une id de fonction à un autre identifiant qui est plus utile pour le profileur. Le `FunctionIDMapper` renvoi de l’ID alternatif à utiliser pour une fonction donnée. Le moteur d’exécution honore alors la demande du profileur en passant cette pièce d’identité `clientData` alternative, `FunctionEnter2` `FunctionLeave2`en `FunctionTailcall2` plus de l’ID de fonction traditionnelle, de retour au profileur dans le paramètre de la , , et les crochets, pour identifier la fonction pour laquelle le crochet est appelé.  
  
 Vous pouvez utiliser la méthode [ICorProfilerInfo::SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) `FunctionIDMapper` pour spécifier la mise en œuvre de la fonction. Vous ne `ICorProfilerInfo::SetFunctionIDMapper` pouvez appeler la méthode qu’une seule fois, et nous vous recommandons de le faire dans [l’ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.  
  
 Par défaut, on suppose qu’un profileur qui fixe le drapeau COR_PRF_MONITOR_ENTERLEAVE en utilisant [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md), et qui définit les crochets via [ICorProfilerInfo::SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md) ou [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), devrait recevoir le `FunctionEnter2`, `FunctionLeave2`, et `FunctionTailcall2` les rappels pour chaque fonction. Cependant, les profileurs peuvent mettre en œuvre `FunctionIDMapper` pour éviter `pbHookFunction` `false`sélectivement de recevoir ces rappels pour certaines fonctions en définissant à .  
  
 Les profileurs doivent tolérer les cas où plusieurs threads d’une application profilée appellent la même méthode/fonction simultanément. Dans de tels cas, le `FunctionIDMapper` profileur peut `FunctionID`recevoir plusieurs rappels pour la même . Le profileur devrait être certain de retourner les mêmes valeurs de ce `FunctionID`rappel quand il est appelé plusieurs fois avec le même .  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** CorProf.idl  
  
 **Bibliothèque :** CorGuids.lib  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [SetFunctionIDMapper, méthode](icorprofilerinfo-setfunctionidmapper-method.md)
- [FunctionIDMapper2, fonction](functionidmapper2-function.md)
- [FunctionEnter2 (fonction)](functionenter2-function.md)
- [FunctionLeave2 (fonction)](functionleave2-function.md)
- [FunctionTailcall2 (fonction)](functiontailcall2-function.md)
- [Fonctions statiques globales du profilage](profiling-global-static-functions.md)
