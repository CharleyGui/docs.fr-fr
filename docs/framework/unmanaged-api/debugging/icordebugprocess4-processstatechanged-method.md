---
title: ICorDebugProcess4::ProcessStateChanged Method
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
ms.openlocfilehash: a6f36f5b86b4fa58ce2a4ef4aa23d527f797a5a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178630"
---
# <a name="icordebugprocess4processstatechanged-method"></a>ICorDebugProcess4::ProcessStateChanged Method

Informe le pipeline ICorDebug que le débbuggeur hors processus poursuit l’exécution du débbugee.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT ProcessStateChanged(
    [in] CorDebugStateChange change
);
```

## <a name="parameters"></a>Paramètres

 `eChange`\
[dans] Un membre du [recensement corDebugStateChange](cordebugstatechange-enumeration.md) décrivant un changement dans l’état d’exécution du processus.

## <a name="remarks"></a>Notes 

La méthode fournie fait `ICorDebugProcess4` partie de l’interface et correspond à la quatrième fente de la table de méthode virtuelle.

## <a name="requirements"></a>Spécifications

 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).

 **En-tête:** Aucun

 **Bibliothèque:** Aucun

 **.NET Versions-cadre:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Voir aussi

- [ICorDebugProcess4, interface](icordebugprocess4-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)
