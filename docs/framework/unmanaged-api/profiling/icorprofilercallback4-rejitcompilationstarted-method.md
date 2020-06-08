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
ms.openlocfilehash: 6e340fa08800f31d36e6cfb280cac847a4fca548
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499348"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a>ICorProfilerCallback4::ReJITCompilationStarted, méthode
Notifie le profileur que le compilateur juste-à-temps (JIT) a commencé à recompiler une fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ReJITCompilationStarted(
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a>Paramètres  
 `functionId`  
 dans ID de la fonction que le compilateur JIT a commencé à recompiler.  
  
 `rejitId`  
 dans ID de recompilation de la nouvelle version de la fonction.  
  
 `fIsSafeToBlock`  
 [in] `true` pour indiquer que le blocage peut amener le runtime à attendre que le thread appelant retourne à partir de ce rappel ; `false`pour indiquer que le blocage n’affectera pas le fonctionnement du Runtime. Une valeur de `true` n’endommage pas le runtime, mais peut affecter les résultats de profilage.  
  
## <a name="remarks"></a>Remarques  
 Il est possible de recevoir plus d’une paire d' `ReJITCompilationStarted` appels de méthode [rejitcompilationfinished,](icorprofilercallback4-rejitcompilationfinished-method.md) pour chaque fonction en raison de la façon dont le Runtime gère les constructeurs de classe. Par exemple, le runtime commence à recompiler la méthode A, mais le constructeur de classe pour la classe B doit être exécuté. Par conséquent, le runtime RECOMPILE le constructeur pour la classe B et l’exécute. Pendant que le constructeur est en cours d’exécution, il effectue un appel à la méthode A, ce qui entraîne la recompilation de la méthode A. Dans ce scénario, la première recompilation de la méthode A est arrêtée. Toutefois, les deux tentatives de recompilation de la méthode A sont signalées avec les événements de recompilation JIT.  
  
 Les profileurs doivent prendre en charge la séquence de rappels de recompilation JIT dans les cas où deux threads effectuent simultanément des rappels. Par exemple, le thread A appelle `ReJITCompilationStarted` . Toutefois, avant que le thread a appelle [rejitcompilationfinished,](icorprofilercallback4-rejitcompilationfinished-method.md), thread B appelle [ICorProfilerCallback :: ExceptionSearchFunctionEnter,](icorprofilercallback-exceptionsearchfunctionenter-method.md) avec l’ID de fonction du `ReJITCompilationStarted` rappel pour le thread A. Il peut sembler que l’ID de fonction ne soit pas encore valide, car un appel à [rejitcompilationfinished,](icorprofilercallback4-rejitcompilationfinished-method.md) n’a pas encore été reçu par le profileur. Toutefois, dans ce cas, l’ID de fonction est valide.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](icorprofilercallback-interface.md)
- [ICorProfilerCallback4, interface](icorprofilercallback4-interface.md)
- [JITCompilationFinished, méthode](icorprofilercallback-jitcompilationfinished-method.md)
- [ReJITCompilationFinished, méthode](icorprofilercallback4-rejitcompilationfinished-method.md)
