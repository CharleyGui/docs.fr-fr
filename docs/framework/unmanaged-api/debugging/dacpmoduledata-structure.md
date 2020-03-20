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
ms.openlocfilehash: c24bdce64eb7e208bf3830940d7beab1ebf92e78
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179190"
---
# <a name="dacpmoduledata-structure"></a>DacpModuleData, structure

Définit un tampon de transport pour les informations d’exécution d’un module.

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

## <a name="members"></a>Membres

| Membre    | Description                                                             |
| --------- | ----------------------------------------------------------------------- |
| `Address` | Adresse de l’objet du module.                                           |
| `File`    | Un pointeur sur le fichier portable exécutable (PE).                       |
| `ilBase`  | L’adresse de la base de l’image chargée.                                 |
| `payLoad` | Un tampon de charge utile pour les informations supplémentaires du module utilisées par l’heure d’exécution. |

## <a name="remarks"></a>Notes 

Cette structure vit à l’intérieur du temps d’exécution et n’est pas exposée à travers des en-têtes ou des fichiers de bibliothèque. Pour l’utiliser, définissez la structure comme spécifié ci-dessus.

## <a name="requirements"></a>Spécifications
**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
**En-tête:** Aucun  
**Bibliothèque:** Aucun  
**.NET Versions-cadre:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Voir aussi

- [Débogage](index.md)
- [Structures de débogage](debugging-structures.md)
