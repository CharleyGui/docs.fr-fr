---
title: ICorDebugEval::CallFunction, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugEval.CallFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::CallFunction
helpviewer_keywords:
- ICorDebugEval::CallFunction method [.NET Framework debugging]
- CallFunction method [.NET Framework debugging]
ms.assetid: 7f470c5c-e1c0-4d8d-aad8-830f113ae751
topic_type:
- apiref
ms.openlocfilehash: 1cf0080945ad78565fae3fedb454ceba7825cb4a
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976237"
---
# <a name="icordebugevalcallfunction-method"></a>ICorDebugEval::CallFunction, méthode

Configure un appel à la fonction spécifiée.

Cette méthode est obsolète dans la version 2,0 de .NET Framework. Utilisez [ICorDebugEval2 :: CallParameterizedFunction,](icordebugeval2-callparameterizedfunction-method.md) à la place.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CallFunction (
    [in] ICorDebugFunction  *pFunction,
    [in] ULONG32            nArgs,
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]
);
```

## <a name="parameters"></a>Paramètres

`pFunction`\
dans Pointeur vers un objet ICorDebugFunction qui spécifie la fonction à appeler.

`nArgs`\
dans Nombre d’arguments pour la fonction.

`ppArgs`\
dans Tableau de pointeurs, chacun pointant vers un objet ICorDebugValue qui spécifie un argument à passer à la fonction.

## <a name="remarks"></a>Notes 

Si la fonction est virtuelle, `CallFunction` effectue une répartition virtuelle. Si la fonction se trouve dans un domaine d’application différent, une transition est effectuée tant que tous les arguments sont également dans ce domaine d’application.

## <a name="requirements"></a>Spécifications

**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).

**En-tête :** CorDebug.idl, CorDebug.h

**Bibliothèque :** CorGuids.lib

**Versions de .NET Framework :** 1,1, 1,0

## <a name="see-also"></a>Voir aussi

- [CallParameterizedFunction, méthode](icordebugeval2-callparameterizedfunction-method.md)
