---
title: ICorProfilerInfo3::SetEnterLeaveFunctionHooks3, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.SetEnterLeaveFunctionHooks3 Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3
helpviewer_keywords:
- SetEnterLeaveFunctionHooks3 method [.NET Framework profiling]
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method [.NET Framework profiling]
ms.assetid: f0621465-b84f-40ab-a4e5-56a7abc776a7
topic_type:
- apiref
ms.openlocfilehash: 3e07d2b61e85bb626613c40832c1a6aa499ef248
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868497"
---
# <a name="icorprofilerinfo3setenterleavefunctionhooks3-method"></a>ICorProfilerInfo3::SetEnterLeaveFunctionHooks3, méthode
Spécifie les fonctions implémentées par le profileur qui seront appelées sur les fonctions [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md)et [FunctionTailcall3](functiontailcall3-function.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks3(  
            [in] FunctionEnter3    *pFuncEnter3,  
            [in] FunctionLeave3    *pFuncLeave3,  
            [in] FunctionTailcall3 *pFuncTailcall3);  
```  
  
## <a name="parameters"></a>Parameters  
 `pFuncEnter3`  
 dans Pointeur vers l’implémentation à utiliser comme rappel `FunctionEnter3`.  
  
 `pFuncLeave3`  
 dans Pointeur vers l’implémentation à utiliser comme rappel `FunctionLeave3`.  
  
 `pFuncTailcall3`  
 dans Pointeur vers l’implémentation à utiliser comme rappel `FunctionTailcall3`.  
  
## <a name="remarks"></a>Notes  
 Les hooks [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md)et [FunctionTailcall3](functiontailcall3-function.md) ne fournissent pas de frame de pile et d’inspection des arguments. Pour accéder à ces informations, vous devez définir les indicateurs `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`et/ou `COR_PRF_ENABLE_FRAME_INFO`. Le profileur peut utiliser la méthode [ICorProfilerInfo :: SetEventMask](icorprofilerinfo-seteventmask-method.md) pour définir les indicateurs d’événement, puis utiliser la méthode [ICorProfilerInfo3 :: SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) pour inscrire votre implémentation de cette fonction.  
  
 Un seul ensemble de rappels peut être actif à la fois et la version la plus récente est prioritaire. Par conséquent, si un profileur appelle la [méthode SetEnterLeaveFunctionHooks2,](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) et la méthode `SetEnterLeaveFunctionHooks3`, `SetEnterLeaveFunctionHooks3` est utilisé.  
  
 La méthode `SetEnterLeaveFunctionHooks3` peut être appelée uniquement à partir du rappel [ICorProfilerCallback :: Initialize](icorprofilercallback-initialize-method.md) du profileur.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [FunctionEnter3](functionenter3-function.md)
- [FunctionLeave3](functionleave3-function.md)
- [FunctionTailcall3](functiontailcall3-function.md)
- [FunctionEnter3WithInfo](functionenter3withinfo-function.md)
- [FunctionLeave3WithInfo](functionleave3withinfo-function.md)
- [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)
- [Fonctions statiques globales de profilage](profiling-global-static-functions.md)
- [ICorProfilerInfo3](icorprofilerinfo3-interface.md)
- [Interfaces de profilage](profiling-interfaces.md)
- [Profilage](index.md)
