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
ms.openlocfilehash: 0fd7dfc1a48e21abbc80692c110bee55beb68e6b
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82892863"
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
dans A la `true` valeur en cas de continuation à partir d’un événement hors bande ; Sinon, affectez `false`à la valeur.

## <a name="remarks"></a>Notes 

`Continue`poursuit le processus après un appel à la `ICorDebugController::Stop` méthode.

Lors du débogage en mode mixte, n’appelez `Continue` pas sur le thread d’événements Win32 à moins que vous ne continuiez à partir d’un événement hors bande.

Un *événement intrabande* est un événement managé ou un événement non managé normal, pendant lequel le débogueur prend en charge l’interaction avec l’état managé du processus. Dans ce cas, le débogueur reçoit le rappel [ICorDebugUnmanagedCallback ::D ebugevent](icordebugunmanagedcallback-debugevent-method.md) avec son `fOutOfBand` paramètre défini sur `false`.

Un *événement hors bande* est un événement non managé pendant lequel l’interaction avec l’état managé du processus est impossible tant que le processus est arrêté en raison de l’événement. Dans ce cas, le débogueur reçoit le `ICorDebugUnmanagedCallback::DebugEvent` rappel avec son `fOutOfBand` paramètre défini sur `true`.

## <a name="requirements"></a>Spécifications

**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).

**En-tête :** CorDebug.idl, CorDebug.h

**Bibliothèque :** CorGuids.lib

**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
