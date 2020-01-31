---
title: ICorProfilerCallback::Shutdown, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.Shutdown
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::Shutdown
helpviewer_keywords:
- ICorProfilerCallback::Shutdown method [.NET Framework profiling]
- Shutdown method [.NET Framework profiling]
ms.assetid: 1ea194f0-a331-4855-a2ce-37393b8e5f84
topic_type:
- apiref
ms.openlocfilehash: 490f9dd5446a51bd07881cdb9825d737e380a63e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865855"
---
# <a name="icorprofilercallbackshutdown-method"></a>ICorProfilerCallback::Shutdown, méthode
Notifie le profileur que l’application est en cours d’arrêt.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Shutdown();  
```  
  
## <a name="remarks"></a>Notes  
 Le code du profileur ne peut pas appeler sans risque les méthodes de l’interface [ICorProfilerInfo](icorprofilerinfo-interface.md) après l’appel de la méthode `Shutdown`. Tous les appels aux méthodes `ICorProfilerInfo` entraînent un comportement indéfini après le retour de la méthode `Shutdown`. Certains événements immuables peuvent encore se produire après l’arrêt ; le profileur doit effectuer un retour immédiatement lorsque cela se produit.  
  
 La méthode `Shutdown` est appelée uniquement si l’application managée en cours de profilage a démarré en tant que code managé (autrement dit, le frame initial sur la pile de processus est managé). Si l’application a démarré en tant que code non managé mais est ensuite basculée dans le code managé, créant ainsi une instance du common language runtime (CLR), `Shutdown` ne sera pas appelé. Dans ce cas, le profileur doit inclure dans sa bibliothèque une routine de `DllMain` qui utilise la valeur DLL_PROCESS_DETACH pour libérer des ressources et effectuer le traitement du nettoyage de ses données, telles que le vidage des traces sur le disque, etc.  
  
 En général, le profileur doit faire face à des arrêts inattendus. Par exemple, un processus peut être arrêté par Win32 `TerminateProcess` méthode (déclaré dans Winbase. h). Dans d’autres cas, le CLR arrêtera certains threads managés (threads d’arrière-plan) sans fournir de messages de destruction ordonnés pour eux.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](icorprofilercallback-interface.md)
- [Initialize, méthode](icorprofilercallback-initialize-method.md)
