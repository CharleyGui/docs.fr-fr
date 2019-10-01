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
ms.openlocfilehash: 1bdaf6391ca5c19f073708d6258ad5775bec9824
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700729"
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

## <a name="requirements"></a>Configuration requise

 **Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).

 **En-tête :** CorDebug. idl, CorDebug. h

 **Bibliothèque** CorGuids.lib

 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
 
