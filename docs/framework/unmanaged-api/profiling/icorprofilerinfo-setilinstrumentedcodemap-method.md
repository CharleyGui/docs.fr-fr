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
ms.openlocfilehash: 99e473268fd0d5bb8ce120b97576277949b86508
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868995"
---
# <a name="icorprofilerinfosetilinstrumentedcodemap-method"></a>ICorProfilerInfo::SetILInstrumentedCodeMap, méthode

Définit une carte de code pour la fonction spécifiée à l’aide des entrées de mappage MSIL (Microsoft Intermediate Language) spécifiées.

> [!NOTE]
> Dans la version 2,0 de .NET Framework, l’appel de `SetILInstrumentedCodeMap` sur un `FunctionID` qui représente une fonction générique dans un domaine d’application particulier affecte toutes les instances de cette fonction dans le domaine d’application.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetILInstrumentedCodeMap(
    [in]  FunctionID functionId,
    [in]  BOOL       fStartJit,
    [in]  ULONG      cILMapEntries,
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);
```

## <a name="parameters"></a>Parameters

`functionId`\
dans ID de la fonction pour laquelle définir la carte de code.

`fStartJit`\
dans Valeur booléenne qui indique si l’appel à la méthode `SetILInstrumentedCodeMap` est le premier d’une `FunctionID`particulière. Définissez `fStartJit` sur `true` dans le premier appel à `SetILInstrumentedCodeMap` pour un `FunctionID`donné et à `false` par la suite.

`cILMapEntries`\
dans Nombre d’éléments dans le tableau de `cILMapEntries`.

`rgILMapEntries`\
dans Tableau de COR_IL_MAP structures, chacune spécifiant un décalage MSIL.

## <a name="remarks"></a>Notes

Un profileur insère souvent des instructions dans le code source d’une méthode afin d’instrumenter cette méthode (par exemple, pour notifier quand une ligne source donnée est atteinte). `SetILInstrumentedCodeMap` permet à un profileur de mapper les instructions MSIL d’origine à leurs nouveaux emplacements. Un profileur peut utiliser la méthode [ICorProfilerInfo :: GetILToNativeMapping](icorprofilerinfo-getiltonativemapping-method.md) pour obtenir l’offset MSIL d’origine pour un offset natif donné.

Le débogueur suppose que chaque ancien offset fait référence à un offset MSIL dans le code MSIL non modifié d’origine, et que chaque nouvel offset fait référence à l’offset MSIL dans le nouveau code instrumenté. Le mappage doit être trié par ordre de tri. Pour que l’exécution pas à pas fonctionne correctement, suivez les instructions suivantes :

- Ne réorganisez pas le code MSIL instrumenté.

- Ne supprimez pas le code MSIL d’origine.

- Incluez les entrées de tous les points de séquence du fichier de base de données du programme (PDB) dans le mappage. Le mappage n’interpole pas les entrées manquantes. Par conséquent, à partir de la carte suivante :

  (0 ancien, 0 nouveau)

  (5 anciennes, 10 nouvelles)

  (9 vieux, 20 nouveaux)

  - Un ancien décalage de 0, 1, 2, 3 ou 4 sera mappé au nouveau décalage 0.

  - Un ancien décalage de 5, 6, 7 ou 8 sera mappé au nouveau décalage 10.

  - Un ancien décalage de 9 ou plus sera mappé au nouveau décalage 20.

  - Un nouveau décalage de 0, 1, 2, 3, 4, 5, 6, 7, 8 ou 9 sera mappé à l’ancien décalage 0.

  - Un nouveau décalage de 10, 11, 12, 13, 14, 15, 16, 17, 18 ou 19 sera mappé à l’ancien décalage 5.

  - Un nouveau décalage de 20 ou plus sera mappé à l’ancien décalage 9.

Dans le .NET Framework 3,5 et les versions antérieures, vous allouez le tableau `rgILMapEntries` en appelant la méthode [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) . Étant donné que le runtime prend possession de cette mémoire, le profileur ne doit pas tenter de le libérer.

## <a name="requirements"></a>Configuration requise pour

**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).

**En-tête :** CorProf.idl, CorProf.h

**Bibliothèque :** CorGuids.lib

**Versions du .NET Framework :** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]

## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](icorprofilerinfo-interface.md)
