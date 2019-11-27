---
title: ICorProfilerCallback::RuntimeThreadSuspended, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeThreadSuspended
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeThreadSuspended
helpviewer_keywords:
- RuntimeThreadSuspended method [.NET Framework profiling]
- ICorProfilerCallback::RuntimeThreadSuspended method [.NET Framework profiling]
ms.assetid: de830a8b-6ee1-4900-ace3-4237108f6b12
topic_type:
- apiref
ms.openlocfilehash: 509d6cd2e65c2eb8c92f6d79deae9e01e75298f6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433447"
---
# <a name="icorprofilercallbackruntimethreadsuspended-method"></a>ICorProfilerCallback::RuntimeThreadSuspended, méthode
Indique au profileur que le thread spécifié a été suspendu ou est sur le lieu d’être suspendu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT RuntimeThreadSuspended(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a>Paramètres  
 `threadId`  
 dans ID du thread qui a été suspendu.  
  
## <a name="remarks"></a>Notes  
 La notification `RuntimeThreadSuspended` peut se produire à tout moment entre [ICorProfilerCallback :: RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) et les rappels [ICorProfilerCallback :: RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) associés. Les notifications qui se produisent entre [ICorProfilerCallback :: RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) et `RuntimeResumeStarted` sont pour les threads qui étaient exécutés dans du code non managé et qui ont été suspendus lors de l’entrée dans le Runtime.  
  
 En règle générale, ce rappel se produit juste après l’interruption d’un thread. Toutefois, si le thread en cours d’exécution (le thread qui a appelé ce rappel) est celui qui est suspendu, ce rappel se produit juste avant la suspension du thread.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [RuntimeThreadResumed, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)
