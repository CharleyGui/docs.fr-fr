---
title: Fonction GetPropertyOrigin (référence des API non managées)
description: La fonction GetPropertyOrigin détermine la classe dans laquelle une propriété est déclarée.
ms.date: 11/06/2017
api_name:
- GetPropertyOrigin
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetPropertyOrigin
helpviewer_keywords:
- GetPropertyOrigin function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 6cab3765f0359f5dd18831acaaa1aefce3fe1081
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73101853"
---
# <a name="getpropertyorigin-function"></a>GetPropertyOrigin, fonction

Détermine la classe dans laquelle une propriété est déclarée.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetPropertyOrigin (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
);
```

## <a name="parameters"></a>Paramètres

`vFunc`\
dans Ce paramètre n’est pas utilisé.

`ptr`\
dans Pointeur vers une instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`wszMethodName`\
dans Nom de la propriété pour l’objet dont la classe propriétaire est demandée.

`pstrClassName`\
à Reçoit le nom de la classe qui possède la propriété.

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :

|Constante  |valeur  |Description  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Une défaillance générale s’est produite. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | La propriété spécifiée est introuvable. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Un paramètre n’est pas valide. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | La mémoire disponible est insuffisante pour terminer l’opération. |
|`WBEM_S_NO_ERROR` | 0 | L’appel de la fonction a réussi.  |

## <a name="remarks"></a>Notes

Cette fonction encapsule un appel à la méthode [IWbemClassObject :: GetPropertyOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyorigin) .

Étant donné qu’une classe peut hériter des propriétés d’une ou de plusieurs classes de base, les développeurs veulent souvent déterminer la propriété dans laquelle une méthode donnée est définie.

Le paramètre `pstrClassName` ne doit pas pointer vers un `BSTR` valide avant que la fonction soit appelée, car il s’agit d’un paramètre `out` ; ce pointeur n’est pas libéré après le retour de la fonction.

## <a name="requirements"></a>spécifications

**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).

**En-tête :** WMINet_Utils. idl

**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performance (informations de référence sur les API non managées)](index.md)
