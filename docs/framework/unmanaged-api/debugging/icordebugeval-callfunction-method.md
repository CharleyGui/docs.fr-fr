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
ms.openlocfilehash: 4ac26ef4449dc02230f26b1247616b4587d217b7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73085160"
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

## <a name="requirements"></a>spécifications

**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).

**En-tête :** CorDebug.idl, CorDebug.h

**Bibliothèque :** CorGuids.lib

**Versions de .NET Framework :** 1,1, 1,0

## <a name="see-also"></a>Voir aussi

- [CallParameterizedFunction, méthode](icordebugeval2-callparameterizedfunction-method.md)
