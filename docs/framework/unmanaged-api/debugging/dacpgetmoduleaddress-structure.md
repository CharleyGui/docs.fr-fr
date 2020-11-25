---
title: DacpGetModuleAddress, structure
ms.date: 01/16/2019
api.name:
- DacpGetModuleAddress Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpGetModuleAddress Structure
helpviewer.keywords:
- DacpGetModuleAddress Structure [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: a65fa9974165fa36e59a7fb83dca6dd902f7d8dc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724392"
---
# <a name="dacpgetmoduleaddress-structure"></a>DacpGetModuleAddress, structure

Définit le conteneur pour une demande d’adresse de module.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntaxe

```cpp
struct DacpGetModuleAddress
{
    CLRDATA_ADDRESS ModulePtr;
};
```

## <a name="members"></a>Membres

| Membre      | Description                |
| ----------- | -------------------------- |
| `ModulePtr` | Pointeur vers le module. |

## <a name="methods"></a>Méthodes

| Méthode                                                                                               | Description                                                                    |
| ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| [Requête](dacpgetmoduleaddress-request-method.md) | Exécute une requête pour remplir la structure à partir de la structure d’exécution donnée. |

## <a name="remarks"></a>Remarques

Cette structure se trouve à l’intérieur du runtime et n’est pas exposée via des en-têtes ou des fichiers de bibliothèque. Pour l’utiliser, définissez la structure comme indiqué ci-dessus, où `CLRDATA_ADDRESS` est un entier non signé 64 bits.

## <a name="requirements"></a>Configuration requise

**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
**En-tête :** None  
**Bibliothèque :** None  
**Versions de .NET Framework :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Voir aussi

- [Débogage](index.md)
- [Structures de débogage](debugging-structures.md)
