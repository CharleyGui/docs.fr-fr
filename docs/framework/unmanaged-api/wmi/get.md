---
title: Obtenez la fonction (référence API non gestion)
description: La fonction Get récupère la valeur de la propriété spécifiée.
ms.date: 11/06/2017
api_name:
- Get
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Get
helpviewer_keywords:
- Get function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 67fcfb301eebfcf4ed4fdcaa5c9ddf85c47a6073
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174977"
---
# <a name="get-function"></a>Get, fonction

Récupère la valeur de la propriété spécifiée si elle existe.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Get (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [out] VARIANT*         pVal,
   [out] CIMTYPE*         pvtType,
   [out] LONG*            plFlavor
);
```

## <a name="parameters"></a>Paramètres

`vFunc`\
[dans] Ce paramètre n’est pas utilisé.

`ptr`\
[dans] Un pointeur à une instance [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)

`wszName`\
[in] Nom de la propriété.

`lFlags`\
[in] Réservée. Ce paramètre doit être de 0.

`pVal`\
[out] Si la fonction revient avec `wszName` succès, contient la valeur de la propriété. L’argument `pval` est attribué le bon type et la valeur pour le qualificatif.

`pvtType`\
[out] Si la fonction revient avec succès, contient une [constante de type CIM](/windows/win32/api/wbemcli/ne-wbemcli-cimtype_enumeration) qui indique le type de propriété. Sa valeur peut `null`également être .

`plFlavor`\
[out] Si la fonction revient avec succès, reçoit des informations sur l’origine de la propriété. Sa valeur `null`peut être, ou l’une des constantes WBEM_FLAVOR_TYPE suivantes définies dans le fichier d’en-tête *WbemCli.h:*

|Constant  |Valeur  |Description  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | 0x40 | La propriété est une propriété système standard. |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | 0x20 | Pour une classe : La propriété est héritée de la classe mère. <br> Par exemple : La propriété, bien qu’héritée de la classe mère, n’a pas été modifiée par l’exemple.  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | 0 | Pour une classe: La propriété appartient à la classe dérivée. <br> Par exemple : La propriété est modifiée par l’exemple; c’est-à-dire qu’une valeur a été fournie, ou qu’un qualificatif a été ajouté ou modifié. |

## <a name="return-value"></a>Valeur retournée

Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli.h,* ou vous pouvez les définir comme des constantes dans votre code :

|Constant  |Valeur  |Description  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Il y a eu un échec général. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Un ou plusieurs paramètres ne sont pas valides. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | La propriété spécifiée n’a pas été trouvée. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | La mémoire n'est pas suffisante pour terminer cette opération. |
|`WBEM_S_NO_ERROR` | 0 | L’appel de fonction a été réussi.  |

## <a name="remarks"></a>Notes 

Cette fonction enveloppe un appel à [l’IWbemClassObject::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get) méthode.

La `Get` fonction peut également retourner les propriétés du système.

L’argument `pVal` est attribué le bon type et la valeur pour le qualificatif et la fonction COM [VariantInit](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit)

## <a name="requirements"></a>Spécifications

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).

 **En-tête:** WMINet_Utils.idl

 **.NET Versions-cadre:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
