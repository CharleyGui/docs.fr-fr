---
title: ICorProfilerInfo2::GetObjectGeneration, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetObjectGeneration
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetObjectGeneration
helpviewer_keywords:
- GetObjectGeneration method [.NET Framework profiling]
- ICorProfilerInfo2::GetObjectGeneration method [.NET Framework profiling]
ms.assetid: b0d25f76-0bd5-4aa6-96cf-bfec0e1de28b
topic_type:
- apiref
ms.openlocfilehash: b75de955e3b6857c9cc1b5411df4b0f262c4cb9a
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862696"
---
# <a name="icorprofilerinfo2getobjectgeneration-method"></a>ICorProfilerInfo2::GetObjectGeneration, méthode
Obtient le segment du tas qui contient l’objet spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetObjectGeneration(  
    [in] ObjectID objectId,  
    [out] COR_PRF_GC_GENERATION_RANGE *range);  
```  
  
## <a name="parameters"></a>Parameters  
 `objectId`  
 dans ID de l’objet.  
  
 `range`  
 à Pointeur vers une structure [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) , qui décrit une plage (autrement dit, un bloc) de mémoire dans la génération en cours d’garbage collection. Cette plage contient l’objet spécifié.  
  
## <a name="remarks"></a>Notes  
 La méthode `GetObjectGeneration` peut être appelée à partir de tout rappel de profileur, à condition que garbage collection ne soit pas en cours. Autrement dit, il peut être appelé à partir de tout rappel, à l’exception de ceux qui se produisent entre [ICorProfilerCallback2 :: GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md) et [ICorProfilerCallback2 :: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md).  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interface](icorprofilerinfo2-interface.md)
