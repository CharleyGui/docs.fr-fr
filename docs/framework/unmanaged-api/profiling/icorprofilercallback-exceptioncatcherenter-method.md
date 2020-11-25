---
title: ICorProfilerCallback::ExceptionCatcherEnter, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCatcherEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCatcherEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionCatcherEnter method [.NET Framework profiling]
- ExceptionCatcherEnter method [.NET Framework profiling]
ms.assetid: 41462329-a648-46f0-ae6d-728b94c31aa9
topic_type:
- apiref
ms.openlocfilehash: 97b9f517a24a7d82b7697cd0723628ede073b537
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700156"
---
# <a name="icorprofilercallbackexceptioncatcherenter-method"></a>ICorProfilerCallback::ExceptionCatcherEnter, méthode

Indique au profileur que le contrôle est passé au bloc approprié `catch` .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ExceptionCatcherEnter(  
    [in] FunctionID functionId,  
    [in] ObjectID   objectId);  
```  
  
## <a name="parameters"></a>Paramètres

- `functionId`

  \[in] identificateur de la fonction contenant le `catch` bloc.
  
- `objectId`

  \[in] identificateur de l’exception gérée.

## <a name="remarks"></a>Remarques  

 La `ExceptionCatcherEnter` méthode est appelée uniquement si le point catch se trouve dans le code compilé avec le compilateur juste-à-temps (JIT). Une exception interceptée dans du code non managé ou dans le code interne du runtime n’appelle pas cette notification. La `objectId` valeur est repassée, car une garbage collection aurait pu déplacer l’objet depuis la `ExceptionThrown` notification.  
  
 Le profileur ne doit pas se bloquer dans son implémentation de cette méthode, car la pile n’est peut-être pas dans un État qui autorise garbage collection, et par conséquent, Preemptive garbage collection ne peut pas être activé. Si le profileur est bloqué ici et que garbage collection est tentée, le runtime se bloque jusqu’à ce que ce rappel soit retourné.  
  
 L’implémentation du profileur de cette méthode ne doit pas appeler dans du code managé ou de quelque manière qu’elle provoque une allocation de mémoire managée.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](icorprofilercallback-interface.md)
- [ExceptionCatcherLeave, méthode](icorprofilercallback-exceptioncatcherleave-method.md)
