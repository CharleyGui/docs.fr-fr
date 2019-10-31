---
title: ICorDebugController::Continue, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugController.Continue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Continue
helpviewer_keywords:
- Continue method [.NET Framework debugging]
- ICorDebugController::Continue method [.NET Framework debugging]
ms.assetid: 8684cd06-ad3e-48ef-832e-15320e1f43a2
topic_type:
- apiref
ms.openlocfilehash: 14356a12c944ef93dba5e7b818d3ee5cf5adc607
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125424"
---
# <a name="icordebugcontrollercontinue-method"></a>ICorDebugController::Continue, méthode

Reprend l’exécution des threads managés après un appel à la [méthode Stop](icordebugcontroller-stop-method.md).

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Continue (
    [in] BOOL fIsOutOfBand
);
```

## <a name="parameters"></a>Paramètres

`fIsOutOfBand`  
dans Défini sur `true` en cas de continuation à partir d’un événement hors bande ; Sinon, affectez la valeur `false`.

## <a name="remarks"></a>Notes

`Continue` poursuit le processus après un appel à la méthode `ICorDebugController::Stop`.

Lors du débogage en mode mixte, n’appelez pas `Continue` sur le thread d’événements Win32, à moins que vous ne continuiez à partir d’un événement hors bande.

Un *événement intrabande* est un événement managé ou un événement non managé normal, pendant lequel le débogueur prend en charge l’interaction avec l’état managé du processus. Dans ce cas, le débogueur reçoit le rappel [ICorDebugUnmanagedCallback ::D ebugevent](icordebugunmanagedcallback-debugevent-method.md) avec son paramètre `fOutOfBand` défini sur `false`.

Un *événement hors bande* est un événement non managé pendant lequel l’interaction avec l’état managé du processus est impossible tant que le processus est arrêté en raison de l’événement. Dans ce cas, le débogueur reçoit le rappel `ICorDebugUnmanagedCallback::DebugEvent` avec son paramètre `fOutOfBand` défini sur `true`.

## <a name="requirements"></a>spécifications

**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).

**En-tête :** CorDebug.idl, CorDebug.h

**Bibliothèque :** CorGuids.lib

**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
