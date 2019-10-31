---
title: Fonction ConnectServerWmi (référence des API non managées)
description: La fonction ConnectServerWmi utilise DCOM pour créer une connexion à un espace de noms WMI.
ms.date: 11/06/2017
api_name:
- ConnectServerWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ConnectServerWmi
helpviewer_keywords:
- ConnectServerWmi function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 25a73060ed242fd0e77042cd0ea9618b9b27250f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128692"
---
# <a name="connectserverwmi-function"></a>ConnectServerWmi fonction)

Crée une connexion via DCOM à un espace de noms WMI sur un ordinateur spécifié.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT ConnectServerWmi (
   [in] BSTR               strNetworkResource,
   [in] BSTR               strUser,
   [in] BSTR               strPassword,
   [in] BSTR               strLocale,
   [in] long               lSecurityFlags,
   [in] BSTR               strAuthority,
   [in] IWbemContext*      pCtx,
   [out] IWbemServices**   ppNamespace,
   [in] DWORD              impLevel,
   [in] DWORD              authLevel
);
```

## <a name="parameters"></a>Paramètres

`strNetworkResource`\
dans Pointeur vers un `BSTR` valide qui contient le chemin d’accès de l’objet de l’espace de noms WMI correct. Pour plus d’informations, consultez la section [Notes](#remarks) .

`strUser`\
dans Pointeur vers un `BSTR` valide qui contient le nom d’utilisateur. Une valeur `null` indique le contexte de sécurité actuel. Si l’utilisateur provient d’un domaine différent de celui en cours, `strUser` peut également contenir le domaine et le nom d’utilisateur séparés par une barre oblique inverse. `strUser` peut également être au format UPN (user principal name), tel que `userName@domainName`. Pour plus d’informations, consultez la section [Notes](#remarks) .

`strPassword`\
dans Pointeur vers un `BSTR` valide qui contient le mot de passe. `null` indique le contexte de sécurité actuel. Une chaîne vide ("") indique un mot de passe de longueur nulle valide.

`strLocale`\
dans Pointeur vers un `BSTR` valide qui indique les paramètres régionaux corrects pour la récupération d’informations. Pour les identificateurs de paramètres régionaux Microsoft, le format de la chaîne est « MS\_*xxx*», où *xxx* est une chaîne au format hexadécimal qui indique l’identificateur de paramètres régionaux (LCID). Si des paramètres régionaux non valides sont spécifiés, la méthode retourne `WBEM_E_INVALID_PARAMETER` sauf sur Windows 7, où les paramètres régionaux par défaut du serveur sont utilisés à la place. Si « NULL1 », les paramètres régionaux actuels sont utilisés.

`lSecurityFlags`\
dans Indicateurs à passer à la méthode `ConnectServerWmi`. La valeur zéro (0) pour ce paramètre entraîne l’appel à `ConnectServerWmi` retourner uniquement après l’établissement d’une connexion au serveur. Cela peut empêcher une application de répondre indéfiniment en cas de rupture du serveur. Les autres valeurs valides sont les suivantes :

| Constante  | valeur  | Description  |
|---------|---------|---------|
| `CONNECT_REPOSITORY_ONLY` | 0x40 | Réservé à un usage interne. Ne pas utiliser. |
| `WBEM_FLAG_CONNECT_USE_MAX_WAIT` | 0x80 | `ConnectServerWmi` retourne en deux minutes ou moins. |

`strAuthority`\
dans Nom de domaine de l’utilisateur. Il peut afficher les valeurs suivantes :

| valeur | Description |
|---------|---------|
| vide | L’authentification NTLM est utilisée et le domaine NTLM de l’utilisateur actuel est utilisé. Si `strUser` spécifie le domaine (emplacement recommandé), il ne doit pas être spécifié ici. La fonction retourne `WBEM_E_INVALID_PARAMETER` si vous spécifiez le domaine dans les deux paramètres. |
| Kerberos :*nom principal* | L’authentification Kerberos est utilisée, et ce paramètre contient un nom de principal Kerberos. |
| NTLMDOMAIN :*nom de domaine* | L’authentification NT LAN Manager est utilisée, et ce paramètre contient un nom de domaine NTLM. |

`pCtx`\
dans En général, ce paramètre est `null`. Dans le cas contraire, il s’agit d’un pointeur vers un objet [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) requis par un ou plusieurs fournisseurs de classes dynamiques.

`ppNamespace`\
à Quand la fonction retourne une valeur, reçoit un pointeur vers un objet [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) lié à l’espace de noms spécifié. Elle est définie pour pointer vers `null` lorsqu’il y a une erreur.

`impLevel`\
dans Niveau d’emprunt d’identité.

`authLevel`\
dans Niveau d’autorisation.

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :

|Constante  |valeur  |Description  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Une défaillance générale s’est produite. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Un paramètre n’est pas valide. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | La mémoire disponible est insuffisante pour terminer l’opération. |
| `WBEM_S_NO_ERROR` | 0 | L’appel de la fonction a réussi.  |

## <a name="remarks"></a>Notes

Cette fonction encapsule un appel à la méthode [IWbemLocator :: ConnectServer](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemlocator-connectserver) .

Pour un accès local à l’espace de noms par défaut, `strNetworkResource` peut être un chemin d’objet simple : « root\default » ou «\\.\root\default ». Pour accéder à l’espace de noms par défaut sur un ordinateur distant à l’aide de COM ou de la mise en réseau compatible avec Microsoft, incluez le nom de l’ordinateur : «\\myserver\root\default ». Le nom de l’ordinateur peut également être un nom DNS ou une adresse IP. La fonction `ConnectServerWmi` peut également se connecter à des ordinateurs exécutant IPv6 à l’aide d’une adresse IPv6.

`strUser` ne peut pas être une chaîne vide. Si le domaine est spécifié dans `strAuthority`, il ne doit pas être également inclus dans `strUser`ou la fonction retourne `WBEM_E_INVALID_PARAMETER`.

## <a name="requirements"></a>spécifications

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).

 **En-tête :** WMINet_Utils. idl

 **Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performance (informations de référence sur les API non managées)](index.md)
