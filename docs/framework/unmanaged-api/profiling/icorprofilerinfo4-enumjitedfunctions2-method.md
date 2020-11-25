---
title: ICorProfilerInfo4::EnumJITedFunctions2, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.EnumJITedFunctions2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::EnumJITedFunctions2
helpviewer_keywords:
- EnumJITedFunctions2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::EnumJITedFunctions2 method [.NET Framework profiling]
ms.assetid: 40e9a1be-9bd2-4fad-9921-34a84b61c1e3
topic_type:
- apiref
ms.openlocfilehash: 2a6ddaef7b64427f8349abedbbd85b4d82a0b88c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697790"
---
# <a name="icorprofilerinfo4enumjitedfunctions2-method"></a>ICorProfilerInfo4::EnumJITedFunctions2, méthode

Retourne un énumérateur pour toutes les fonctions qui ont été précédemment compilées juste-à-temps et qui ont été recompilées juste-à-temps. Cette méthode remplace la méthode [ICorProfilerInfo3 :: EnumJITedFunctions,](icorprofilerinfo3-enumjitedfunctions-method.md) , qui n’énumère pas les ID recompilés juste-à-temps.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a>Paramètres  

 `ppEnum`  
 à Pointeur vers l’énumérateur [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) .  
  
## <a name="remarks"></a>Remarques  

 Cette méthode peut se chevaucher avec `JITCompilation` les rappels tels que la méthode [ICorProfilerCallback :: JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) . L’énumération retournée comprend des valeurs pour le `COR_PRF_FUNCTION::reJitId` champ. La méthode [ICorProfilerInfo3 :: EnumJITedFunctions,](icorprofilerinfo3-enumjitedfunctions-method.md) , que cette méthode remplace, n’énumère pas les ID recompilés juste-à-temps, car le `COR_PRF_FUNCTION::reJitId` champ a toujours la valeur 0. La `ICorProfilerInfo4::EnumJITedFunctions` méthode énumère les ID recompilés juste-à-temps, car le `COR_PRF_FUNCTION::reJitId` champ est défini correctement. Notez que la méthode [ICorProfilerInfo4 :: enumjitedfunctions2,](icorprofilerinfo4-enumjitedfunctions2-method.md) peut déclencher un garbage collection, contrairement à la [méthode ICorProfilerInfo3 :: EnumJITedFunctions,](icorprofilerinfo3-enumjitedfunctions-method.md) .  Pour plus d’informations, consultez [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md).  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [EnumJITedFunctions, méthode](icorprofilerinfo3-enumjitedfunctions-method.md)
- [ICorProfilerInfo4, interface](icorprofilerinfo4-interface.md)
- [Interfaces de profilage](profiling-interfaces.md)
- [Profilage](index.md)
