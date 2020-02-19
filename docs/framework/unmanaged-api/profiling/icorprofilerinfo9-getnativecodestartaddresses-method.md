---
title: ICorProfilerInfo9::GetNativeCodeStartAddresses
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetNativeCodeStartAddresses
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 99706fdc3d60a5e1a7f85400c1184d5acc808e42
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449725"
---
# <a name="icorprofilerinfo9getnativecodestartaddresses-method"></a>ICorProfilerInfo9 :: GetNativeCodeStartAddresses, méthode

Étant donné une functionId et rejitId, énumère l’adresse de début du code natif de toutes les versions JIT de ce code qui existent actuellement.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetNativeCodeStartAddresses( [in]  FunctionID functionID,
                                     [in]  ReJITID reJitId,
                                     [in]  ULONG32 cCodeStartAddresses,
                                     [out] ULONG32 *pcCodeStartAddresses,
                                     [out] UINT_PTR codeStartAddresses[]);
```

## <a name="parameters"></a>Paramètres

- `functionId`

  \[in] ID de la fonction dont les adresses de début de code natif doivent être retournées.

- `reJitId`

  \[dans] identité de la fonction recompilée juste-à-temps.

- `cCodeStartAddresses`

  \[dans] taille maximale du tableau de `codeStartAddresses`.

- `pcCodeStartAddresses`

  \[out] nombre d’adresses disponibles.

- `codeStartAddresses`

  \[out] tableau de `UINT_PTR`, chacun d’entre eux étant l’adresse de début d’un corps natif pour la fonction spécifiée.

## <a name="remarks"></a>Notes

Lorsque la compilation à plusieurs niveaux est activée, une fonction peut avoir plusieurs corps de code natif.

## <a name="requirements"></a>Spécifications

**Plateformes :** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/install/dependencies.md?pivots=os-windows).

**En-tête :** CorProf.idl, CorProf.h

**Bibliothèque :** CorGuids.lib

**Versions de .net :** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]

## <a name="see-also"></a>Voir aussi

- [Interface ICorProfilerInfo9](icorprofilerinfo9-interface.md)
