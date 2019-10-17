---
title: ICorDebugCodeEnum::Next, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugCodeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCodeEnum::Next
helpviewer_keywords:
- ICorDebugCodeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 644ece86-384d-4c63-9fba-52c789616ff7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac3fc157543f2990c7c9f9917140b35f8948108e
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395475"
---
# <a name="icordebugcodeenumnext-method"></a>ICorDebugCodeEnum::Next, méthode

Obtient le nombre spécifié d’instances « ICorDebugCode » de l’énumération, en commençant à la position actuelle.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Next (
    [in] ULONG  celt,
    [out, size_is(celt), length_is(*pceltFetched)]
        ICorDebugCode *values[],
    [out] ULONG *pceltFetched
);
```

## <a name="parameters"></a>Paramètres

`celt`  
dans Nombre d’instances `ICorDebugCode` à récupérer.

`values`  
à Tableau de pointeurs, chacun pointant vers un objet `ICorDebugCode`.

`pceltFetched`  
à Pointeur vers le nombre d’instances `ICorDebugCode` réellement retournées. Cette valeur peut être null si `celt` est un.

## <a name="requirements"></a>spécifications

**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).

**En-tête :** CorDebug.idl, CorDebug.h

**Bibliothèque :** CorGuids.lib

**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
