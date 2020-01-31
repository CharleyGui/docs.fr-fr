---
title: DacpReJitData, structure
ms.date: 02/01/2019
api.name:
- DacpReJitData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpReJitData Structure
helpviewer.keywords:
- DacpReJitData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 46031f29da6916eeaeea863ebef6924a720d7155
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793816"
---
# <a name="dacprejitdata-structure"></a>DacpReJitData, structure

Définit les informations de base sur une méthode instrumentée de profileur donnée.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntaxe

```cpp
struct MSLAYOUT DacpReJitData
{
    enum Flags
    {
        kUnknown,
        kRequested,
        kActive,
        kReverted,
    };

    CLRDATA_ADDRESS                 rejitID;
    Flags                           flags;
    CLRDATA_ADDRESS                 NativeCodeAddr;
};
```

## <a name="members"></a>Members

| Member           | Description                                                                                      |
| ---------------- | ------------------------------------------------------------------------------------------------ |
| `rejitID`        | Numéro de révision ReJit pour une méthode.                                                          |
| `flags`          | Indicateur qui spécifie l’état actuel de l’instrumentation ReJit de la méthode pour la version donnée. |
| `NativeCodeAddr` | Adresse de base de l’implémentation rejitted de la méthode.                                         |

## <a name="remarks"></a>Notes

Cette structure se trouve à l’intérieur du runtime et n’est pas exposée via des en-têtes ou des fichiers de bibliothèque. Pour l’utiliser, définissez la structure comme indiqué ci-dessus. La structure doit également être définie à l’aide de `ms_struct` empaquetage si vous n’utilisez pas les compilateurs Microsoft.

## <a name="requirements"></a>Configuration requise pour
**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
**En-tête :** None  
**Bibliothèque :** None  
**Versions du .NET Framework :** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Voir aussi

- [Débogage](index.md)
- [Structures de débogage](debugging-structures.md)
