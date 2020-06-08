---
title: IMetaDataTables::GetUserString, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetUserString
helpviewer_keywords:
- IMetaDataTables::GetUserString method [.NET Framework metadata]
- GetUserString method, IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 35b8f0d6-9aba-4714-adb2-62020a38fb7e
topic_type:
- apiref
ms.openlocfilehash: 21ce66722e069573b651ada950b64ef6d97220fb
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501142"
---
# <a name="imetadatatablesgetuserstring-method"></a>IMetaDataTables::GetUserString, méthode

Obtient la chaîne codée en dur à l’index spécifié dans la colonne de chaîne de l’étendue actuelle.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetUserString (
    [in]  ULONG       ixUserString,
    [out] ULONG       *pcbData,
    [out] const void  **ppData
);
```

## <a name="parameters"></a>Paramètres

`ixUserString`\
dans Valeur d’index à partir de laquelle la chaîne codée en dur sera récupérée.

`pcbData`\
à Pointeur vers la taille de `ppData` .

`ppData`\
à Pointeur vers un pointeur vers la chaîne retournée.

## <a name="requirements"></a>Configuration requise

**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).

**En-tête :** Cor. h

**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll

**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Voir aussi

- [IMetaDataTables, interface](imetadatatables-interface.md)
- [IMetaDataTables2, interface](imetadatatables2-interface.md)
