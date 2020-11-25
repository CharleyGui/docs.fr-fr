---
title: DacpMethodDescData, structure
ms.date: 02/01/2019
api.name:
- DacpMethodDescData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpMethodDescData Structure
helpviewer.keywords:
- DacpMethodDescData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: dcf01c00a106c131646a16597dca4092a06c5983
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723062"
---
# <a name="dacpmethoddescdata-structure"></a>DacpMethodDescData, structure

Définit une mémoire tampon de transport pour les informations d’exécution d’une méthode.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntaxe

```cpp
struct DacpMethodDescData
{
    int             bHasNativeCode;
    int             bIsDynamic;
    unsigned short  wSlotNumber;
    CLRDATA_ADDRESS NativeCodeAddr;
    CLRDATA_ADDRESS data;
    CLRDATA_ADDRESS MethodDescPtr;
    CLRDATA_ADDRESS nativeCodeInfo;
    CLRDATA_ADDRESS moduleInfo;
    mdToken         MDToken;
    CLRDATA_ADDRESS payloadGC;
    CLRDATA_ADDRESS payloadGC2;
    CLRDATA_ADDRESS managedDynamicMethodObject;
    CLRDATA_ADDRESS requestedIP;
    DacpReJitData   rejitDataCurrent;
    DacpReJitData   rejitDataRequested;
    unsigned long   cJittedRejitVersions;
};
```

## <a name="members"></a>Membres

| Membre                       | Description                                                                                     |
| ---------------------------- | ----------------------------------------------------------------------------------------------- |
| `bHasNativeCode`             | Indique si le runtime a du code natif disponible pour l’instanciation donnée de la méthode. |
| `bIsDynamic`                 | Indique si la méthode est générée dynamiquement via la génération de code léger.           |
| `wSlotNumber`                | Numéro d’emplacement de la méthode dans la table de méthodes.                                                   |
| `NativeCodeAddr`             | Adresse Native initiale de la méthode.                                                            |
| `data`                       | Pointeur vers une mémoire tampon utilisée en interne par le Runtime.                                             |
| `MethodDescPtr`              | Pointeur vers le `MethodDesc` dans le Runtime.                                                     |
| `nativeCodeInfo`             | Pointeur vers une mémoire tampon utilisée en interne par le runtime pour suivre les méthodes.                            |
| `moduleInfo`                 | Pointeur vers une mémoire tampon utilisée en interne par le runtime pour les informations de module.                      |
| `MDToken`                    | Jeton associé à la méthode donnée.                                                         |
| `payloadGC`                  | Pointeur vers une mémoire tampon de garbage collection utilisée en interne par le Runtime.                          |
| `payloadGC2`                 | Pointeur vers une mémoire tampon de garbage collection utilisée en interne par le Runtime.                          |
| `managedDynamicMethodObject` | Si la méthode est dynamique, le runtime utilise cette mémoire tampon en interne pour le suivi des informations.     |
| `requestedIP`                | Utilisé pour remplir la structure par demande lorsqu’une adresse de code natif est fournie.                    |
| `rejitDataCurrent`           | Informations sur la dernière version instrumentée de la méthode.                                   |
| `rejitDataRequested`         | Informations de ReJIT pour l’adresse Native demandée.                                             |
| `cJittedRejitVersions`       | Nombre de fois que la méthode a été rejitted par l’instrumentation.                           |

## <a name="remarks"></a>Remarques

Cette structure se trouve à l’intérieur du runtime et n’est pas exposée via des en-têtes ou des fichiers de bibliothèque. Pour l’utiliser, définissez la structure comme indiqué ci-dessus.

## <a name="requirements"></a>Configuration requise

**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
**En-tête :** None  
**Bibliothèque :** None  
**Versions de .NET Framework :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Voir aussi

- [Débogage](index.md)
- [Structures de débogage](debugging-structures.md)
- [Types de données communs](../common-data-types-unmanaged-api-reference.md)
