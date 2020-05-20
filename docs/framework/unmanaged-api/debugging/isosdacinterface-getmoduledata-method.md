---
title: 'ISOSDacInterface :: GetModuleData, méthode'
ms.date: 02/01/2019
api.name:
- ISOSDacInterface::GetModuleData Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetModuleData Method
helpviewer.keywords:
- ISOSDacInterface::GetModuleData Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: b302100eb6cbfa83896cd358762c496ea01f7509
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420979"
---
# <a name="isosdacinterfacegetmoduledata-method"></a>ISOSDacInterface :: GetModuleData, méthode

Récupère les données correspondant au module chargé à une adresse donnée.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetModuleData(
    CLRDATA_ADDRESS moduleAddr,
    DacpModuleData *data
);
```

## <a name="parameters"></a>Paramètres

`moduleAddr`\
dans Adresse du module pour lequel des informations doivent être récupérées.

`data`\
à La [structure DacpModuleData](dacpmoduledata-structure.md) pour contenir les informations du module chargé.

## <a name="remarks"></a>Notes

La méthode fournie fait partie de l' `ISOSDacInterface` interface et correspond au quatorzième emplacement de la table de méthodes virtuelles.

## <a name="requirements"></a>Conditions requises

**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
**En-tête :** None  
**Bibliothèque :** None  
**Versions de .NET Framework :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Voir aussi

- [Débogage](index.md)
- [ISOSDacInterface, interface](isosdacinterface-interface.md)
