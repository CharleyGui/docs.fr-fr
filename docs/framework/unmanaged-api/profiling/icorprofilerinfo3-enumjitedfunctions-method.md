---
title: ICorProfilerInfo3::EnumJITedFunctions, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.EnumJITedFunctions Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::EnumJITedFunctions
helpviewer_keywords:
- ICorProfilerInfo3::EnumJITedFunctions method [.NET Framework profiling]
- EnumJITedFunctions method [.NET Framework profiling]
ms.assetid: e2847a36-f460-45e2-9b6c-b33b008f40d9
topic_type:
- apiref
ms.openlocfilehash: a22a0de9a20f32ce1c9818bbcf29222a4b331420
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862423"
---
# <a name="icorprofilerinfo3enumjitedfunctions-method"></a>ICorProfilerInfo3::EnumJITedFunctions, méthode
Retourne un énumérateur pour toutes les fonctions qui ont été précédemment compilées juste-à-temps.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a>Parameters  
 `ppEnum`  
 à Pointeur vers l’énumérateur [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) .  
  
## <a name="remarks"></a>Notes  
 Cette méthode peut se chevaucher avec des rappels `JITCompilation` tels que la méthode [ICorProfilerCallback :: JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) . L’énumérateur retourné par cette méthode n’inclut pas les fonctions qui sont chargées à partir d’images natives générées avec Ngen. exe.  
  
> [!NOTE]
> L’énumération retournée comprend uniquement « 0 » pour la valeur du champ `COR_PRF_FUNCTION::reJitId`.  Si vous avez besoin de valeurs `COR_PRF_FUNCTION::reJitId` valides, utilisez la méthode [ICorProfilerInfo4 :: enumjitedfunctions2,](icorprofilerinfo4-enumjitedfunctions2-method.md) .  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo3, interface](icorprofilerinfo3-interface.md)
- [Interfaces de profilage](profiling-interfaces.md)
- [Profilage](index.md)
