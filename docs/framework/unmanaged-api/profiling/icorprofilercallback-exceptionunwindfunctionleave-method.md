---
title: ICorProfilerCallback::ExceptionUnwindFunctionLeave, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFunctionLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionLeave method [.NET Framework profiling]
- ExceptionUnwindFunctionLeave method [.NET Framework profiling]
ms.assetid: ebaad1d5-ee0a-4cb0-96bc-8ba5d371b747
topic_type:
- apiref
ms.openlocfilehash: 9d3e39cd910240b965896f1b866b0c21de616a57
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866336"
---
# <a name="icorprofilercallbackexceptionunwindfunctionleave-method"></a>ICorProfilerCallback::ExceptionUnwindFunctionLeave, méthode
Notifie le profileur que la phase de déroulement de la gestion des exceptions a terminé le déroulement d’une fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ExceptionUnwindFunctionLeave();  
```  
  
## <a name="remarks"></a>Notes  
 Lorsque la méthode `ExceptionUnwindFunctionLeave` est appelée, l’instance de la fonction et ses données de pile sont supprimés de la pile.  
  
 Le profileur ne doit pas se bloquer pendant cet appel, car la pile n’est peut-être pas dans un État qui autorise garbage collection, et par conséquent, Preemptive garbage collection ne peut pas être activé. Si le profileur est bloqué ici et qu’une garbage collection est tentée, le runtime se bloque jusqu’à ce que ce rappel soit retourné.  
  
 En outre, pendant cet appel, le profileur ne doit pas appeler dans du code managé ou de quelque manière qu’il soit à l’origine d’une allocation de mémoire managée.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](icorprofilercallback-interface.md)
- [ExceptionUnwindFunctionEnter, méthode](icorprofilercallback-exceptionunwindfunctionenter-method.md)
