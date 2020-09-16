---
title: ICorProfilerInfo9::GetCodeInfo4
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetCodeInfo4
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: ecaff179378eb417393c0a0d17d0a00d3b99e5a4
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90541296"
---
# <a name="icorprofilerinfo9getcodeinfo4-method"></a>ICorProfilerInfo9 :: GetCodeInfo4, méthode

À partir de l’adresse de début du code natif, retourne les blocs de mémoire virtuelle qui stockent ce code.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetCodeInfo4( [in]  UINT_PTR pNativeCodeStartAddress,
                      [in]  ULONG32 cCodeInfos,
                      [out] ULONG32* pcCodeInfos,
                      [out] COR_PRF_CODE_INFO codeInfos[]);
```

## <a name="parameters"></a>Paramètres

- `pNativeCodeStartAddress`

  \[in] pointeur vers le début d’une fonction native.

- `cCodeInfos`

  \[in] taille du `codeInfos` tableau.

- `pcCodeInfos`

  \[out] pointeur vers le nombre total de structures de [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) disponibles.

- `codeInfos`

  \[out] mémoire tampon fournie par l’appelant. Suite au retour de la méthode, celle-ci contient un tableau de structures `COR_PRF_CODE_INFO` qui décrivent chacune un bloc de code natif.

## <a name="remarks"></a>Notes

La `GetCodeInfo4` méthode est semblable à [getcodeinfo3,](icorprofilerinfo4-getcodeinfo3-method.md), à ceci près qu’elle peut rechercher des informations de code pour différentes versions natives d’une méthode.

> [!NOTE]
> `GetCodeInfo4` peut déclencher un garbage collection.

Les étendues sont triées par ordre croissant des offsets du langage CIL (Common Intermediate Language).

Après le `GetCodeInfo4` retour de, vous devez vérifier que la `codeInfos` mémoire tampon est suffisamment grande pour contenir toutes les structures de [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) . Pour ce faire, comparez la valeur de `cCodeInfos` à celle du paramètre `cchName`. Si `cCodeInfos` divisée par la taille d’une structure [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) est plus petite que `pcCodeInfos` , allouez une `codeInfos` mémoire tampon plus grande, mettez à jour `cCodeInfos` avec la nouvelle taille plus grande, puis rappelez `GetCodeInfo4` .

Vous pouvez également commencer par appeler `GetCodeInfo4` avec un tampon `codeInfos` de longueur nulle pour obtenir la taille correcte du tampon. Vous pouvez ensuite affecter `codeInfos` à la taille de la mémoire tampon la valeur retournée dans `pcCodeInfos` , multipliée par la taille d’une [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structure, puis rappeler `GetCodeInfo4` .

## <a name="requirements"></a>Spécifications

**Plateformes :** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/install/windows.md?pivots=os-windows).

**En-tête :** CorProf.idl, CorProf.h

**Bibliothèque :** CorGuids.lib

**Versions de .net :**[!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]

## <a name="see-also"></a>Voir aussi

- [Interface ICorProfilerInfo9](ICorProfilerInfo9-interface.md)
