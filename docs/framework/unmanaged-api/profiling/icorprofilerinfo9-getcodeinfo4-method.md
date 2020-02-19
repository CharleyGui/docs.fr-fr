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
ms.openlocfilehash: f65cebff912adeb7afc34434467cf7be72f9be32
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449762"
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

Vous pouvez également commencer par appeler `GetCodeInfo4` avec un tampon `codeInfos` de longueur nulle pour obtenir la taille correcte du tampon. Vous pouvez ensuite définir la taille de la mémoire tampon `codeInfos` sur la valeur retournée dans `pcCodeInfos`, multipliée par la taille d’une structure [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) , et appeler de nouveau `GetCodeInfo4`.

## <a name="requirements"></a>Spécifications

**Plateformes :** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/install/dependencies.md?pivots=os-windows).

**En-tête :** CorProf.idl, CorProf.h

**Bibliothèque :** CorGuids.lib

**Versions de .net :** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]

## <a name="see-also"></a>Voir aussi

- [Interface ICorProfilerInfo9](ICorProfilerInfo9-interface.md)
