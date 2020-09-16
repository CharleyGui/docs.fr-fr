---
title: ICorProfilerInfo10::RequestReJITWithInliners
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.RequestReJITWithInliners
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: e3d5a09730cb8e477bd506749017a403acff1696
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90540555"
---
# <a name="icorprofilerinfo10requestrejitwithinliners-method"></a>ICorProfilerInfo10 :: RequestReJITWithInliners, méthode

ReJITs les méthodes demandées, ainsi que les Inlines des méthodes demandées.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT RequestReJITWithInliners( [in]                       DWORD       dwRejitFlags,
                                  [in]                       ULONG       cFunctions,
                                  [in, size_is(cFunctions)]  ModuleID    moduleIds[],
                                  [in, size_is(cFunctions)]  mdMethodDef methodIds[]);
```

## <a name="parameters"></a>Paramètres

- `dwRejitFlags`

  \[in] masque de [COR_PRF_REJIT_FLAGS](cor-prf-rejit-flags-enumeration.md).

- `cFunctions`

  \[in] nombre de fonctions à recompiler.

- `moduleIds`

  \[in] spécifie la `moduleId` partie des `module` paires (, `methodDef` ) qui identifient les fonctions à recompiler.

- `methodIds`

  \[in] spécifie la `methodId` partie des `module` paires (, `methodDef` ) qui identifient les fonctions à recompiler.

## <a name="remarks"></a>Notes

[Requestrejit,](icorprofilerinfo4-requestrejit-method.md) n’effectue aucun suivi des méthodes Inline. Le profileur devait bloquer l’incorporation ou suivre l’inline et appeler `RequestReJIT` pour tous les inlineers pour s’assurer que chaque instance d’une méthode Inline était ReJITted. Cela pose un problème avec ReJIT lors de l’attachement, car le profileur n’est pas présent pour surveiller l’incorporation. Cette méthode peut être appelée pour garantir que l’ensemble complet des Inlines sera également ReJITted.

## <a name="requirements"></a>Spécifications

**Plateformes :** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/install/windows.md?pivots=os-windows).

**En-tête :** CorProf.idl, CorProf.h

**Bibliothèque :** CorGuids.lib

**Versions de .net :**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>Voir aussi

- [Interface ICorProfilerInfo10](icorprofilerinfo10-interface.md)
