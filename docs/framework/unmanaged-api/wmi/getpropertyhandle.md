---
title: Getpropertyhandle, fonction (référence des API non managées)
description: Getpropertyhandle, de la fonction retourne un handle unique qui identifie une propriété.
ms.date: 11/06/2017
api_name:
- GetPropertyHandle
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetPropertyHandle
helpviewer_keywords:
- GetPropertyHandle function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d1397188b38066bac6375da0c76e7d66724a75d7
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636243"
---
# <a name="getpropertyhandle-function"></a>GetPropertyHandle, fonction

Retourne un handle unique qui identifie une propriété.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetPropertyHandle (
   [in] int                  vFunc,
   [in] IWbemObjectAccess*   ptr,
   [in] LPCWSTR              wszPropertyName,
   [out] CIMTYPE*            pType,
   [out] long*               pHandle
);
```

## <a name="parameters"></a>Paramètres

`vFunc`\
[in] Ce paramètre n’est pas utilisé.

`ptr`\
[in] Un pointeur vers un [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instance.

`wszPropertyName`\
[in] Se terminant par null chaîne de caractères encodés UTF16 qui contient le nom de propriété.

`pType`\
[out] Un pointeur vers un [ `CIMTYPE` ](/windows/desktop/api/wbemcli/ne-wbemcli-tag_cimtype_enumeration) membre d’énumération qui représente le type CIM de la propriété.

`pHandle`\
[out] Pointeur vers un entier qui contient le descripteur de propriété.

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :

|Constante  |Value  |Description  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0x80041002 | Le nom de la propriété spécifiée est introuvable. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Un paramètre n’est pas valide. |
|`WBEM_E_NOT_SUPPORTED` | 0x8004100c | La propriété demandée est de type sont `CIM_OBJECT` ou `CIM_ARRAY`. |
|`WBEM_S_NO_ERROR` | 0 | L’appel de fonction a réussi.  |

## <a name="remarks"></a>Notes

Cette fonction encapsule un appel à la [IWbemClassObject::GetPropertyHandle](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-getpropertyhandle) (méthode).

Vous pouvez utiliser ce handle pour identifier les propriétés lorsque vous utilisez [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) méthodes pour lire ou écrire des valeurs de propriété.

Handles peuvent être récupérées pour les propriétés de tous les types de données autre que `CIM_OBJECT` et `CIM_ARRAY`. Retourné handles travail sur toutes les instances d’une classe.

## <a name="requirements"></a>Configuration requise

**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).

**En-tête :** WMINet_Utils.idl

**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
