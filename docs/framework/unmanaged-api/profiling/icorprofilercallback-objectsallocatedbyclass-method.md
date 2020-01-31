---
title: ICorProfilerCallback::ObjectsAllocatedByClass, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectsAllocatedByClass
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectsAllocatedByClass
helpviewer_keywords:
- ObjectsAllocatedByClass method [.NET Framework profiling]
- ICorProfilerCallback::ObjectsAllocatedByClass method [.NET Framework profiling]
ms.assetid: 91d688f3-a80e-419d-9755-ff94bc04188a
topic_type:
- apiref
ms.openlocfilehash: 028207486f43e35086ed2e515eb3ae6bca304491
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866071"
---
# <a name="icorprofilercallbackobjectsallocatedbyclass-method"></a>ICorProfilerCallback::ObjectsAllocatedByClass, méthode
Notifie le profileur du nombre d’instances de chaque classe spécifiée qui ont été créées depuis la garbage collection la plus récente.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ObjectsAllocatedByClass(  
    [in] ULONG   cClassCount,  
    [in, size_is(cClassCount)] ClassID classIds[] ,  
    [in, size_is(cClassCount)] ULONG   cObjects[] );  
```  
  
## <a name="parameters"></a>Parameters  
 `cClassCount`  
 dans Taille des tableaux `classIds` et `cObjects`.  
  
 `classIds`  
 dans Tableau d’ID de classe, où chaque ID spécifie une classe avec une ou plusieurs instances.  
  
 `cObjects`  
 dans Tableau d’entiers, où chaque entier spécifie le nombre d’instances pour la classe correspondante dans le tableau de `classIds`.  
  
## <a name="remarks"></a>Notes  
 Les tableaux `classIds` et `cObjects` sont des tableaux parallèles. Par exemple, `classIds[i]` et `cObjects[i]` référencent la même classe. Si aucune instance d’une classe n’a été créée depuis la garbage collection précédente, la classe est omise. Le rappel `ObjectsAllocatedByClass` ne signale pas les objets alloués dans le tas d’objets volumineux.  
  
 Les nombres signalés par `ObjectsAllocatedByClass` sont uniquement des estimations. Pour obtenir des nombres exacts, utilisez [ICorProfilerCallback :: ObjectAllocated](icorprofilercallback-objectallocated-method.md).  
  
 Le tableau `classIds` peut contenir une ou plusieurs entrées NULL si le tableau de `cObjects` correspondant a des types qui déchargent.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](icorprofilercallback-interface.md)
