---
title: ICorDebugProcess2::GetVersion, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetVersion
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetVersion
helpviewer_keywords:
- GetVersion method, ICorDebugProcess2 interface [.NET Framework debugging]
- ICorDebugProcess2::GetVersion method [.NET Framework debugging]
ms.assetid: e11d5a75-61d9-4548-aedf-79c26079bd17
topic_type:
- apiref
ms.openlocfilehash: 391b848d3b3f66f6af6bf3adbefb6e94d526e748
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213502"
---
# <a name="icordebugprocess2getversion-method"></a>ICorDebugProcess2::GetVersion, méthode

Obtient le numéro de version du common language runtime (CLR) qui s’exécute dans ce processus.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetVersion (
    [out] COR_VERSION     *version
);
```

## <a name="parameters"></a>Paramètres

`version`\
à Pointeur vers une structure COR_VERSION qui stocke le numéro de version du Runtime.

## <a name="remarks"></a>Remarks

La `GetVersion` méthode retourne un code d’erreur si aucun Runtime n’a été chargé dans le processus.

## <a name="requirements"></a>Spécifications

**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).

**En-tête :** CorDebug.idl, CorDebug.h

**Bibliothèque :** CorGuids.lib

**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
