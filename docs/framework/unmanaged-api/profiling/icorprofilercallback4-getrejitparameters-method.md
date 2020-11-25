---
title: ICorProfilerCallback4::GetReJITParameters, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.GetReJITParameters
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::GetReJITParameters
helpviewer_keywords:
- ICorProfilerCallback4::GetReJITParameters method [.NET Framework profiling]
- GetReJITParameters method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 0e9bfe07-9f20-498c-b568-9017c8f6056c
topic_type:
- apiref
ms.openlocfilehash: 2cee763674da7472ca48355e7eaba3b7dfb7adbe
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730303"
---
# <a name="icorprofilercallback4getrejitparameters-method"></a>ICorProfilerCallback4::GetReJITParameters, méthode

Permet au profileur de code de définir d’autres indicateurs de génération de code pour un nouveau corps de méthode recompilée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetReJITParameters(     [in] ModuleID moduleId,     [in] mdMethodDef methodId,     [in] ICorProfilerFunctionControl *pFunctionControl);  
```  
  
## <a name="parameters"></a>Paramètres  

 `moduleID`  
 dans Module qui contient la méthode pour laquelle le CLR a besoin de paramètres de recompilation JIT.  
  
 `methodId`  
 dans `MethodDef` De la méthode pour laquelle le CLR a besoin de paramètres de recompilation JIT.  
  
 `pFunctionControl`  
 dans Pointeur vers une interface [ICorProfilerFunctionControl](icorprofilerfunctioncontrol-interface.md) que le profileur peut utiliser pour fournir des informations de recompilation JIT pour la méthode en cours de recompilation.  
  
## <a name="remarks"></a>Remarques  

 Le CLR émet un `GetReJITParameters` rappel afin que le profileur puisse spécifier les paramètres pour recompiler une méthode donnée. Le `GetReJITParameters` rappel est émis une seule fois par fonction ; les paramètres fournis par le profileur s’appliquent à toutes les instances de cette fonction.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](icorprofilercallback-interface.md)
- [ICorProfilerCallback4, interface](icorprofilercallback4-interface.md)
- [JITCompilationStarted, méthode](icorprofilercallback-jitcompilationstarted-method.md)
- [ReJITCompilationStarted, méthode](icorprofilercallback4-rejitcompilationstarted-method.md)
