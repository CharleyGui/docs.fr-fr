---
title: ICorProfilerCallback::ObjectAllocated, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectAllocated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectAllocated
helpviewer_keywords:
- ObjectAllocated method [.NET Framework profiling]
- ICorProfilerCallback::ObjectAllocated method [.NET Framework profiling]
ms.assetid: eb412622-77cc-4abd-a2cd-c910fe8edd54
topic_type:
- apiref
ms.openlocfilehash: fda234a6a280aeea1f497ad195d6d41efb6aa951
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674323"
---
# <a name="icorprofilercallbackobjectallocated-method"></a>ICorProfilerCallback::ObjectAllocated, méthode

Indique au profileur que la mémoire dans le tas a été allouée pour un objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ObjectAllocated(  
    [in] ObjectID objectId,  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a>Paramètres  

 `objectId`  
 dans ID de l’objet pour lequel la mémoire a été allouée.  
  
 `classId`  
 dans ID de la classe dont l’objet est une instance.  
  
## <a name="remarks"></a>Remarques  

 La `ObjectedAllocated` méthode n’est pas appelée pour les allocations à partir de la pile ou de la mémoire non managée. Le `classId` paramètre peut faire référence à une classe dans du code managé qui n’a pas encore été chargée. Le profileur reçoit un rappel de charge de classe pour cette classe immédiatement après le `ObjectAllocated` rappel.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](icorprofilercallback-interface.md)
- [ClassLoadStarted, méthode](icorprofilercallback-classloadstarted-method.md)
- [ClassLoadFinished, méthode](icorprofilercallback-classloadfinished-method.md)
