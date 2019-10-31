---
title: StrongNameKeyDelete, fonction
ms.date: 03/30/2017
api_name:
- StrongNameKeyDelete
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyDelete
helpviewer_keywords:
- StrongNameKeyDelete function [.NET Framework strong naming]
ms.assetid: 313e71e4-1790-4d2f-b68b-5040ebd1c149
topic_type:
- apiref
ms.openlocfilehash: d37f990241ae704abef55d863da0f40a31284837
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141588"
---
# <a name="strongnamekeydelete-function"></a>StrongNameKeyDelete, fonction

Supprime le conteneur de clé spécifié.

Cette fonction a été dépréciée. Utilisez la méthode [ICLRStrongName :: StrongNameKeyDelete (](../hosting/iclrstrongname-strongnamekeydelete-method.md) à la place.

## <a name="syntax"></a>Syntaxe

```cpp
BOOLEAN StrongNameKeyDelete (
    [in]  LPCWSTR   wszKeyContainer
);
```

## <a name="parameters"></a>Paramètres

`wszKeyContainer`\
dans Nom du conteneur de clé à supprimer.

## <a name="return-value"></a>Valeur de retour

`true` en cas de réussite de l’opération ; Sinon, `false`.

## <a name="remarks"></a>Notes

Utilisez la fonction [StrongNameKeyInstall](strongnamekeyinstall-function.md) pour importer une paire de clés publique/privée dans un conteneur.

Si la fonction `StrongNameKeyDelete` ne se termine pas correctement, appelez la fonction [StrongNameErrorInfo](strongnameerrorinfo-function.md) pour récupérer la dernière erreur générée.

## <a name="requirements"></a>spécifications

**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).

**En-tête :** StrongName. h

**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll

**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>Voir aussi

- [StrongNameKeyDelete, méthode](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [StrongNameKeyInstall, méthode](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [ICLRStrongName, interface](../hosting/iclrstrongname-interface.md)
