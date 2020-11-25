---
title: Fonction CreateClassEnumWmi (référence des API non managées)
description: La fonction CreateClassEnumWmi retourne un énumérateur pour toutes les classes qui répondent aux critères spécifiés.
ms.date: 11/06/2017
api_name:
- CreateClassEnumWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CreateClassEnumWmi
helpviewer_keywords:
- CreateClassEnumWmi function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 5b80954e288f6720c75d0af0b8af083fa4856754
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719734"
---
# <a name="createclassenumwmi-function"></a>CreateClassEnumWmi, fonction

Retourne un énumérateur pour toutes les classes qui remplissent les critères de sélection spécifiés.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CreateClassEnumWmi (
   [in] BSTR                    strSuperclass,
   [in] long                    lFlags,
   [in] IWbemContext*           pCtx,
   [out] IEnumWbemClassObject** ppEnum,
   [in] DWORD                   authLevel,
   [in] DWORD                   impLevel,
   [in] IWbemServices*          pCurrentNamespace,
   [in] BSTR                    strUser,
   [in] BSTR                    strPassword,
   [in] BSTR                    strAuthority
);
```

## <a name="parameters"></a>Paramètres

`strSuperclass`\
dans Si la valeur n’est pas `null` ou vide, spécifie le nom d’une classe parente ; l’énumérateur retourne uniquement les sous-classes de cette classe. Si elle est `null` ou vide et si `lFlags` est WBEM_FLAG_SHALLOW, retourne uniquement les classes de niveau supérieur (classes sans classe parente). Si la valeur est `null` ou est vide et si `lFlags` a la valeur `WBEM_FLAG_DEEP` , retourne toutes les classes de l’espace de noms.

`lFlags`\
dans Combinaison d’indicateurs qui affectent le comportement de cette fonction. Les valeurs suivantes sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :

|Constante  |Value  |Description  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | Si cette valeur est définie, la fonction récupère les qualificateurs modifiés stockés dans l’espace de noms localisé des paramètres régionaux de la connexion actuelle. <br/> Si la valeur n’est pas définie, la fonction récupère uniquement les qualificateurs stockés dans l’espace de noms immédiat. |
| `WBEM_FLAG_DEEP` | 0 | L’énumération comprend toutes les sous-classes de la hiérarchie, mais pas cette classe. |
| `WBEM_FLAG_SHALLOW` | 1 | L’énumération inclut uniquement des instances pures de cette classe et exclut toutes les instances des sous-classes qui fournissent des propriétés introuvables dans cette classe. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | L’indicateur provoque un appel semi-synchrone. |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | La fonction retourne un énumérateur avant uniquement. En général, les énumérateurs avant uniquement sont plus rapides et utilisent moins de mémoire que les énumérateurs conventionnels, mais ils n’autorisent pas les appels à [cloner](clone.md). |
| `WBEM_FLAG_BIDIRECTIONAL` | 0 | WMI conserve les pointeurs vers les objets de l’énumération jusqu’à ce qu’ils soient libérés. |

Les indicateurs recommandés sont `WBEM_FLAG_RETURN_IMMEDIATELY` et `WBEM_FLAG_FORWARD_ONLY` pour des performances optimales.

`pCtx`\
dans En général, cette valeur est `null` . Dans le cas contraire, il s’agit d’un pointeur vers une instance [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) qui peut être utilisée par le fournisseur qui fournit les classes demandées.

`ppEnum`\
à Reçoit le pointeur vers l’énumérateur.

`authLevel`\
dans Niveau d’autorisation.

`impLevel`\
dans Niveau d’emprunt d’identité.

`pCurrentNamespace`\
dans Pointeur vers un objet [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) qui représente l’espace de noms actuel.

`strUser`\
dans Nom d’utilisateur. Pour plus d’informations, consultez la fonction [ConnectServerWmi](connectserverwmi.md) .

`strPassword`\
dans Mot de passe. Pour plus d’informations, consultez la fonction [ConnectServerWmi](connectserverwmi.md) .

`strAuthority`\
dans Nom de domaine de l’utilisateur. Pour plus d’informations, consultez la fonction [ConnectServerWmi](connectserverwmi.md) .

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :

|Constante  |Value  |Description  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | L’utilisateur n’a pas l’autorisation d’afficher une ou plusieurs des classes que la fonction peut retourner. |
| `WBEM_E_FAILED` | 0x80041001 | Une erreur inconnue s’est produite. |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | `strSuperClass` n’existe pas. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Un paramètre n'est pas valide. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | La mémoire n'est pas suffisante pour terminer cette opération. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI a probablement été arrêté et redémarré. Appelez à nouveau [ConnectServerWmi](connectserverwmi.md) . |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Le lien de l’appel de procédure distante (RPC) entre le processus en cours et WMI a échoué. |
|`WBEM_S_NO_ERROR` | 0 | L’appel de la fonction a réussi.  |

## <a name="remarks"></a>Remarques

Cette fonction encapsule un appel à la méthode [IWbemServices :: CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createclassenum) .

Si l’appel de fonction échoue, vous pouvez obtenir des informations supplémentaires sur l’erreur en appelant la fonction [GetErrorInfo](geterrorinfo.md) .

## <a name="requirements"></a>Configuration requise

**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).

**En-tête :** WMINet_Utils. idl

**Versions de .NET Framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
