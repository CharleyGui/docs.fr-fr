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
ms.openlocfilehash: 9761eb5085a77279c4d07d39946a5ad1453ecaaf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717234"
---
# <a name="icorprofilercallbackshutdown-method"></a>ICorProfilerCallback::Shutdown, méthode

Notifie le profileur que l’application est en cours d’arrêt.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Shutdown();  
```  
  
## <a name="remarks"></a>Notes  

 Le code du profileur ne peut pas appeler sans risque les méthodes de l’interface [ICorProfilerInfo](icorprofilerinfo-interface.md) après l’appel de la `Shutdown` méthode. Tous les appels aux `ICorProfilerInfo` méthodes entraînent un comportement indéfini après le `Shutdown` retour de la méthode. Certains événements immuables peuvent encore se produire après l’arrêt ; le profileur doit effectuer un retour immédiatement lorsque cela se produit.  
  
 La `Shutdown` méthode est appelée uniquement si l’application managée en cours de profilage a démarré en tant que code managé (autrement dit, le frame initial sur la pile de processus est managé). Si l’application a démarré en tant que code non managé mais est ensuite basculée dans le code managé, la création d’une instance du common language runtime (CLR) ne sera `Shutdown` pas appelée. Dans ce cas, le profileur doit inclure dans sa bibliothèque une `DllMain` routine qui utilise la valeur DLL_PROCESS_DETACH pour libérer des ressources et effectuer le traitement du nettoyage de ses données, telles que le vidage des traces sur le disque, etc.  
  
 En général, le profileur doit faire face à des arrêts inattendus. Par exemple, un processus peut être arrêté par la `TerminateProcess` méthode Win32 (déclarée dans Winbase. h). Dans d’autres cas, le CLR arrêtera certains threads managés (threads d’arrière-plan) sans fournir de messages de destruction ordonnés pour eux.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](icorprofilercallback-interface.md)
- [Initialize, méthode](icorprofilercallback-initialize-method.md)
