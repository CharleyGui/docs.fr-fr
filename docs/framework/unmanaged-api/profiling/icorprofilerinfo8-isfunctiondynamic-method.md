---
title: ICorProfilerInfo8::IsFunctionDynamic
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.IsFunctionDynamic
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 01aa1df27dccf41060083333588e04bc5ea88520
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855927"
---
# <a name="icorprofilerinfo8isfunctiondynamic-method"></a>ICorProfilerInfo8 :: IsFunctionDynamic, méthode

Détermine si une fonction n’a pas de métadonnées associées.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT IsFunctionDynamic( [in]  FunctionID  functionId,
                           [out] BOOL        *isDynamic);
```

#### <a name="parameters"></a>Paramètres

`functionId` \
dans  `FunctionID` Qui identifie la fonction en question.

`isDynamic` \
à Pointeur vers `BOOL` qui contient une valeur indiquant si la fonction n’a pas de métadonnées.

## <a name="remarks"></a>Notes

Une fonction est considérée comme dynamique si elle n’a pas de métadonnées. Certaines méthodes telles que les stubs IL ou les méthodes LCG n’ont pas de métadonnées associées qui peuvent être récupérées à l’aide des API IMetaDataImport. Ces méthodes peuvent être rencontrées par les profileurs par le biais de pointeurs d’instruction ou en écoutant [ICorProfilerCallback ::D ynamicmethodjitcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).

## <a name="requirements"></a>Configuration requise

**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).

**En-tête :** CorProf. idl, CorProf. h

**Bibliothèque** CorGuids.lib

**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Voir aussi

- [Interface ICorProfilerInfo8](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md)
