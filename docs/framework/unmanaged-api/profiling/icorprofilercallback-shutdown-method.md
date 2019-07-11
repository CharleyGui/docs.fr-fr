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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9d63dd911a5f674a3ce0b02ec78de443c7aebf84
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747171"
---
# <a name="icorprofilercallbackshutdown-method"></a>ICorProfilerCallback::Shutdown, méthode
Notifie le profileur que l’application est en cours d’arrêt.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Shutdown();  
```  
  
## <a name="remarks"></a>Notes  
 Le code du profileur ne peut pas appeler en toute sécurité les méthodes de la [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) interface après le `Shutdown` méthode est appelée. Tous les appels à `ICorProfilerInfo` méthodes entraînent un comportement indéfini après le `Shutdown` méthode retourne. Certains événements immuables peuvent encore se produire après l’arrêt ; le profileur doit veiller à retourner immédiatement lorsque cela se produit.  
  
 Le `Shutdown` méthode sera appelée uniquement si l’application managée est en cours de profilage démarré en tant que code géré (autrement dit, le frame initial sur la pile de processus est géré). Si l’application a démarré en tant que code non managé, mais a sauté ultérieurement dans le code managé, créant ainsi une instance du common language runtime (CLR), puis `Shutdown` ne sera pas appelé. Dans ce cas, le profileur doit inclure dans sa bibliothèque un `DllMain` valeur de routine qui utilise le DLL_PROCESS_DETACH pour libérer les ressources et exécuter le nettoyage de ses données, par exemple, vider des traces sur le disque et ainsi de suite.  
  
 En règle générale, le profileur doit faire face à des arrêts inattendus. Par exemple, un processus peut être arrêté par de Win32 `TerminateProcess` (méthode) (déclaré dans Winbase.h). Dans d’autres cas, le CLR arrêtera certains threads managés (threads d’arrière-plan) sans la remise des messages de destruction de façon ordonnée pour eux.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [Initialize, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)
