---
title: ICorProfilerCallback4::ReJITCompilationStarted, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITCompilationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITCompilationStarted
helpviewer_keywords:
- ReJITCompilationStarted method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITCompilationStarted method [.NET Framework profiling]
ms.assetid: 512fdd00-262a-4456-a075-365ef4133c4d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 58293929b576493d3751f9ce30ba00cec92e180c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758166"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a>ICorProfilerCallback4::ReJITCompilationStarted, méthode
Notifie le profileur que le compilateur juste-à-temps (JIT) a démarré recompiler une fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ReJITCompilationStarted(   
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a>Paramètres  
 `functionId`  
 [in] L’ID de la fonction que le compilateur JIT a commencé à recompiler.  
  
 `rejitId`  
 [in] L’ID de la recompilation de la nouvelle version de la fonction.  
  
 `fIsSafeToBlock`  
 [in] `true` pour indiquer que le blocage peut entraîner l’exécution pour attendre que le thread appelant retourner à partir de ce rappel ; `false` pour indiquer que le blocage n’affecte pas l’opération du runtime. La valeur `true` n’endommage pas le runtime, mais peut affecter les résultats de profilage.  
  
## <a name="remarks"></a>Notes  
 Il est possible de recevoir plus d’une paire de `ReJITCompilationStarted` et [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) appels de méthode pour chaque fonction en raison du mode le runtime gère les constructeurs de classe. Par exemple, le runtime commence à recompiler la méthode A, mais le constructeur de classe pour la classe B doit être exécutée. Par conséquent, le runtime recompile le constructeur de classe B et l’exécute. Alors que le constructeur est en cours d’exécution, il effectue un appel à la méthode A, ce qui entraîne la méthode A de nouveau être recompilée. Dans ce scénario, la première recompilation de la méthode A est arrêtée. Toutefois, les deux tente de recompiler la méthode A sont signalé avec les événements de recompilation JIT.  
  
 Les profileurs doivent prendre en charge de la séquence des rappels de recompilation JIT dans les cas où deux threads effectuent simultanément des rappels. Par exemple, le thread A appelle `ReJITCompilationStarted`; Toutefois, avant les appels du thread A [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md), thread B appelle [ICorProfilerCallback::ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) avec l’ID de fonction à partir de la `ReJITCompilationStarted` rappel pour le thread A. Il peut apparaître que l’ID de fonction n'est pas encore valide, car un appel à [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) n’a pas encore été reçu par le profileur. Toutefois, dans ce cas, l’ID de fonction est valide.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback4, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [JITCompilationFinished, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)
- [ReJITCompilationFinished, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)
