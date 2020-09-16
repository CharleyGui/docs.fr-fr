---
title: ICorProfilerInfo9::GetILToNativeMapping3
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetILToNativeMapping3
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 14391a0fe046b44aedca1da2bc42c7d962e1a5e7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90541276"
---
# <a name="icorprofilerinfo9getiltonativemapping3-method"></a>ICorProfilerInfo9 :: GetILToNativeMapping3, méthode

À partir de l’adresse de début du code natif, retourne les informations de mappage natives à IL pour cette version JIT du code.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetILToNativeMapping3( [in]  UINT_PTR pNativeCodeStartAddress,
                               [in]  ULONG32 cMap,
                               [out] ULONG32 *pcMap,
                               [out] COR_DEBUG_IL_TO_NATIVE_MAP map[]);
```

## <a name="parameters"></a>Paramètres

- `pNativeCodeStartAddress`

  \[in] pointeur vers le début d’une fonction native.

- `cMap`

  \[in] taille maximale du `map` tableau.

- `pcMap`

  \[out] nombre total de structures de COR_DEBUG_IL_TO_NATIVE_MAP disponibles.

- `map`

  \[out] tableau de structures [COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md) , chacune spécifiant les décalages. Suite au retour de la méthode `GetILToNativeMapping3`, `map` contient une partie ou la totalité des structures `COR_DEBUG_IL_TO_NATIVE_MAP`.

## <a name="remarks"></a>Notes

Lorsque la compilation à plusieurs niveaux est activée, une méthode peut avoir plusieurs corps de code natif. [ICorProfilerInfo9 :: GetNativeCodeStartAddresses](icorprofilerinfo9-getnativecodestartaddresses-method.md) retourne les adresses de démarrage de tous les corps de code natif.

## <a name="requirements"></a>Spécifications

**Plateformes :** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/install/windows.md?pivots=os-windows).

**En-tête :** CorProf.idl, CorProf.h

**Bibliothèque :** CorGuids.lib

**Versions de .NET Framework :**[!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]

## <a name="see-also"></a>Voir aussi

- [Interface ICorProfilerInfo9](icorprofilerinfo9-interface.md)
