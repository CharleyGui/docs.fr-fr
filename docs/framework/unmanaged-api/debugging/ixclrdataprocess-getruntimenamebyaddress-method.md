---
title: 'IXCLRDataProcess :: GetRuntimeNameByAddress, méthode'
ms.date: 4/27/2020
api.name:
- IXCLRDataProcess::GetRuntimeNameByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::GetRuntimeNameByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::GetRuntimeNameByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: tommcdon
ms.author: tommcdon
ms.openlocfilehash: 6648bdafe6e5cdd402bcfa02a148c57f0f1e209e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96270489"
---
# <a name="ixclrdataprocessgetruntimenamebyaddress-method"></a>IXCLRDataProcess :: GetRuntimeNameByAddress, méthode

Obtient un nom pour l’adresse donnée.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetRuntimeNameByAddress(
    [in] CLRDATA_ADDRESS address,
    [in] ULONG32 flags,
    [in] ULONG32 bufLen,
    [out] ULONG32 *nameLen,
    [out, size_is(bufLen)] WCHAR nameBuf[],
    [out] CLRDATA_ADDRESS* displacement
);
```

## <a name="parameters"></a>Paramètres

`address`\
dans `CLRDATA_ADDRESS` Valeur qui représente une adresse de code.

`flags`\
dans Défini sur « 0 ».

`bufLen`\
dans Longueur de la mémoire tampon.

`namLen`\
à Pointeur vers le nombre de caractères retournés.

`namBuf`\
[out, size_is ( `bufLen` )] mémoire tampon d’entrée de longueur `bufLen` qui stocke le nom du Runtime.

`displacement`\
à `CLRDATA_ADDRESS` Pointeur vers l’offset de code du symbole retourné.

## <a name="remarks"></a>Notes

La méthode fournie fait partie de l' `IXCLRDataProcess` interface et correspond au 16ème emplacement de la table de méthodes virtuelles.

> [!NOTE]
> Si la mémoire tampon n’est pas assez grande pour le nom, cette méthode retourne `S_FALSE` et définit `nameLen` la longueur de mémoire tampon requise.

## <a name="requirements"></a>Spécifications

**Plateformes :** Voir [Configuration système requise](../../get-started/system-requirements.md)\
**En-tête :** None
**Bibliothèque :** None
**Versions de .NET Framework :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]

## <a name="see-also"></a>Voir aussi

- [Débogage](index.md)
- [IXCLRDataProcess, interface](ixclrdataprocess-interface.md)
