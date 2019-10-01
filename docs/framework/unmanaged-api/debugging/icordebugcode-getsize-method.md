---
title: ICorDebugCode::GetSize, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetSize method [.NET Framework debugging]
ms.assetid: 115bc6de-f5e2-4e8e-bb38-c7cf54045434
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 89df0e9be0600b51dcc8a68c5aba3f06e86e1b53
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700810"
---
# <a name="icordebugcodegetsize-method"></a>ICorDebugCode::GetSize, méthode

Obtient la taille, en octets, du code binaire représenté par ce « ICorDebugCode ».

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetSize (
    [out] ULONG32    *pcBytes
);
```

## <a name="parameters"></a>Paramètres

 `pcBytes`  
 à Pointeur vers la taille, en octets, du code binaire que cet objet `ICorDebugCode` représente.

## <a name="requirements"></a>Configuration requise

 **Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).

 **En-tête :** CorDebug. idl, CorDebug. h

 **Bibliothèque** CorGuids.lib

 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
 
