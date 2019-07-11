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
ms.openlocfilehash: 97079b824dbd0e056374af4173e49304babd6c32
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739135"
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
| `bHasNativeCode`             | Indique si le runtime est disponible pour l’instanciation spécifique de la méthode de code natif. |
| `bIsDynamic`                 | Indique si la méthode générée dynamiquement via la génération de code léger.           |
| `wSlotNumber`                | Numéro d’emplacement de la méthode dans la table de méthodes.                                                   |
| `NativeCodeAddr`             | Adresse native initiale de la méthode.                                                            |
| `data`                       | Pointeur vers une mémoire tampon utilisée en interne par le runtime.                                             |
| `MethodDescPtr`              | Pointeur vers le `MethodDesc` dans le runtime.                                                     |
| `nativeCodeInfo`             | Pointeur vers une mémoire tampon utilisée en interne par le runtime pour effectuer le suivi de méthodes.                            |
| `moduleInfo`                 | Pointeur vers une mémoire tampon utilisée en interne par le runtime pour des informations sur le module.                      |
| `MDToken`                    | Jeton associé à la méthode donnée.                                                         |
| `payloadGC`                  | Pointeur vers une mémoire tampon de collection de mémoire utilisée en interne par le runtime.                          |
| `payloadGC2`                 | Pointeur vers une mémoire tampon de collection de mémoire utilisée en interne par le runtime.                          |
| `managedDynamicMethodObject` | Si la méthode est dynamique, le runtime utilise cette mémoire tampon en interne pour plus d’informations de suivi.     |
| `requestedIP`                | Utilisé pour remplir la structure par demande en fonction d’une adresse de code natif.                    |
| `rejitDataCurrent`           | Informations sur la dernière version de la méthode instrumentée.                                   |
| `rejitDataRequested`         | Informations de ReJIT pour l’adresse native demandée.                                             |
| `cJittedRejitVersions`       | Nombre de fois que la méthode a été rejitted via l’instrumentation.                           |

## <a name="remarks"></a>Notes

Cette structure se trouve au sein du runtime et n’est pas exposée par le biais d’en-têtes ou les fichiers de bibliothèque. Pour l’utiliser, définir la structure comme indiqué ci-dessus.

## <a name="requirements"></a>Configuration requise
**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
**En-tête :** Aucun  
**Bibliothèque :** Aucun  
**Versions du .NET Framework :** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Voir aussi

- [Débogage](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [Structures de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Types de données communs](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)
