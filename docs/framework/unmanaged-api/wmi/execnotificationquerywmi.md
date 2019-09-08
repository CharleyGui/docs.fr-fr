---
title: Fonction ExecNotificationQueryWmi (référence des API non managées)
description: La fonction ExecNotificationQueryWmi exécute une requête pour recevoir des événements.
ms.date: 11/06/2017
api_name:
- ExecNotificationQueryWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ExecNotificationQueryWmi
helpviewer_keywords:
- ExecNotificationQueryWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5cfe54c7c9b7ae707b2d3591afbd830bac171f0b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798644"
---
# <a name="execnotificationquerywmi-function"></a>ExecNotificationQueryWmi, fonction

Exécute une requête pour recevoir des événements. L’appel est retourné immédiatement, et l’appelant peut interroger l’énumérateur retourné pour les événements à mesure qu’ils arrivent. La libération de l’énumérateur retourné annule la requête.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT ExecNotificationQueryWmi (
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
dans Combinaison des deux indicateurs suivants qui affectent le comportement de cette fonction. Ces valeurs sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code.

| Constante | Valeur  | Description  |
|---------|---------|---------|
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | L’indicateur provoque un appel semi-synchrone. Si cet indicateur n’est pas défini, l’appel échoue. Cela est dû au fait que les événements sont reçus en continu, ce qui signifie que l’utilisateur doit interroger l’énumérateur retourné. Le blocage de cet appel rend indéfiniment impossible. |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | La fonction retourne un énumérateur avant uniquement. En général, les énumérateurs avant uniquement sont plus rapides et utilisent moins de mémoire que les énumérateurs conventionnels, mais ils n’autorisent pas les appels à [cloner](clone.md). |

`pCtx`\
dans En général, cette valeur `null`est. Dans le cas contraire, il s’agit d’un pointeur vers une instance [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) qui peut être utilisée par le fournisseur qui fournit les événements demandés.

`ppEnum`\
à Si aucune erreur ne se produit, reçoit le pointeur vers l’énumérateur qui permet à l’appelant de récupérer les instances dans le jeu de résultats de la requête. Pour plus d’informations, consultez la section [Notes](#remarks) .

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

|Constante  |Valeur  |Description  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | L’utilisateur n’a pas l’autorisation d’afficher une ou plusieurs des classes que la fonction peut retourner. |
| `WBEM_E_FAILED` | 0x80041001 | Une erreur non spécifiée s’est produite. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Un paramètre n’est pas valide. |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | La requête spécifie une classe qui n’existe pas. |
| `WBEMESS_E_REGISTRATION_TOO_PRECISE` | 0x80042002 | Une précision trop importante a été demandée pour la remise des événements. Une plus grande tolérance d’interrogation doit être spécifiée. |
| `WBEMESS_E_REGISTRATION_TOO_BROAD` | 0x80042001 | La requête demande plus d’informations que la gestion de Windows. Cette `HRESULT` valeur est retournée lorsqu’une requête d’événement entraîne une demande d’interrogation de tous les objets d’un espace de noms. |
| `WBEM_E_INVALID_QUERY` | 0x80041017 | La requête comportait une erreur de syntaxe. |
| `WBEM_E_INVALID_QUERY_TYPE` | 0x80041018 | Le langage de requête demandé n’est pas pris en charge. |
| `WBEM_E_QUOTA_VIOLATION` | 0x8004106c | La requête est trop complexe. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | La mémoire disponible est insuffisante pour terminer l’opération. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI a probablement été arrêté et redémarré. Appelez à nouveau [ConnectServerWmi](connectserverwmi.md) . |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Le lien de l’appel de procédure distante (RPC) entre le processus en cours et WMI a échoué. |
| `WBEM_E_UNPARSABLE_QUERY` | 0x80041058 | La requête ne peut pas être analysée. |
| `WBEM_S_NO_ERROR` | 0 | L’appel de la fonction a réussi.  |

## <a name="remarks"></a>Notes

Cette fonction encapsule un appel à la méthode [IWbemServices :: ExecNotificationQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execnotificationquery) .

Une fois que la fonction a retourné une valeur, l' `ppEnum` appelant passe régulièrement l’objet retourné à la fonction [suivante](next.md) pour voir si des événements sont disponibles.

Il existe des limites concernant le nombre `AND` de `OR` Mots clés et qui peuvent être utilisés dans les requêtes WQL. Un grand nombre de mots clés WQL utilisés dans une requête complexe peut faire en sorte `WBEM_E_QUOTA_VIOLATION` `HRESULT` que WMI retourne le code d’erreur (ou 0x8004106c) en tant que valeur. La limite des mots clés WQL dépend de la complexité de la requête.

Si l’appel de fonction échoue, vous pouvez obtenir des informations supplémentaires sur l’erreur en appelant la fonction [GetErrorInfo](geterrorinfo.md) .

## <a name="requirements"></a>Configuration requise

**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).

**En-tête :** WMINet_Utils.idl

**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performance (informations de référence sur les API non managées)](index.md)
