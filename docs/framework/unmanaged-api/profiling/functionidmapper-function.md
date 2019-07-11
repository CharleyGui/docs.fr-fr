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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b9dee1404a8da63208bba7b7529b16eabbee3254
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745763"
---
# <a name="functionidmapper-function"></a>FunctionIDMapper (fonction)
Notifie le profileur que l’identificateur donné d’une fonction peut être remappé vers un autre ID à utiliser dans le [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), et [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) rappels pour cette fonction. `FunctionIDMapper` permet également au profileur d'indiquer s'il souhaite recevoir des rappels pour cette fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,   
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `funcId`  
 [in] Identificateur de fonction à remapper.  
  
 `pbHookFunction`  
 [out] Un pointeur vers une valeur qui affecte le profileur `true` s’il souhaite recevoir `FunctionEnter2`, `FunctionLeave2`, et `FunctionTailcall2` rappels ; sinon, il définit cette valeur à `false`.  
  
## <a name="return-value"></a>Valeur de retour  
 Le profileur retourne une valeur que le moteur d'exécution utilise comme autre identificateur de fonction. La valeur de retour ne peut pas être null, sauf si `false` est retourné dans `pbHookFunction`. Sinon, une valeur de retour null génère des résultats imprévisibles, y compris éventuellement interrompre le processus.  
  
## <a name="remarks"></a>Notes  
 Le `FunctionIDMapper` fonction est un rappel. Il est implémenté par le profileur pour remapper un ID de fonction à tout autre identificateur qui est plus utile pour le profileur. Le `FunctionIDMapper` retourne l’autre ID à utiliser pour toute fonction donnée. Le moteur d’exécution répond ensuite à la demande du profileur en passant cet ID secondaire, en plus de l’ID de fonction classique, au profileur dans le `clientData` paramètre de la `FunctionEnter2`, `FunctionLeave2`, et `FunctionTailcall2` hooks, pour identifier la fonction pour laquelle le hook est appelé.  
  
 Vous pouvez utiliser la [ICorProfilerInfo::SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) méthode pour spécifier l’implémentation de la `FunctionIDMapper` (fonction). Vous pouvez appeler la `ICorProfilerInfo::SetFunctionIDMapper` méthode qu’une seule fois et nous vous recommandons d’effectuer dans le [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) rappel.  
  
 Par défaut, il est supposé qu’un profileur que qui définit l’indicateur COR_PRF_MONITOR_ENTERLEAVE à l’aide de [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md), et qui définit des raccordements via [ICorProfilerInfo::SetEnterLeaveFunctionHooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) ou [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), doivent recevoir la `FunctionEnter2`, `FunctionLeave2`, et `FunctionTailcall2` pour chaque fonction. Toutefois, les profileurs peuvent implémenter `FunctionIDMapper` pour éviter de manière sélective recevoir ces rappels pour certaines fonctions en définissant `pbHookFunction` à `false`.  
  
 Les profileurs doivent être à tolérance de panne de cas où plusieurs threads d’une application profilée appellent simultanément la même méthode/fonction. Dans ce cas, le profileur peut recevoir plusieurs `FunctionIDMapper` rappels pour le même `FunctionID`. Le profileur doit être certain de retourner les mêmes valeurs de ce rappel lorsqu’elle est appelée plusieurs fois avec le même `FunctionID`.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [SetFunctionIDMapper, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [FunctionIDMapper2, fonction](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)
- [FunctionEnter2, fonction](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [FunctionLeave2, fonction](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [FunctionTailcall2, fonction](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [Fonctions statiques globales de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
