---
title: ICorProfilerInfo2::SetEnterLeaveFunctionHooks2, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.SetEnterLeaveFunctionHooks2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2
helpviewer_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
- SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
ms.assetid: 3c26b3e7-f72b-48a5-bf8c-edc122523a4b
topic_type:
- apiref
ms.openlocfilehash: 7eac42e1d8132ca9e6d6c6b43efd43b88c1e5d3d
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868575"
---
# <a name="icorprofilerinfo2setenterleavefunctionhooks2-method"></a>ICorProfilerInfo2::SetEnterLeaveFunctionHooks2, méthode
Spécifie les fonctions implémentées par le profileur à appeler sur les versions mises à jour des raccordements « Enter », « Leave » et « tailcall » des fonctions managées.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks2(  
    [in] FunctionEnter2    *pFuncEnter,  
    [in] FunctionLeave2    *pFuncLeave,  
    [in] FunctionTailcall2 *pFuncTailcall);  
```  
  
## <a name="parameters"></a>Parameters  
 `pFuncEnter`  
 dans Pointeur vers l’implémentation à utiliser comme rappel [FunctionEnter2](functionenter2-function.md) .  
  
 `pFuncLeave`  
 dans Pointeur vers l’implémentation à utiliser comme rappel [FunctionLeave2](functionleave2-function.md) .  
  
 `pFuncTailcall`  
 dans Pointeur vers l’implémentation à utiliser comme rappel [FunctionTailcall2](functiontailcall2-function.md) .  
  
## <a name="remarks"></a>Notes  
 La méthode `SetEnterLeaveFunctionHooks2` est semblable à la méthode [ICorProfilerInfo :: SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md) . Utilisez la première pour spécifier les fonctions à utiliser comme versions plus récentes des rappels entrée/sortie/tailcall, et la seconde pour spécifier les fonctions à utiliser comme versions antérieures des rappels entrée/sortie/tailcall.  
  
 Un seul ensemble de rappels peut être actif à la fois. Ainsi, si un profileur appelle à la fois `ICorProfilerInfo::SetEnterLeaveFunctionHooks` et `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` est utilisé.  
  
 La méthode `SetEnterLeaveFunctionHooks2` peut être appelée uniquement à partir du rappel [ICorProfilerCallback :: Initialize](icorprofilercallback-initialize-method.md) du profileur.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interface](icorprofilerinfo2-interface.md)
