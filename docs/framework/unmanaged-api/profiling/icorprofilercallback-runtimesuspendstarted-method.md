---
title: ICorProfilerCallback::RuntimeSuspendStarted, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeSuspendStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendStarted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendStarted method [.NET Framework profiling]
- RuntimeSuspendStarted method [.NET Framework profiling]
ms.assetid: c8461cac-e31b-4efa-ad2c-26598173eb96
topic_type:
- apiref
ms.openlocfilehash: e88f6356c2e29a1d8a9e49527c5921e8155c3ce4
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865881"
---
# <a name="icorprofilercallbackruntimesuspendstarted-method"></a>ICorProfilerCallback::RuntimeSuspendStarted, méthode
Indique au profileur que le runtime est sur le paragraphe d’interrompre tous les threads d’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT RuntimeSuspendStarted(  
    [in] COR_PRF_SUSPEND_REASON suspendReason);  
```  
  
## <a name="parameters"></a>Parameters  
 `suspendReason`  
 dans Valeur de l’énumération [COR_PRF_SUSPEND_REASON](cor-prf-suspend-reason-enumeration.md) qui indique la raison de la suspension.  
  
## <a name="remarks"></a>Notes  
 Tous les threads d’exécution qui se trouvent dans du code non managé sont autorisés à continuer à s’exécuter jusqu’à ce qu’ils essaient d’entrer à nouveau dans le Runtime. À ce stade, ils sont également suspendus jusqu’à la reprise du Runtime. Cela s’applique également aux nouveaux threads qui entrent dans le Runtime. Tous les threads du runtime sont suspendus immédiatement s’ils sont déjà dans du code interruptible, ou ils sont invités à s’interrompre lorsqu’ils atteignent du code interruptible.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](icorprofilercallback-interface.md)
- [RuntimeSuspendAborted, méthode](icorprofilercallback-runtimesuspendaborted-method.md)
- [RuntimeSuspendFinished, méthode](icorprofilercallback-runtimesuspendfinished-method.md)
