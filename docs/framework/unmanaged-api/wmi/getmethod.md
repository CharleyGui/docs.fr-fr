---
title: GetMethod, fonction (référence des API non managées)
description: La fonction GetMethod récupère des informations sur une méthode.
ms.date: 11/06/2017
api_name:
- GetMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethod
helpviewer_keywords:
- GetMethod function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 48986f5ff1cbbb45840ec1a059aa86711848d717
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73102586"
---
# <a name="getmethod-function"></a>GetMethod, fonction

Récupère les informations sur la méthode spécifiée.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetMethod (
   [in] int                vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszName,
   [in] LONG                lFlags,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature
);
```

## <a name="parameters"></a>Paramètres

`vFunc`\
dans Ce paramètre n’est pas utilisé.

`ptr`\
dans Pointeur vers une instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`wszName`\
dans Nom de la méthode. Ce paramètre ne peut pas être `null` et doit pointer vers un `LPCWSTR`valide.

`lFlags`\
[in] Réservée. Ce paramètre doit avoir la valeur 0.

`ppInSignature`\
à Pointeur vers l’adresse d’une instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) qui décrit les paramètres in de la méthode. Ce paramètre est ignoré s’il est défini sur `null`.

`ppOutSignature`\
à Pointeur vers l’adresse d’une instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) qui décrit les paramètres de sortie de la méthode. Ce paramètre est ignoré s’il est défini sur `null`.

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :

|Constante  |valeur  |Description  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0x80041002 | La propriété spécifiée est introuvable. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | La mémoire disponible est insuffisante pour terminer l’opération. |
|`WBEM_S_NO_ERROR` | 0 | L’appel de la fonction a réussi.  |

## <a name="remarks"></a>Notes

Cette fonction encapsule un appel à la méthode [IWbemClassObject :: GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) .

La gestion Windows peut définir le pointeur [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) sur `null` si la méthode n’a pas de paramètres in.

Dans `ppInSignature` et `ppOutSignature` décrivent les paramètres in et out, respectivement, en tant que propriétés dans une instance `IWbemClassObject` de la classe système [_Parameters](/windows/desktop/WmiSdk/--parameters). Les propriétés de `ppInSignature` sont nommées `Param`*n*, où *n* est la position du paramètre dans la signature de la méthode (par exemple, `Param1`, `Param2`, etc.). Les propriétés de `ppOutSignature` sont également nommées `Param`*n*, et la valeur de retour est nommée `ReturnValue`. Pour plus d’informations et pour obtenir un exemple, consultez [IWbemClassObject :: GetMethod, méthode](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod).

## <a name="requirements"></a>spécifications

**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).

**En-tête :** WMINet_Utils. idl

**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performance (informations de référence sur les API non managées)](index.md)
