---
title: ICorProfilerInfo::SetEnterLeaveFunctionHooks, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetEnterLeaveFunctionHooks
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetEnterLeaveFunctionHooks
helpviewer_keywords:
- SetEnterLeaveFunctionHooks method [.NET Framework profiling]
- ICorProfilerInfo::SetEnterLeaveFunctionHooks method [.NET Framework profiling]
ms.assetid: 72399636-c219-4ffd-8ac8-39432c9d4641
topic_type:
- apiref
ms.openlocfilehash: 45593e7e30e1c8f8036489936aab3c607b01dd52
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438646"
---
# <a name="icorprofilerinfosetenterleavefunctionhooks-method"></a>ICorProfilerInfo::SetEnterLeaveFunctionHooks, méthode
Spécifie les fonctions implémentées par le profileur à appeler sur les raccordements « Enter », « Leave » et « tailcall » des fonctions managées.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks(  
    [in] FunctionEnter    *pFuncEnter,  
    [in] FunctionLeave    *pFuncLeave,  
    [in] FunctionTailcall *pFuncTailcall);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pFuncEnter`  
 dans Pointeur vers l’implémentation à utiliser comme rappel [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) .  
  
 `pFuncLeave`  
 dans Pointeur vers l’implémentation à utiliser comme rappel [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) .  
  
 `pFuncTailcall`  
 dans Pointeur vers l’implémentation à utiliser comme rappel [FunctionTailcall (](../../../../docs/framework/unmanaged-api/profiling/functiontailcall-function.md) .  
  
## <a name="remarks"></a>Notes  
 Dans la version de .NET Framework 1,0, chaque pointeur de fonction peut avoir la valeur null pour désactiver ce rappel correspondant.  
  
 Un seul ensemble de rappels peut être actif à la fois. Ainsi, si un profileur appelle à la fois `SetEnterLeaveFunctionHooks` et [ICorProfilerInfo2 :: SetEnterLeaveFunctionHooks2,](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), `SetEnterLeaveFunctionHooks2` est prioritaire.  
  
 La méthode `SetEnterLeaveFunctionHooks` peut être appelée uniquement à partir du rappel [ICorProfilerCallback :: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) du profileur.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
