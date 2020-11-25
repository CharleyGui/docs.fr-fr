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
ms.openlocfilehash: 18aed5c5314fc1057767b599c538952a1d4d6b57
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722230"
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
 dans Pointeur vers l’implémentation à utiliser comme rappel [FunctionEnter](functionenter-function.md) .  
  
 `pFuncLeave`  
 dans Pointeur vers l’implémentation à utiliser comme rappel [FunctionLeave](functionleave-function.md) .  
  
 `pFuncTailcall`  
 dans Pointeur vers l’implémentation à utiliser comme rappel [FunctionTailcall (](functiontailcall-function.md) .  
  
## <a name="remarks"></a>Remarques  

 Dans la version de .NET Framework 1,0, chaque pointeur de fonction peut avoir la valeur null pour désactiver ce rappel correspondant.  
  
 Un seul ensemble de rappels peut être actif à la fois. Ainsi, si un profileur appelle à la fois `SetEnterLeaveFunctionHooks` et [ICorProfilerInfo2 :: SetEnterLeaveFunctionHooks2,](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), `SetEnterLeaveFunctionHooks2` est prioritaire.  
  
 La `SetEnterLeaveFunctionHooks` méthode peut être appelée uniquement à partir du rappel [ICorProfilerCallback :: Initialize](icorprofilercallback-initialize-method.md) du profileur.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](icorprofilerinfo-interface.md)
