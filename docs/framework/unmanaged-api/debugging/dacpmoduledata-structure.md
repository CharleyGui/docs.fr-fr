---
title: DacpModuleData, structure
ms.date: 02/01/2019
api.name:
- DacpModuleData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpModuleData Structure
helpviewer.keywords:
- DacpModuleData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: b46a04d67f59c5031b5bd195cef4cc2275e1e5e0
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793811"
---
# <a name="dacpmoduledata-structure"></a>DacpModuleData, structure

Définit une mémoire tampon de transport pour les informations d’exécution d’un module.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntaxe

```cpp
struct DacpModuleData
{
    CLRDATA_ADDRESS Address;
    CLRDATA_ADDRESS File; 
    CLRDATA_ADDRESS  ilBase;
    char payLoad[132];
};
```

## <a name="members"></a>Members

| Member    | Description                                                             |
| --------- | ----------------------------------------------------------------------- |
| `Address` | Adresse de l’objet de module.                                           |
| `File`    | Pointeur vers le fichier exécutable portable (PE).                       |
| `ilBase`  | Adresse de la base de l’image chargée.                                 |
| `payLoad` | Mémoire tampon de charge utile pour les informations de module supplémentaires utilisées par le Runtime. |

## <a name="remarks"></a>Notes

Cette structure se trouve à l’intérieur du runtime et n’est pas exposée via des en-têtes ou des fichiers de bibliothèque. Pour l’utiliser, définissez la structure comme indiqué ci-dessus.

## <a name="requirements"></a>Configuration requise pour
**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
**En-tête :** None  
**Bibliothèque :** None  
**Versions du .NET Framework :** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Voir aussi

- [Débogage](index.md)
- [Structures de débogage](debugging-structures.md)
