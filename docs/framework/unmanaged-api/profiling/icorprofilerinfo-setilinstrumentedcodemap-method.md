---
title: ICorProfilerInfo::SetILInstrumentedCodeMap, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetILInstrumentedCodeMap
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap
helpviewer_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap method [.NET Framework profiling]
- SetILInstrumentedCodeMap method [.NET Framework profiling]
ms.assetid: bce1dcf8-b4ec-4e73-a917-f2df1ad49c8a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e41df91ceb9e4b776c2aa1ce864b7e09ec485fd5
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661952"
---
# <a name="icorprofilerinfosetilinstrumentedcodemap-method"></a>ICorProfilerInfo::SetILInstrumentedCodeMap, méthode

Définit une carte de code pour la fonction spécifiée à l’aide d’entrées de mappage Microsoft intermediate language (MSIL) spécifiées.

> [!NOTE]
> Dans le .NET Framework version 2.0, l’appel `SetILInstrumentedCodeMap` sur un `FunctionID` que représente une fonction générique dans un domaine d’application affecte toutes les instances de cette fonction dans le domaine d’application.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetILInstrumentedCodeMap(
    [in]  FunctionID functionId,
    [in]  BOOL       fStartJit,
    [in]  ULONG      cILMapEntries,
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);
```

## <a name="parameters"></a>Paramètres

`functionId`\
[in] L’ID de la fonction pour laquelle définir la carte de code.

`fStartJit`\
[in] Valeur booléenne qui indique si l’appel à la `SetILInstrumentedCodeMap` méthode est le premier pour un particulier `FunctionID`. Définissez `fStartJit` à `true` dans le premier appel à `SetILInstrumentedCodeMap` pour une donnée `FunctionID`et `false` par la suite.

`cILMapEntries`\
[in] Le nombre d’éléments dans le `cILMapEntries` tableau.

`rgILMapEntries`\
[in] Tableau de structures COR_IL_MAP, dont chacun spécifie un offset MSIL.

## <a name="remarks"></a>Notes

Un profileur insère souvent des instructions dans le code source d’une méthode pour instrumenter cette méthode (par exemple, pour avertir lorsqu’une ligne source donnée est atteinte). `SetILInstrumentedCodeMap` permet à un profileur mapper les instructions MSIL d’origine à leurs nouveaux emplacements. Un profileur peut utiliser le [ICorProfilerInfo::GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) méthode pour obtenir l’offset MSIL d’origine pour un offset natif donné.

Le débogueur suppose que chaque ancien offset fait référence à un offset MSIL dans le code MSIL non modifié d’origine, et que chaque nouveau décalage fait référence à l’offset MSIL dans le nouveau code instrumenté. Le mappage doit être trié par ordre croissant. Pour le pas à pas fonctionne correctement, suivez ces instructions :

- Ne réorganisez pas le code MSIL instrumenté.

- Ne supprimez pas le code MSIL d’origine.

- Inclure des entrées pour tous les points de séquence à partir du fichier de base de données (PDB) du programme dans le mappage. Le mappage n’interpole pas les entrées manquantes. Ainsi, étant donné le plan suivant :

  (0 ancien, 0 nouveau)

  (5 anciens, 10 nouveaux)

  (9 ancien, 20 nouveaux)

  - Un ancien offset de 0, 1, 2, 3 ou 4 sera mappé à nouveau décalage 0.

  - Un ancien offset de 5, 6, 7 ou 8 sera mappé à nouveau décalage de 10.

  - Un ancien offset de 9 ou version ultérieure sera mappé à nouveau décalage de 20.

  - Un nouveau décalage de 0, 1, 2, 3, 4, 5, 6, 7, 8 ou 9 sera mappé à l’ancien offset 0.

  - Un nouveau décalage de 10, 11, 12, 13, 14, 15, 16, 17, 18 ou 19 sera mappé à l’ancien offset 5.

  - Un nouveau décalage supérieur ou égal à 20 sera mappé à l’ancien offset 9.

## <a name="requirements"></a>Configuration requise

**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).

**En-tête :** CorProf.idl, CorProf.h

**Bibliothèque :** CorGuids.lib

**Versions du .NET Framework :** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]

## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
