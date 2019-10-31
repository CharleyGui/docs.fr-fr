---
title: ICorDebugModule2::ResolveAssembly, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.ResolveAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::ResolveAssembly
helpviewer_keywords:
- ICorDebugModule2::ResolveAssembly method [.NET Framework debugging]
- ResolveAssembly method [.NET Framework debugging]
ms.assetid: ddf9085c-7161-44bd-9609-cd2732b9009f
topic_type:
- apiref
ms.openlocfilehash: 0809a149a5a5a5e9adea059140d7b4b456337ef3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125301"
---
# <a name="icordebugmodule2resolveassembly-method"></a>ICorDebugModule2::ResolveAssembly, méthode

Résout l’assembly référencé par le jeton de métadonnées spécifié.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT ResolveAssembly (
    [in]  mdToken             tkAssemblyRef,
    [out] ICorDebugAssembly   **ppAssembly
);
```

## <a name="parameters"></a>Paramètres

`tkAssemblyRef`\
dans Valeur `mdToken` qui référence l’assembly.

`ppAssembly`\
à Pointeur vers l’adresse d’un objet ICorDebugAssembly qui représente l’assembly.

## <a name="remarks"></a>Notes

Si l’assembly n’est pas déjà chargé lors de l’appel de `ResolveAssembly`, une valeur HRESULT de CORDBG_E_CANNOT_RESOLVE_ASSEMBLY est retournée.

## <a name="requirements"></a>spécifications

**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).

**En-tête :** CorDebug.idl, CorDebug.h

**Bibliothèque :** CorGuids.lib

**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
