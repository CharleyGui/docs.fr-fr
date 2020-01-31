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
ms.openlocfilehash: 5822136eb1a7f582bcfae901a99775950e586198
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863177"
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

## <a name="parameters"></a>Parameters

- `dwRejitFlags`

  \[dans] masque de [réCOR_PRF_REJIT_FLAGS](cor-prf-rejit-flags-enumeration.md).

- `cFunctions`

  \[in] nombre de fonctions à recompiler.

- `moduleIds`

  \[in] spécifie la partie `moduleId` des paires (`module`, `methodDef`) qui identifient les fonctions à recompiler.

- `methodIds`

  \[in] spécifie la partie `methodId` des paires (`module`, `methodDef`) qui identifient les fonctions à recompiler.

## <a name="remarks"></a>Notes

[Requestrejit,](icorprofilerinfo4-requestrejit-method.md) n’effectue aucun suivi des méthodes Inline. Le profileur devait bloquer l’incorporation ou le suivi des Inlines et appeler `RequestReJIT` pour tous les Inlines afin de s’assurer que chaque instance d’une méthode Inline était ReJITted. Cela pose un problème avec ReJIT lors de l’attachement, car le profileur n’est pas présent pour surveiller l’incorporation. Cette méthode peut être appelée pour garantir que l’ensemble complet des Inlines sera également ReJITted.

## <a name="requirements"></a>Configuration requise pour

**Plateformes :** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).

**En-tête :** CorProf.idl, CorProf.h

**Bibliothèque :** CorGuids.lib

**Versions de .net :** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>Voir aussi

- [Interface ICorProfilerInfo10](icorprofilerinfo10-interface.md)
