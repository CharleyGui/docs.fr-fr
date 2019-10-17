---
title: ICorDebugCode2::GetCodeChunks, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugCode2.GetCodeChunks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2::GetCodeChunks
helpviewer_keywords:
- GetCodeChunks method [.NET Framework debugging]
- ICorDebugCode2::GetCodeChunks method [.NET Framework debugging]
ms.assetid: 210a2f02-2678-4555-bc4a-78a0408764c8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d64773aa0d35f2e97232576d145dfcba624812ec
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395526"
---
# <a name="icordebugcode2getcodechunks-method"></a>ICorDebugCode2::GetCodeChunks, méthode

Obtient les blocs de code composés de cet objet de code.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetCodeChunks (
    [in]  ULONG32     cbufSize,
    [out] ULONG32     *pcnumChunks,
    [out, size_is(cbufSize), length_is(*pcnumChunks)]
        CodeChunkInfo chunks[]
);
```

## <a name="parameters"></a>Paramètres

`cbufSize`  
dans Taille du tableau `chunks`.

`pcnumChunks`  
à Nombre de segments retournés dans le tableau `chunks`.

`chunks`  
à Tableau de structures « CodeChunkInfo », chacune représentant un segment de code unique. Si la valeur de `cbufSize` est égale à 0, ce paramètre peut avoir la valeur null.

## <a name="remarks"></a>Notes

Les segments de code ne se chevauchent jamais et suivent l’ordre dans lequel ils ont été concaténés par [ICorDebugCode :: GetCode](icordebugcode-getcode-method.md). Un objet de code MSIL (Microsoft Intermediate Language) dans le .NET Framework version 2,0 comprendra un seul segment de code.

## <a name="requirements"></a>spécifications

**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).

**En-tête :** CorDebug.idl, CorDebug.h

**Bibliothèque :** CorGuids.lib

**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
