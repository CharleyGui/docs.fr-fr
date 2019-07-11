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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 10a000fd98ad12dc39f8f8338485d6bb4093ee07
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782981"
---
# <a name="icorprofilercallbackobjectallocated-method"></a>ICorProfilerCallback::ObjectAllocated, méthode
Notifie le profileur de mémoire dans le tas a été allouée pour un objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ObjectAllocated(  
    [in] ObjectID objectId,  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a>Paramètres  
 `objectId`  
 [in] L’ID de l’objet pour lequel la mémoire a été allouée.  
  
 `classId`  
 [in] L’ID de la classe dont l’objet est une instance.  
  
## <a name="remarks"></a>Notes  
 Le `ObjectedAllocated` méthode n’est pas appelée pour les allocations de la pile ou de mémoire non managée. Le `classId` paramètre peut faire référence à une classe dans le code managé qui n’a pas encore été chargée. Le profileur reçoit un rappel de chargement de classe pour cette classe immédiatement après le `ObjectAllocated` rappel.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ClassLoadStarted, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)
- [ClassLoadFinished, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)
