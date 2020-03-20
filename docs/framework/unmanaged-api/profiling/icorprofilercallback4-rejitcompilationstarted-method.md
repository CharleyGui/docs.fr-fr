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
ms.openlocfilehash: be257930ca0fad658afa75d6efa4573d4f888a2b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177079"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a>ICorProfilerCallback4::ReJITCompilationStarted, méthode
Informe le profileur que le compilateur juste-à-temps (JIT) a commencé à recomposer une fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ReJITCompilationStarted(
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a>Paramètres  
 `functionId`  
 [dans] L’ID de la fonction que le compilateur JIT a commencé à recomposer.  
  
 `rejitId`  
 [dans] L’ID de recomplération de la nouvelle version de la fonction.  
  
 `fIsSafeToBlock`  
 [dans] `true` pour indiquer que le blocage peut faire attendre le temps d’exécution pour que le fil d’appel revienne de ce rappel; `false` pour indiquer que le blocage n’affectera pas le fonctionnement de l’exécution. Une valeur `true` de ne nuit pas à l’exécution, mais peut affecter les résultats de profilage.  
  
## <a name="remarks"></a>Notes   
 Il est possible de recevoir `ReJITCompilationStarted` plus d’une paire de et [ReJITCompilationLa](icorprofilercallback4-rejitcompilationfinished-method.md) méthode définie appelle pour chaque fonction en raison de la façon dont le temps d’exécution gère les constructeurs de classe. Par exemple, le temps d’exécution commence à recomposer la méthode A, mais le constructeur de classe pour la classe B doit être exécuté. Par conséquent, le temps d’exécution recompile le constructeur pour la classe B et l’exécute. Pendant que le constructeur est en marche, il fait un appel à la méthode A, ce qui provoque la méthode A à être recompilé à nouveau. Dans ce scénario, la première récompatation de la méthode A est stoppée. Cependant, les deux tentatives de recompiler la méthode A sont signalées avec des événements de recomplération JIT.  
  
 Les profileurs doivent prendre en charge la séquence des rappels de recomplissement JIT dans les cas où deux threads effectuent simultanément des rappels. Par exemple, les `ReJITCompilationStarted`appels de fil A ; cependant, avant le fil A appelle [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md), thread B appelle [ICorProfilerCallback::ExceptionSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) avec l’ID de fonction de la callback pour le `ReJITCompilationStarted` fil A. Il peut sembler que l’ID de fonction ne devrait pas encore être valide parce qu’un appel à [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) n’avait pas encore été reçu par le profileur. Toutefois, dans ce cas, l’ID de fonction est valide.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](icorprofilercallback-interface.md)
- [ICorProfilerCallback4, interface](icorprofilercallback4-interface.md)
- [JITCompilationFinished, méthode](icorprofilercallback-jitcompilationfinished-method.md)
- [ReJITCompilationFinished, méthode](icorprofilercallback4-rejitcompilationfinished-method.md)
