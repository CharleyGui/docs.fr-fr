---
title: StrongNameKeyInstall, fonction
ms.date: 03/30/2017
api_name:
- StrongNameKeyInstall
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyInstall
helpviewer_keywords:
- StrongNameKeyInstall function [.NET Framework strong naming]
ms.assetid: e32fd546-7757-4681-be3d-658e93281e50
topic_type:
- apiref
ms.openlocfilehash: 9e441d4da64e9704fbda2368d2b07289aaea610a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125194"
---
# <a name="strongnamekeyinstall-function"></a>StrongNameKeyInstall, fonction

Importe une paire de clés publique/privée dans un conteneur.

Cette fonction a été dépréciée. Utilisez la méthode [ICLRStrongName :: StrongNameKeyInstall](../hosting/iclrstrongname-strongnamekeyinstall-method.md) à la place.

## <a name="syntax"></a>Syntaxe

```cpp
BOOLEAN StrongNameKeyInstall (
    [in]  LPCWSTR   wszKeyContainer,
    [in]  BYTE      *pbKeyBlob,
    [in]  ULONG     cbKeyBlob
);
```

## <a name="parameters"></a>Paramètres

`wszKeyContainer`\
dans Nom du conteneur de clé. `wszKeyContainer` doit être une chaîne non vide.

`pbKeyBlob`\
dans Paire de clés binaires.

`cbKeyBlob`\
dans Taille, en octets, de `pbKeyBlob`.

## <a name="return-value"></a>Valeur de retour

`true` en cas de réussite de l’opération ; Sinon, `false`.

## <a name="remarks"></a>Notes

Utilisez la fonction [StrongNameKeyDelete (](strongnamekeydelete-function.md) pour supprimer le conteneur de clé.

Si la fonction `StrongNameKeyInstall` ne se termine pas correctement, appelez la fonction [StrongNameErrorInfo](strongnameerrorinfo-function.md) pour récupérer la dernière erreur générée.

## <a name="requirements"></a>spécifications

**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).

**En-tête :** StrongName. h

**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll

**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>Voir aussi

- [StrongNameKeyInstall, méthode](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [StrongNameKeyDelete, méthode](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [ICLRStrongName, interface](../hosting/iclrstrongname-interface.md)
