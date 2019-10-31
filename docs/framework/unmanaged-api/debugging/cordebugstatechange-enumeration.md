---
title: CorDebugStateChange, énumération
ms.date: 02/07/2019
api_name:
- CorDebugStateChange
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 1d4424ab-5143-4e50-a84a-ceeb4ddf3bba
topic_type:
- apiref
ms.openlocfilehash: 239e3a82df0e6010278669f9f429bfad0d163319
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133721"
---
# <a name="cordebugstatechange-enumeration"></a>CorDebugStateChange, énumération

Représente la quantité de données mises en cache à ignorer sur la base des modifications apportées au processus.

## <a name="syntax"></a>Syntaxe

```cpp
typedef enum CorDebugStateChange
{
    PROCESS_RUNNING = 0x0000001,
    FLUSH_ALL       = 0x0000002,
} CorDebugStateChange;
```

## <a name="members"></a>Membres

| Membre            | Description                                                              |
| ----------------- | ------------------------------------------------------------------------ |
| `PROCESS_RUNNING` | Le processus a atteint un nouvel état de mémoire via l'exécution en avant.            |
| `FLUSH_ALL`       | La mémoire du processus peut être arbitrairement différente de ce qu'elle était précédemment. |

## <a name="remarks"></a>Notes

 Un membre de l’énumération `CorDebugStateChange` est fourni en tant qu’argument lorsque le débogueur appelle la méthode `ProcessStateChanged` avec [ICorDebugProcess4 ::P rocessstatechanged](icordebugprocess4-processstatechanged-method.md) ou [ICorDebugProcess6 ::P rocessstatechanged](icordebugprocess6-processstatechanged-method.md)

## <a name="requirements"></a>spécifications

 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).

 **En-tête :** CorDebug.idl, CorDebug.h

 **Bibliothèque :** CorGuids.lib

 **Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Voir aussi

- [Énumérations de débogage](debugging-enumerations.md)
- [Débogage](index.md)
