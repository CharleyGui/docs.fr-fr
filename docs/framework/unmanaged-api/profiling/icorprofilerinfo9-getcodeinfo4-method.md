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
ms.openlocfilehash: 3e3e3afc221d153ff3573126ff10014d39af761a
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868302"
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

## <a name="parameters"></a>Parameters

- `pNativeCodeStartAddress`

  \[dans] pointeur vers le début d’une fonction native.

- `cCodeInfos`

  \[dans] taille du tableau de `codeInfos`.

- `pcCodeInfos`

  \[out] pointeur vers le nombre total de structures [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) disponibles.

- `codeInfos`

  \[out] une mémoire tampon fournie par l’appelant. Suite au retour de la méthode, celle-ci contient un tableau de structures `COR_PRF_CODE_INFO` qui décrivent chacune un bloc de code natif.

## <a name="remarks"></a>Notes

La méthode `GetCodeInfo4` est semblable à [getcodeinfo3,](icorprofilerinfo4-getcodeinfo3-method.md), à ceci près qu’elle peut rechercher des informations de code pour différentes versions natives d’une méthode.

> [!NOTE]
> `GetCodeInfo4` pouvez déclencher une garbage collection.

Les étendues sont triées par ordre croissant des offsets du langage CIL (Common Intermediate Language).

Une fois que `GetCodeInfo4` a retourné, vous devez vérifier que la mémoire tampon de `codeInfos` est suffisamment grande pour contenir toutes les structures de [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) . Pour ce faire, comparez la valeur de `cCodeInfos` à celle du paramètre `cchName`. Si `cCodeInfos` divisée par la taille d’une structure [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) est plus petite que `pcCodeInfos`, allouez une plus grande mémoire tampon d' `codeInfos`, mettez à jour `cCodeInfos` avec la nouvelle taille plus grande, puis appelez à nouveau `GetCodeInfo4`.

Vous pouvez également commencer par appeler `GetCodeInfo4` avec un tampon `codeInfos` de longueur nulle pour obtenir la taille correcte du tampon. Vous pouvez ensuite affecter à la `codeInfos` taille de la mémoire tampon la valeur retournée dans `pcCodeInfos`, multipliée par la taille d’une structure [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md), puis rappeler `GetCodeInfo4`.

## <a name="requirements"></a>Configuration requise pour

**Plateformes :** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).

**En-tête :** CorProf.idl, CorProf.h

**Bibliothèque :** CorGuids.lib

**Versions de .net :** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]

## <a name="see-also"></a>Voir aussi

- [Interface ICorProfilerInfo9](ICorProfilerInfo9-interface.md)
