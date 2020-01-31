---
title: 'ICorDebugVariableHome :: GetArgumentIndex, méthode'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetArgumentIndex
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetArgumentIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetArgumentIndex method [.NET Framework debugging]
- GetArgumentIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: e86fcc72-388d-4009-ab21-8f9c3323e9a3
topic_type:
- apiref
ms.openlocfilehash: 12d4e63480f03bfad613f30362ddaeaf12b57a88
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791048"
---
# <a name="icordebugvariablehomegetargumentindex-method"></a>ICorDebugVariableHome :: GetArgumentIndex, méthode

Obtient l’index d’un argument de fonction.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetArgumentIndex(
    [out] ULONG32* pArgumentIndex
);
```

## <a name="parameters"></a>Parameters

`pArgumentIndex`\
à Pointeur vers l’index de l’argument.

## <a name="return-value"></a>Valeur de retour

La méthode retourne les valeurs suivantes.

|Value|Description|
|-----------|-----------------|
|`S_OK`|L’appel de méthode a retourné un index d’argument valide.|
|`E_FAIL`|L’instance [ICorDebugVariableHome](icordebugvariablehome-interface.md) actuelle représente une variable locale.|

## <a name="remarks"></a>Notes

L’index de l’argument peut être utilisé pour récupérer les métadonnées de cet argument.

## <a name="requirements"></a>Configuration requise pour

**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).

**En-tête :** CorDebug.idl, CorDebug.h

**Bibliothèque :** CorGuids.lib

**Versions du .NET Framework :** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]

## <a name="see-also"></a>Voir aussi

- [ICorDebugVariableHome, interface](icordebugvariablehome-interface.md)
