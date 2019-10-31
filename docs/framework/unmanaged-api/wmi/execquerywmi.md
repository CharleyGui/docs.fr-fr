---
title: Fonction ExecQueryWmi (référence des API non managées)
description: La fonction ExecQueryWmi exécute une requête pour récupérer des objets.
ms.date: 11/06/2017
api_name:
- ExecQueryWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ExecQueryWmi
helpviewer_keywords:
- ExecQueryWmi function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 3c6ea58eca5ac635893a24b57ade261e04a69721
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130436"
---
# <a name="execquerywmi-function"></a>ExecQueryWmi, fonction

Exécute une requête pour récupérer des objets.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT ExecQueryWmi (
   [in] BSTR                    strQueryLanguage,
   [in] BSTR                    strQuery,
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

`strQueryLanguage`\
dans Chaîne avec le langage de requête valide pris en charge par la gestion de Windows. Il doit s’agir de « WQL », l’acronyme de Langage de requêtes WMI (WQL).

`strQuery`\
dans Texte de la requête. Ce paramètre ne peut pas être `null`.

`lFlags`\
dans Combinaison d’indicateurs qui affectent le comportement de cette fonction. Les valeurs suivantes sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :

| Constante | valeur  | Description  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | Si cette valeur est définie, la fonction récupère les qualificateurs modifiés stockés dans l’espace de noms localisé des paramètres régionaux de la connexion actuelle. <br/> Si la valeur n’est pas définie, la fonction récupère uniquement les qualificateurs stockés dans l’espace de noms immédiat. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | L’indicateur provoque un appel semi-synchrone. |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | La fonction retourne un énumérateur avant uniquement. En général, les énumérateurs avant uniquement sont plus rapides et utilisent moins de mémoire que les énumérateurs conventionnels, mais ils n’autorisent pas les appels à [cloner](clone.md). |
| `WBEM_FLAG_BIDIRECTIONAL` | 0 | WMI conserve les pointeurs vers les objets de l’énumération jusqu’à ce qu’ils soient libérés. |
| `WBEM_FLAG_ENSURE_LOCATABLE` | 0x100 | Garantit que tous les objets retournés contiennent suffisamment d’informations pour que les propriétés système, telles que **__PATH**, **__RELPATH**et **__SERVER**, ne soient pas `null`. |
| `WBEM_FLAG_PROTOTYPE` | 2 | Cet indicateur est utilisé pour le prototypage. Elle n’exécute pas la requête et retourne à la place un objet qui ressemble à un objet de résultat standard. |
| `WBEM_FLAG_DIRECT_READ` | 0x200 | Entraîne un accès direct au fournisseur pour la classe spécifiée, sans tenir compte de sa classe parente ou de toute sous-classe. |

Les indicateurs recommandés sont `WBEM_FLAG_RETURN_IMMEDIATELY` et `WBEM_FLAG_FORWARD_ONLY` pour des performances optimales.

`pCtx`\
dans En général, cette valeur est `null`. Dans le cas contraire, il s’agit d’un pointeur vers une instance [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) qui peut être utilisée par le fournisseur qui fournit les classes demandées.

`ppEnum`\
à Si aucune erreur ne se produit, reçoit le pointeur vers l’énumérateur qui permet à l’appelant de récupérer les instances dans le jeu de résultats de la requête. La requête peut avoir un jeu de résultats avec zéro instance. Pour plus d’informations, consultez la section [Notes](#remarks) .

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

|Constante  |valeur  |Description  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | L’utilisateur n’a pas l’autorisation d’afficher une ou plusieurs des classes que la fonction peut retourner. |
| `WBEM_E_FAILED` | 0x80041001 | Une erreur non spécifiée s’est produite. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Un paramètre n’est pas valide. |
| `WBEM_E_INVALID_QUERY` | 0x80041017 | La requête comportait une erreur de syntaxe. |
| `WBEM_E_INVALID_QUERY_TYPE` | 0x80041018 | Le langage de requête demandé n’est pas pris en charge. |
| `WBEM_E_QUOTA_VIOLATION` | 0x8004106c | La requête est trop complexe. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | La mémoire disponible est insuffisante pour terminer l’opération. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI a probablement été arrêté et redémarré. Appelez à nouveau [ConnectServerWmi](connectserverwmi.md) . |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Le lien de l’appel de procédure distante (RPC) entre le processus en cours et WMI a échoué. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | La requête spécifie une classe qui n’existe pas. |
| `WBEM_S_NO_ERROR` | 0 | L’appel de la fonction a réussi.  |

## <a name="remarks"></a>Notes

Cette fonction encapsule un appel à la méthode [IWbemServices :: ExecQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execquery) .

Cette fonction traite la requête spécifiée dans le paramètre `strQuery` et crée un énumérateur par le biais duquel l’appelant peut accéder aux résultats de la requête. L’énumérateur est un pointeur vers une interface [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) ; les résultats de la requête sont des instances d’objets de classe rendues disponibles par le biais de l’interface [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

Il existe des limites quant au nombre de mots clés `AND` et `OR` qui peuvent être utilisés dans les requêtes WQL. Un grand nombre de mots clés WQL utilisés dans une requête complexe peut faire en sorte que WMI retourne le code d’erreur `WBEM_E_QUOTA_VIOLATION` (ou 0x8004106c) sous la forme d’une valeur `HRESULT`. La limite des mots clés WQL dépend de la complexité de la requête.

Si l’appel de fonction échoue, vous pouvez obtenir des informations supplémentaires sur l’erreur en appelant la fonction [GetErrorInfo](geterrorinfo.md) .

## <a name="requirements"></a>spécifications

**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).

**En-tête :** WMINet_Utils. idl

**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performance (informations de référence sur les API non managées)](index.md)
