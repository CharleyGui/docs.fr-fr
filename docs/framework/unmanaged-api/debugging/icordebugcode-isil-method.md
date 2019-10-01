---
title: ICorDebugCode::IsIL, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugCode.IsIL
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::IsIL
helpviewer_keywords:
- ICorDebugCode::IsIL method [.NET Framework debugging]
- IsIL method [.NET Framework debugging]
ms.assetid: 132ef8cc-d938-43f3-b8f2-e3b97c0ceb33
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0a81f4a53954c559ab12e27bcf039b7b1a1804cc
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700794"
---
# <a name="icordebugcodeisil-method"></a>ICorDebugCode::IsIL, méthode

Obtient une valeur qui indique si ce « ICorDebugCode » représente du code qui a été compilé en langage MSIL (Microsoft Intermediate Language).

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT IsIL (
    [out] BOOL       *pbIL
);
```

## <a name="parameters"></a>Paramètres
 `pbIL`  
 [out] `true` si cet `ICorDebugCode` représente du code qui a été compilé en MSIL ; dans le cas contraire, `false`.

## <a name="requirements"></a>Configuration requise

 **Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).  

 **En-tête :** CorDebug. idl, CorDebug. h  

 **Bibliothèque** CorGuids.lib  

 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
 
