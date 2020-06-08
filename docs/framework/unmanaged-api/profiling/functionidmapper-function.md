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
ms.openlocfilehash: afc818dfe625bfc329ceb1660539eb119702a90d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500674"
---
# <a name="functionidmapper-function"></a>FunctionIDMapper (fonction)
Notifie le profileur que l’identificateur donné d’une fonction peut être remappé à un autre ID à utiliser dans les rappels [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md)et [FunctionTailcall2](functiontailcall2-function.md) pour cette fonction. `FunctionIDMapper` permet également au profileur d'indiquer s'il souhaite recevoir des rappels pour cette fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a>Paramètres

- `funcId`

  \[in] identificateur de fonction à remapper.

- `pbHookFunction`

  \[out] pointeur vers une valeur à laquelle le profileur affecte `true` s’il souhaite recevoir `FunctionEnter2` des `FunctionLeave2` `FunctionTailcall2` rappels, et ; sinon, il définit cette valeur sur `false` .

## <a name="return-value"></a>Valeur renvoyée  
 Le profileur retourne une valeur que le moteur d'exécution utilise comme autre identificateur de fonction. La valeur de retour ne peut pas être null, sauf si `false` est retourné dans `pbHookFunction`. Sinon, une valeur de retour NULL produira des résultats imprévisibles, y compris éventuellement l’arrêt du processus.  
  
## <a name="remarks"></a>Remarques  
 La `FunctionIDMapper` fonction est un rappel. Elle est implémentée par le profileur pour remapper un ID de fonction à un autre identificateur qui est plus utile pour le profileur. `FunctionIDMapper`Retourne l’ID de remplacement à utiliser pour toute fonction donnée. Le moteur d’exécution honore ensuite la demande du profileur en passant cet ID alternatif, en plus de l’ID de fonction traditionnel, au profileur dans le `clientData` paramètre `FunctionEnter2` des `FunctionLeave2` `FunctionTailcall2` raccordements, et, pour identifier la fonction pour laquelle le hook est appelé.  
  
 Vous pouvez utiliser la méthode [ICorProfilerInfo :: SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) pour spécifier l’implémentation de la `FunctionIDMapper` fonction. Vous pouvez appeler la `ICorProfilerInfo::SetFunctionIDMapper` méthode une seule fois, et nous vous recommandons de le faire dans le rappel [ICorProfilerCallback :: Initialize](icorprofilercallback-initialize-method.md) .  
  
 Par défaut, il est supposé qu’un profileur qui définit l’indicateur COR_PRF_MONITOR_ENTERLEAVE à l’aide de [ICorProfilerInfo :: SetEventMask](icorprofilerinfo-seteventmask-method.md)et qui définit des raccordements via [ICorProfilerInfo :: SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md) ou [ICorProfilerInfo2 :: SetEnterLeaveFunctionHooks2,](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), doit recevoir les `FunctionEnter2` `FunctionLeave2` `FunctionTailcall2` rappels, et pour chaque fonction. Toutefois, les profileurs peuvent implémenter `FunctionIDMapper` pour ne pas recevoir de manière sélective ces rappels pour certaines fonctions en affectant à la valeur `pbHookFunction` `false` .  
  
 Les profileurs doivent être tolérants dans les cas où plusieurs threads d’une application profilée appellent la même méthode/fonction simultanément. Dans ce cas, le profileur peut recevoir plusieurs `FunctionIDMapper` rappels pour le même `FunctionID` . Le profileur doit être certain de retourner les mêmes valeurs à partir de ce rappel lorsqu’il est appelé plusieurs fois avec le même `FunctionID` .  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf. idl  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [SetFunctionIDMapper, méthode](icorprofilerinfo-setfunctionidmapper-method.md)
- [FunctionIDMapper2, fonction](functionidmapper2-function.md)
- [FunctionEnter2 (fonction)](functionenter2-function.md)
- [FunctionLeave2 (fonction)](functionleave2-function.md)
- [FunctionTailcall2 (fonction)](functiontailcall2-function.md)
- [Fonctions statiques globales du profilage](profiling-global-static-functions.md)
