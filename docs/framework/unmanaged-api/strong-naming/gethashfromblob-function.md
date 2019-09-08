---
title: GetHashFromBlob, fonction
ms.date: 03/30/2017
api_name:
- GetHashFromBlob
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromBlob
helpviewer_keywords:
- GetHashFromBlob function [.NET Framework strong naming]
ms.assetid: b712d862-f2d0-4b55-87d4-65bbeadef982
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 59b4df08157ce14a58393e54b671e8f41b8998ed
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799228"
---
# <a name="gethashfromblob-function"></a>GetHashFromBlob, fonction

Obtient un hachage de l’assembly à l’adresse mémoire spécifiée, à l’aide de l’algorithme de hachage spécifié.

Cette fonction a été dépréciée. Utilisez la méthode [ICLRStrongName :: GetHashFromBlob (](../hosting/iclrstrongname-gethashfromblob-method.md) à la place.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetHashFromBlob (
    [in]  BYTE    *pbBlob,
    [in]  DWORD   cchBlob,
    [in, out] unsigned int   *piHashAlg,
    [out] BYTE    *pbHash,
    [in]  DWORD   cchHash,
    [out] DWORD   *pchHash
);
```

## <a name="parameters"></a>Paramètres

`pbBlob`\
dans Pointeur vers l’adresse du bloc de mémoire à hacher.

`cchBlob`\
dans Longueur, en octets, du bloc de mémoire.

`piHashAlg`\
[in, out] Constante qui spécifie l’algorithme de hachage. Utilisez zéro pour l’algorithme par défaut.

`pbHash`\
à Mémoire tampon de hachage retournée.

`cchHash`\
dans Taille maximale demandée de `pbHash`.

`pchHash`\
à Taille, en octets, du retourné `pbHash`.

## <a name="requirements"></a>Configuration requise

**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).

**En-tête :** StrongName.h

**Bibliothèque** Inclus en tant que ressource dans MsCorEE. dll

**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>Voir aussi

- [GetHashFromBlob, méthode](../hosting/iclrstrongname-gethashfromblob-method.md)
- [ICLRStrongName, interface](../hosting/iclrstrongname-interface.md)
