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
ms.openlocfilehash: 54f7dae511c8bf25dc96451e6477acf26655430a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503196"
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
  
## <a name="remarks"></a>Remarques  
 La `RuntimeThreadSuspended` notification peut se produire à tout moment entre [ICorProfilerCallback :: RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) et les rappels [ICorProfilerCallback :: RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) associés. Les notifications qui se produisent entre [ICorProfilerCallback :: RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) et `RuntimeResumeStarted` sont pour les threads qui étaient exécutés dans du code non managé et qui ont été suspendues lors de l’entrée dans le Runtime.  
  
 En règle générale, ce rappel se produit juste après l’interruption d’un thread. Toutefois, si le thread en cours d’exécution (le thread qui a appelé ce rappel) est celui qui est suspendu, ce rappel se produit juste avant la suspension du thread.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](icorprofilercallback-interface.md)
- [RuntimeThreadResumed, méthode](icorprofilercallback-runtimethreadresumed-method.md)
