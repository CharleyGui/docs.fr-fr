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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 31766fed66368c044b188b5a58452a5e264a25cb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782202"
---
# <a name="icorprofilerinfo2setenterleavefunctionhooks2-method"></a>ICorProfilerInfo2::SetEnterLeaveFunctionHooks2, méthode
Spécifie les fonctions implémentées par le profileur à être appelée sur les versions mises à jour des « entrer », « quitter » et « tailcall » de fonctions managées.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks2(  
    [in] FunctionEnter2    *pFuncEnter,  
    [in] FunctionLeave2    *pFuncLeave,  
    [in] FunctionTailcall2 *pFuncTailcall);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pFuncEnter`  
 [in] Un pointeur vers l’implémentation à utiliser comme la [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) rappel.  
  
 `pFuncLeave`  
 [in] Un pointeur vers l’implémentation à utiliser comme la [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) rappel.  
  
 `pFuncTailcall`  
 [in] Un pointeur vers l’implémentation à utiliser comme la [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) rappel.  
  
## <a name="remarks"></a>Notes  
 Le `SetEnterLeaveFunctionHooks2` méthode est similaire à la [ICorProfilerInfo::SetEnterLeaveFunctionHooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) (méthode). Utilisez l’ancienne base de données pour spécifier les fonctions à utiliser comme les versions plus récentes de l’entrée/leave/tailcall les rappels et ce dernier pour spécifier les fonctions à utiliser comme les versions antérieures des rappels de l’entrée/leave/tailcall.  
  
 Qu’un seul jeu de rappels peut être actif à la fois. Par conséquent, si un profileur appelle `ICorProfilerInfo::SetEnterLeaveFunctionHooks` et `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` est utilisé.  
  
 Le `SetEnterLeaveFunctionHooks2` méthode peut être appelée uniquement à partir du profileur [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) rappel.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
