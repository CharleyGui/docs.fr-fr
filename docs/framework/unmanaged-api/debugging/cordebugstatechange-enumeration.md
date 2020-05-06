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
ms.openlocfilehash: d94422d25da91cd2a6653a95cbd852c3930a151a
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795688"
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

 Un membre de l' `CorDebugStateChange` énumération est fourni en tant qu’argument lorsque le débogueur `ProcessStateChanged` appelle la méthode avec [ICorDebugProcess4 ::P rocessStateChanged](icordebugprocess4-processstatechanged-method.md) ou [ICorDebugProcess6 ::P rocessstatechanged](icordebugprocess6-processstatechanged-method.md)

## <a name="requirements"></a>Spécifications

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).

 **En-tête :** CorDebug.idl, CorDebug.h

 **Bibliothèque :** CorGuids.lib

 **Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Voir aussi

- [Énumérations de débogage](debugging-enumerations.md)
- [Débogage](index.md)
