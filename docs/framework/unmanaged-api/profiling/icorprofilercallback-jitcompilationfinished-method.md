---
title: ICorProfilerCallback::JITCompilationFinished, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCompilationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCompilationFinished
helpviewer_keywords:
- JITCompilationFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationFinished method [.NET Framework profiling]
ms.assetid: 8dcd7537-d0c6-498c-8a56-2c060310ef65
topic_type:
- apiref
ms.openlocfilehash: 1bbdfa93913b9fdf8aa164c8ca6c35cd33a228df
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449924"
---
# <a name="icorprofilercallbackjitcompilationfinished-method"></a>ICorProfilerCallback::JITCompilationFinished, méthode
Notifie le profileur que le compilateur juste-à-temps (JIT) a terminé la compilation d’une fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT JITCompilationFinished(  
    [in] FunctionID functionId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a>Paramètres  
 `functionId`  
 dans ID de la fonction qui a été compilée.  
  
 `hrStatus`  
 dans Valeur indiquant si la compilation a réussi.  
  
 `fIsSafeToBlock`  
 dans Valeur indiquant au profileur si le blocage affecte le fonctionnement du Runtime. La valeur est `true` si le blocage peut amener le runtime à attendre que le thread appelant retourne à partir de ce rappel ; Sinon, `false`.  
  
 Bien qu’une valeur de `true` n’endommage pas le runtime, elle peut incliner les résultats de profilage.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [JITCompilationStarted, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)
