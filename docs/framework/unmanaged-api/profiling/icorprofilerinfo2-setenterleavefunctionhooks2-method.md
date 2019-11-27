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
ms.openlocfilehash: 4068c8fee13a6086bc6b48bcc6d4117357062747
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449786"
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
  
## <a name="parameters"></a>Paramètres  
 `pFuncEnter`  
 dans Pointeur vers l’implémentation à utiliser comme rappel [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) .  
  
 `pFuncLeave`  
 dans Pointeur vers l’implémentation à utiliser comme rappel [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) .  
  
 `pFuncTailcall`  
 dans Pointeur vers l’implémentation à utiliser comme rappel [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) .  
  
## <a name="remarks"></a>Notes  
 La méthode `SetEnterLeaveFunctionHooks2` est semblable à la méthode [ICorProfilerInfo :: SetEnterLeaveFunctionHooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) . Utilisez la première pour spécifier les fonctions à utiliser comme versions plus récentes des rappels entrée/sortie/tailcall, et la seconde pour spécifier les fonctions à utiliser comme versions antérieures des rappels entrée/sortie/tailcall.  
  
 Un seul ensemble de rappels peut être actif à la fois. Ainsi, si un profileur appelle à la fois `ICorProfilerInfo::SetEnterLeaveFunctionHooks` et `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` est utilisé.  
  
 La méthode `SetEnterLeaveFunctionHooks2` peut être appelée uniquement à partir du rappel [ICorProfilerCallback :: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) du profileur.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
