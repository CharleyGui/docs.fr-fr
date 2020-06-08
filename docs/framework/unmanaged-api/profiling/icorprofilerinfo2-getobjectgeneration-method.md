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
ms.openlocfilehash: 1263202c1fe524c924a88b9356e5ab9116cea553
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502858"
---
# <a name="icorprofilerinfo2getobjectgeneration-method"></a>ICorProfilerInfo2::GetObjectGeneration, méthode
Obtient le segment du tas qui contient l’objet spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetObjectGeneration(  
    [in] ObjectID objectId,  
    [out] COR_PRF_GC_GENERATION_RANGE *range);  
```  
  
## <a name="parameters"></a>Paramètres  
 `objectId`  
 dans ID de l’objet.  
  
 `range`  
 à Pointeur vers une structure [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) , qui décrit une plage (autrement dit, un bloc) de mémoire dans la génération en cours d’garbage collection. Cette plage contient l’objet spécifié.  
  
## <a name="remarks"></a>Remarques  
 La `GetObjectGeneration` méthode peut être appelée à partir de tout rappel de profileur, à condition que garbage collection ne soit pas en cours. Autrement dit, il peut être appelé à partir de tout rappel, à l’exception de ceux qui se produisent entre [ICorProfilerCallback2 :: GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md) et [ICorProfilerCallback2 :: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md).  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interface](icorprofilerinfo2-interface.md)
