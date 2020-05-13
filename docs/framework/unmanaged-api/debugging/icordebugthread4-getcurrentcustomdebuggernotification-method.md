---
title: ICorDebugThread4::GetCurrentCustomDebuggerNotification, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.GetCurrentCustomDebuggerNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::GetCurrentCustomDebuggerNotification
helpviewer_keywords:
- GetCurrentCustomDebuggerNotification method [.NET Framework debugging]
- ICorDebugThread4::GetCurrentCustomDebuggerNotification method [.NET Framework debugging]
ms.assetid: 57e0f2d2-5f0e-4e2d-99ec-3f26632eb693
topic_type:
- apiref
ms.openlocfilehash: 76ad1c0ac421f05cf30f6d3d1f3e65848796a0c7
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378694"
---
# <a name="icordebugthread4getcurrentcustomdebuggernotification-method"></a>ICorDebugThread4::GetCurrentCustomDebuggerNotification, méthode

Obtient l’objet [ICorDebugManagedCallback3 :: CustomNotification,](icordebugmanagedcallback3-customnotification-method.md) actuel sur le thread actuel.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetCurrentCustomDebuggerNotification(
    [out] ICorDebugValue **ppNotificationObject
    );
```

## <a name="parameters"></a>Paramètres

`ppNotificationObject`\
à Pointeur vers l’objet actuel `ICorDebugManagedCallback3::CustomNotification` sur le thread actuel.

## <a name="remarks"></a>Remarks

La valeur de `ppNotificationObject` est null si la méthode n’est pas appelée à partir d’un `ICorDebugManagedCallback3::CustomNotification` rappel, ou si aucun objet de notification en cours n’existe.

## <a name="requirements"></a>Spécifications

**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).

**En-tête :** CorDebug.idl, CorDebug.h

**Bibliothèque :** CorGuids.lib

**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]

## <a name="see-also"></a>Voir aussi

- [ICorDebugThread4, interface](icordebugthread4-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)
