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
ms.openlocfilehash: 7593e8873c2714df85146903c0052a9909a95ccd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444715"
---
# <a name="icorprofilerinfo9getnativecodestartaddresses-method"></a>ICorProfilerInfo9::GetNativeCodeStartAddresses Method

Given a functionId and rejitId, enumerates the native code start address of all jitted versions of this code that currently exist.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetNativeCodeStartAddresses( [in]  FunctionID functionID,
                                     [in]  ReJITID reJitId,
                                     [in]  ULONG32 cCodeStartAddresses,
                                     [out] ULONG32 *pcCodeStartAddresses,
                                     [out] UINT_PTR codeStartAddresses[]);
```

#### <a name="parameters"></a>Paramètres

`functionId` \
[in] The ID of the function whose native code start addresses should be returned.

`reJitId` \
[in] Identité de la fonction recompilée juste-à-temps.

`cCodeStartAddresses` \
[in] Taille maximale du tableau `codeStartAddresses`.

`pcCodeStartAddresses` \
[out] The number of available addresses.

`codeStartAddresses` \
[out] An array of `UINT_PTR`, each one of which is the start address for a native body for the specified function.

## <a name="remarks"></a>Notes

When tiered compilation is enabled, a function may have more than one native code body.

## <a name="requirements"></a>spécifications

**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).

**En-tête :** CorProf.idl, CorProf.h

**Bibliothèque :** CorGuids.lib

**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]

## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo9 Interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md)
