---
title: Put, fonction (référence des API non managées)
description: La fonction put assigne une nouvelle valeur à une propriété nommée.
ms.date: 11/06/2017
api_name:
- Put
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Put
helpviewer_keywords:
- Put function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5aa629c2d07fb25db035cd80aba3c74413070e6e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798398"
---
# <a name="put-function"></a>Put, fonction

Affecte une nouvelle valeur à une propriété nommée.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Put (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [in] VARIANT*          pVal,
   [in] CIMTYPE           vtType
);
```

## <a name="parameters"></a>Paramètres

`vFunc`\
dans Ce paramètre n’est pas utilisé.

`ptr`\
dans Pointeur vers une instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`wszName`\
dans Nom de la propriété. Ce paramètre ne peut pas être `null`.

`lFlags`\
[in] Réservée. Ce paramètre doit avoir la valeur 0.

`pVal`\
dans Pointeur vers un valide `VARIANT` qui devient la nouvelle valeur de propriété. Si `pVal` `VARIANT` `VT_NULL`est oupointe`null`vers un de type, la propriété a la valeur. `null`

`vtType`\
dans Type de `VARIANT` pointé par `pVal`. Pour plus d’informations, consultez la section [Notes](#remarks) .

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :

|Constante  |`Value`  |Description  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Une défaillance générale s’est produite. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Un ou plusieurs paramètres ne sont pas valides. |
|`WBEM_E_INVALID_PROPERTY_TYPE` | 0x8004102a | Le type de propriété n’est pas reconnu. Cette valeur est retournée lors de la création d’instances de classe si la classe existe déjà. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | La mémoire disponible est insuffisante pour terminer l’opération. |
| `WBEM_E_TYPE_MISMATCH` | 0x80041005 | Pour les instances : Indique que `pVal` pointe vers un `VARIANT` de type incorrect pour la propriété. <br/> Pour les définitions de classe : La propriété existe déjà dans la classe parente et le nouveau type COM est différent de l’ancien type COM. |
|`WBEM_S_NO_ERROR` | 0 | L’appel de la fonction a réussi. |

## <a name="remarks"></a>Notes

Cette fonction encapsule un appel à la méthode [IWbemClassObject ::P ut](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) .

Cette fonction remplace toujours la valeur de la propriété actuelle par une nouvelle. Si le [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointe vers une définition de classe `Put` , crée ou met à jour la valeur de la propriété. Quand [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointe vers une instance CIM, `Put` met à jour la valeur de la propriété uniquement. `Put` impossible de créer une valeur de propriété.

La `__CLASS` propriété système est accessible en écriture uniquement lors de la création de la classe, lorsqu’elle ne peut pas être laissée vide. Toutes les autres propriétés système sont en lecture seule.

Un utilisateur ne peut pas créer de propriétés dont le nom commence ou se termine par un trait de soulignement (« _ »). Cela est réservé aux classes système et aux propriétés.

Si la propriété définie par la `Put` fonction existe dans la classe parente, la valeur par défaut de la propriété est modifiée, à moins que le type de la propriété ne corresponde pas au type de la classe parente. Si la propriété n’existe pas et qu’il ne s’agit pas d’une incompatibilité de type, la propriété est créée.

Utilisez le `vtType` paramètre uniquement lors de la création de nouvelles propriétés dans une définition `pVal` de `null` classe CIM et est `VARIANT` ou pointe `VT_NULL`vers un de type. Dans ce cas, le `vType` paramètre spécifie le type CIM de la propriété. Dans tous les autres cas `vtType` , doit avoir la valeur 0. `vtType`doit également avoir la valeur 0 si l’objet sous-jacent est une `Val` instance `null`(même si a la valeur), car le type de la propriété est fixe et ne peut pas être modifié.

## <a name="example"></a>Exemple

Pour obtenir un exemple, consultez la méthode [IWbemClassObject ::P ut](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) .

## <a name="requirements"></a>Configuration requise

**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).

**En-tête :** WMINet_Utils.idl

**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performance (informations de référence sur les API non managées)](index.md)
