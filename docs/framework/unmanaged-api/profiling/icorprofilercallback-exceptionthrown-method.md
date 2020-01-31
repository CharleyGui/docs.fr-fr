---
title: ICorProfilerCallback::ExceptionThrown, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionThrown
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionThrown
helpviewer_keywords:
- ExceptionThrown method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionThrown method [.NET Framework profiling]
ms.assetid: f1a23f3b-ac21-4905-8abf-8ea59f15af53
topic_type:
- apiref
ms.openlocfilehash: b1799472c4923aaccfabeae459ad72f6ae94c80d
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866375"
---
# <a name="icorprofilercallbackexceptionthrown-method"></a>ICorProfilerCallback::ExceptionThrown, méthode
Notifie le profileur qu’une exception a été levée.  
  
> [!NOTE]
> Cette fonction est appelée uniquement si l’exception atteint le code managé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ExceptionThrown(  
    [in] ObjectID thrownObjectId);  
```  
  
## <a name="parameters"></a>Parameters

- `thrownObjectId`

  \[in] ID de l’objet qui a provoqué la levée de l’exception.
  
## <a name="remarks"></a>Notes  
 Le profileur ne doit pas se bloquer dans son implémentation de cette méthode, car la pile n’est peut-être pas dans un État qui autorise garbage collection, et par conséquent, Preemptive garbage collection ne peut pas être activé. Si le profileur est bloqué ici et que garbage collection est tentée, le runtime se bloque jusqu’à ce que ce rappel soit retourné.  
  
 L’implémentation du profileur de cette méthode ne doit pas appeler dans du code managé ou de quelque manière qu’elle provoque une allocation de mémoire managée.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](icorprofilercallback-interface.md)
