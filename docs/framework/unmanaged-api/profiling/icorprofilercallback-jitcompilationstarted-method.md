---
title: ICorProfilerCallback::JITCompilationStarted, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCompilationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCompilationStarted
helpviewer_keywords:
- JITCompilationStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationStarted method [.NET Framework profiling]
ms.assetid: 31782b36-d311-4518-8f45-25f65385af5b
topic_type:
- apiref
ms.openlocfilehash: 96ab77a36c0a0bddda0fca342433666dd19082d3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426194"
---
# <a name="icorprofilercallbackjitcompilationstarted-method"></a>ICorProfilerCallback::JITCompilationStarted, méthode
Notifie le profileur que le compilateur juste-à-temps (JIT) a commencé à compiler une fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT JITCompilationStarted(  
    [in] FunctionID functionId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a>Paramètres  
 `functionId`  
 dans ID de la fonction pour laquelle la compilation démarre.  
  
 `fIsSafeToBlock`  
 dans Valeur indiquant au profileur si le blocage affecte le fonctionnement du Runtime. La valeur est `true` si le blocage peut amener le runtime à attendre que le thread appelant retourne à partir de ce rappel ; Sinon, `false`.  
  
 Bien qu’une valeur de `true` n’endommage pas le runtime, elle peut incliner les résultats de profilage.  
  
## <a name="remarks"></a>Notes  
 Il est possible de recevoir plus d’une paire d' `JITCompilationStarted` et d’appels [ICorProfilerCallback :: JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md) pour chaque fonction, en raison de la façon dont le Runtime gère les constructeurs de classe. Par exemple, le runtime commence à effectuer une compilation JIT de la méthode A, mais le constructeur de classe de la classe B doit être exécuté. Par conséquent, le runtime JIT compile le constructeur pour la classe B et l’exécute. Pendant que le constructeur est en cours d’exécution, il effectue un appel à la méthode A, ce qui entraîne une nouvelle compilation juste-à-temps de la méthode A. Dans ce scénario, la première compilation JIT de la méthode A est arrêtée. Toutefois, les deux tentatives de compilation JIT de la méthode A sont signalées par des événements de compilation JIT. Si le profileur va remplacer le code MSIL (Microsoft Intermediate Language) pour la méthode A en appelant la méthode [ICorProfilerInfo :: SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) , il doit le faire pour les deux événements `JITCompilationStarted`, mais il peut utiliser le même bloc MSIL pour les deux.  
  
 Les profileurs doivent prendre en charge la séquence de rappels JIT dans les cas où deux threads effectuent simultanément des rappels. Par exemple, le thread A appelle `JITCompilationStarted`. Toutefois, avant que le thread A appelle `JITCompilationFinished`, le thread B appelle [ICorProfilerCallback :: ExceptionSearchFunctionEnter,](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) avec l’ID de fonction du rappel `JITCompilationStarted` du thread A. Il peut sembler que l’ID de fonction ne soit pas encore valide, car un appel à `JITCompilationFinished` n’a pas encore été reçu par le profileur. Toutefois, dans un cas comme celui-ci, l’ID de fonction est valide.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [JITCompilationFinished, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)
