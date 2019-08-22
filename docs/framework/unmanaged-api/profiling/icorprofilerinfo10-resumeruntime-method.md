---
title: ICorProfilerInfo10::ResumeRuntime
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.ResumeRuntime
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: cf599e5ded73b09d54c98dcd99f51b30c6a4ba82
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69661202"
---
# <a name="icorprofilerinfo10resumeruntime-method"></a>ICorProfilerInfo10:: ResumeRuntime, méthode

Reprend le runtime sans exécuter de GC.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT ResumeRuntime();
```

## <a name="requirements"></a>Configuration requise

**Plateformes** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).

**En-tête :** CorProf. idl, CorProf. h

**Bibliothèque** CorGuids.lib

**Versions de .net:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>Voir aussi

- [Interface ICorProfilerInfo10](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
