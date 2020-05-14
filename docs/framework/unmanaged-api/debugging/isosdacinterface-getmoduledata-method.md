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
ms.openlocfilehash: 14e0eb812c84a0042150345d039451adf178caf1
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396923"
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

## <a name="requirements"></a>Spécifications

**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
**En-tête :** None  
**Bibliothèque :** None  
**Versions de .NET Framework :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Voir aussi

- [Débogage](index.md)
- [ISOSDacInterface, interface](isosdacinterface-interface.md)
