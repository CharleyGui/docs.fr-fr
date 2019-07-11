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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 03b7ca218318df517832d198e72d4f79d30827b8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779241"
---
# <a name="icorprofilercallback4getrejitparameters-method"></a>ICorProfilerCallback4::GetReJITParameters, méthode
Permet au profileur de code définir les indicateurs de génération de code de remplacement pour un nouveau corps de méthode recompilée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetReJITParameters(     [in] ModuleID moduleId,     [in] mdMethodDef methodId,     [in] ICorProfilerFunctionControl *pFunctionControl);  
```  
  
## <a name="parameters"></a>Paramètres  
 `moduleID`  
 [in] Le module qui contient la méthode pour laquelle le CLR doit les paramètres de recompilation JIT.  
  
 `methodId`  
 [in] Le `MethodDef` de la méthode pour laquelle le CLR doit les paramètres de recompilation JIT.  
  
 `pFunctionControl`  
 [in] Un pointeur vers un [ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) interface que le profileur peut utiliser pour fournir des informations de recompilation JIT pour la méthode en cours de recompilation.  
  
## <a name="remarks"></a>Notes  
 Les problèmes CLR un `GetReJITParameters` rappel afin que le profileur peut spécifier les paramètres pour la recompilation d’une méthode donnée. Le `GetReJITParameters` rappel est émis une seule fois par la fonction ; les paramètres fournis par le profileur s’appliquent à toutes les instances de cette fonction.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback4, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [JITCompilationStarted, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)
- [ReJITCompilationStarted, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)
