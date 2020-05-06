---
title: DacpGetModuleAddress::Request, méthode
ms.date: 01/16/2019
api.name:
- DacpGetModuleAddress::Request Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpGetModuleAddress::Request Method
helpviewer.keywords:
- DacpGetModuleAddress::Request Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 1755526636bed6d78663112e4c2ad5ab7c3f731c
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860840"
---
# <a name="dacpgetmoduleaddressrequest-method"></a>DacpGetModuleAddress::Request, méthode

Exécute une requête pour remplir la structure à partir de la structure d’exécution donnée.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Request(
    [in] IXCLRDataModule* pDataModule
);
```

## <a name="parameters"></a>Paramètres

`pDataModule`\
dans Pointeur vers le module de données de départ.

## <a name="remarks"></a>Notes 

Cette structure se trouve à l’intérieur du runtime et n’est pas exposée via des en-têtes ou des fichiers de bibliothèque. Pour l’utiliser, le moyen le plus simple consiste à imiter l’implémentation :

- Retournez la valeur obtenue à partir de `Request` l’appel de `IXCLRDataModule*` la méthode sur le paramètre avec les paramètres suivants :`((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`

## <a name="requirements"></a>Spécifications

**Plateformes :** Voir [Configuration système requise](../../get-started/system-requirements.md)\
**En-tête :** None
**Bibliothèque :** None
**Versions de .NET Framework :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]

## <a name="see-also"></a>Voir aussi

- [Débogage](index.md)
- [DacpGetModuleAddress, structure](dacpgetmoduleaddress-structure.md)
