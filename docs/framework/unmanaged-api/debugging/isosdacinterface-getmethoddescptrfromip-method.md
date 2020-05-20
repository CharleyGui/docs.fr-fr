---
title: 'ISOSDacInterface :: GetMethodDescPtrFromIP, méthode'
ms.date: 02/01/2019
api.name:
- ISOSDacInterface::GetMethodDescPtrFromIP Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetMethodDescPtrFromIP Method
helpviewer.keywords:
- ISOSDacInterface::GetMethodDescPtrFromIP Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: c3de9e5ffe23a13c126343c6f74f042bf1239609
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421005"
---
# <a name="isosdacinterfacegetmethoddescptrfromip-method"></a>ISOSDacInterface :: GetMethodDescPtrFromIP, méthode

Récupère le pointeur de l’MethodDesc correspondant à la méthode contenant l’adresse d’instruction Native donnée.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetMethodDescPtrFromIP(
    CLRDATA_ADDRESS ip,
    CLRDATA_ADDRESS * ppMD
);
```

## <a name="parameters"></a>Paramètres

`ip`\
dans Adresse dans la méthode au moment de l’exécution.

`ppMD`\
à Adresse du `MethodDesc` pour la méthode particulière.

## <a name="remarks"></a>Notes

La méthode fournie fait partie de l' [ `ISOSDacInterface` interface](isosdacinterface-interface.md) et correspond à l’emplacement 22 de la table de méthodes virtuelles.

## <a name="requirements"></a>Conditions requises

**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
**En-tête :** None  
**Bibliothèque :** None  
**Versions de .NET Framework :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Voir aussi

- [Débogage](index.md)
- [ISOSDacInterface, interface](isosdacinterface-interface.md)
