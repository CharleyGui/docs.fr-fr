---
title: ICorProfilerInfo8::GetFunctionFromIP3
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.GetFunctionFromIP3
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 7b0d8033a5ea3b98623b9be384788ef7fc15bf04
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69665637"
---
# <a name="icorprofilerinfo8getfunctionfromip3-method"></a>ICorProfilerInfo8:: GetFunctionFromIP3, méthode

Mappe un pointeur d’instruction de code managé à une FunctionID. Cette méthode fonctionne pour les méthodes dynamiques et non dynamiques.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetFunctionFromIP3([in] LPCBYTE ip,
                           [out] FunctionID *functionId,
                           [out] ReJITID * pReJitId);
```

#### <a name="parameters"></a>Paramètres

`ip` \
dans Pointeur d’instruction dans du code managé.

`pFunctionId` \
à ID de la fonction.

`pReJitId` \
à Identité de la version recompilée juste-à-temps de la fonction.

## <a name="remarks"></a>Notes

Cette méthode fonctionne pour les méthodes dynamiques et non dynamiques. Il s’agit d’un sur-ensemble de [getfunctionfromip2,](icorprofilerinfo4-getfunctionfromip2-method.md), qui fonctionne uniquement pour les fonctions avec métadonnées.

## <a name="requirements"></a>Configuration requise

**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).

**En-tête :** CorProf. idl, CorProf. h

**Bibliothèque** CorGuids.lib

**Versions de .NET Framework:** [! INCLURE[net_current_v472plus](../../../../includes/net-current-v472plus.md)

## <a name="see-also"></a>Voir aussi

- [Interface ICorProfilerInfo8](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md)
