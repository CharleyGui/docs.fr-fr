---
title: ICorDebugProcess4 ::P méthode rocessStateChanged
ms.date: 02/07/2019
api_name:
- ICorDebugProcess4::ProcessStateChanged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess4::ProcessStateChanged
helpviewer_keywords:
- ICorDebugProcess4::ProcessStateChanged method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 910c411d2c63ce2c6cf262e28e08546657dc2a4c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213567"
---
# <a name="icordebugprocess4processstatechanged-method"></a>ICorDebugProcess4 ::P méthode rocessStateChanged

Notifie le pipeline ICorDebug que le débogueur hors processus poursuit l’exécution du débogueur.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT ProcessStateChanged(
    [in] CorDebugStateChange change
);
```

## <a name="parameters"></a>Paramètres

 `eChange`\
dans Membre de l' [énumération cordebugstatechange,](cordebugstatechange-enumeration.md) décrivant une modification de l’état d’exécution du processus.

## <a name="remarks"></a>Remarks

La méthode fournie fait partie de l' `ICorDebugProcess4` interface et correspond au quatrième emplacement de la table de méthodes virtuelles.

## <a name="requirements"></a>Spécifications

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).

 **En-tête :** None

 **Bibliothèque :** None

 **Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Voir aussi

- [ICorDebugProcess4, interface](icordebugprocess4-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)
