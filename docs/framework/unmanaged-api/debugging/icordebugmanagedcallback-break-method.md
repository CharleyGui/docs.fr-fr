---
title: ICorDebugManagedCallback::Break, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.Break
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::Break
helpviewer_keywords:
- Break method [.NET Framework debugging]
- ICorDebugManagedCallback::Break method [.NET Framework debugging]
ms.assetid: 7d78a301-82b3-43b2-9d65-3cda3285ae97
topic_type:
- apiref
ms.openlocfilehash: f70a88df00d15729a6bde06b49417b6439f7c0ec
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212462"
---
# <a name="icordebugmanagedcallbackbreak-method"></a>ICorDebugManagedCallback::Break, méthode

Notifie le débogueur lorsqu’une <xref:System.Reflection.Emit.OpCodes.Break> instruction dans le flux de code est exécutée.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Break (
    [in] ICorDebugAppDomain *pAppDomain,
    [in] ICorDebugThread    *thread
);
```

## <a name="parameters"></a>Paramètres

`pAppDomain`\
dans Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application qui contient l’instruction Break.

`thread`\
dans Pointeur vers un objet ICorDebugThread qui représente le thread qui contient l’instruction Break.

## <a name="requirements"></a>Spécifications

**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).

**En-tête :** CorDebug.idl, CorDebug.h

**Bibliothèque :** CorGuids.lib

**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>Voir aussi

- [ICorDebugManagedCallback, interface](icordebugmanagedcallback-interface.md)
