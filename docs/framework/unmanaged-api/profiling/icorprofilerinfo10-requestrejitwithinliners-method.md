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
ms.openlocfilehash: 99b6893854c358720259095bf3c0270cb3676483
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452173"
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

  \[dans] masque de [réCOR_PRF_REJIT_FLAGS](cor-prf-rejit-flags-enumeration.md).

- `cFunctions`

  \[in] nombre de fonctions à recompiler.

- `moduleIds`

  \[in] spécifie la partie `moduleId` des paires (`module`, `methodDef`) qui identifient les fonctions à recompiler.

- `methodIds`

  \[in] spécifie la partie `methodId` des paires (`module`, `methodDef`) qui identifient les fonctions à recompiler.

## <a name="remarks"></a>Notes

[Requestrejit,](icorprofilerinfo4-requestrejit-method.md) n’effectue aucun suivi des méthodes Inline. Le profileur devait bloquer l’incorporation ou le suivi des Inlines et appeler `RequestReJIT` pour tous les Inlines afin de s’assurer que chaque instance d’une méthode Inline était ReJITted. Cela pose un problème avec ReJIT lors de l’attachement, car le profileur n’est pas présent pour surveiller l’incorporation. Cette méthode peut être appelée pour garantir que l’ensemble complet des Inlines sera également ReJITted.

## <a name="requirements"></a>Configuration requise

**Plateformes :** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/install/dependencies.md?pivots=os-windows).

**En-tête :** CorProf.idl, CorProf.h

**Bibliothèque :** CorGuids.lib

**Versions de .net :** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>Voir aussi

- [Interface ICorProfilerInfo10](icorprofilerinfo10-interface.md)
