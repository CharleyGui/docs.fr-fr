---
title: ICorProfilerInfo10::GetLOHObjectSizeThreshold
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.GetLOHObjectSizeThreshold
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 280f0a401f87f81e1ef9d4a2c85c06599442b5ec
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90543944"
---
# <a name="icorprofilerinfo10getlohobjectsizethreshold-method"></a>ICorProfilerInfo10 :: GetLOHObjectSizeThreshold, méthode

Obtient la valeur du seuil LOH (large Object Heap) configurée.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetLOHObjectSizeThreshold( [out] DWORD *pThreshold );
```

## <a name="parameters"></a>Paramètres

- `pThreshold`

  \[out] seuil du tas d’objets volumineux, en octets.

## <a name="remarks"></a>Notes

Les objets plus grands que le seuil du tas d’objets volumineux seront alloués sur le tas des objets volumineux. À compter de .NET Core 3,0 le seuil du tas d’objets volumineux est configurable, `pThreshold` contient la taille du seuil du tas d’objets volumineux actif, en octets.

## <a name="requirements"></a>Spécifications

**Plateformes :** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/install/windows.md?pivots=os-windows).

**En-tête :** CorProf.idl, CorProf.h

**Bibliothèque :** CorGuids.lib

**Versions de .net :**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>Voir aussi

- [Interface ICorProfilerInfo10](icorprofilerinfo10-interface.md)
