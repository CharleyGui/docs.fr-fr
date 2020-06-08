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
ms.openlocfilehash: c88279d361ea78a2e910c4621e92c500902d9124
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495123"
---
# <a name="icorprofilerinfo8isfunctiondynamic-method"></a>ICorProfilerInfo8 :: IsFunctionDynamic, méthode

Détermine si une fonction n’a pas de métadonnées associées.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT IsFunctionDynamic( [in]  FunctionID  functionId,
                           [out] BOOL        *isDynamic);
```

## <a name="parameters"></a>Paramètres

- `functionId`

  \[in] `FunctionID` qui identifie la fonction en question.

- `isDynamic`

  \[out] pointeur vers un `BOOL` qui contient une valeur indiquant si la fonction n’a pas de métadonnées.

## <a name="remarks"></a>Remarques

Une fonction est considérée comme dynamique si elle n’a pas de métadonnées. Certaines méthodes telles que les stubs IL ou les méthodes LCG n’ont pas de métadonnées associées qui peuvent être récupérées à l’aide des API IMetaDataImport. Ces méthodes peuvent être rencontrées par les profileurs par le biais de pointeurs d’instruction ou en écoutant [ICorProfilerCallback ::D ynamicmethodjitcompilationstarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).

## <a name="requirements"></a>Configuration requise

**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).

**En-tête :** CorProf.idl, CorProf.h

**Bibliothèque :** CorGuids.lib

**Versions de .NET Framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Voir aussi

- [Interface ICorProfilerInfo8](icorprofilerinfo8-interface.md)
