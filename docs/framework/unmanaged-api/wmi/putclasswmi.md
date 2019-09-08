---
title: Fonction PutClassWmi (référence des API non managées)
description: La fonction PutClassWmi crée une nouvelle classe ou met à jour une classe existante.
ms.date: 11/06/2017
api_name:
- PutClassWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutClassWmi
helpviewer_keywords:
- PutClassWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7fcf879705135e0093868b48580a37f9d46aa594
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798382"
---
# <a name="putclasswmi-function"></a>PutClassWmi fonction)

Crée une classe ou met à jour une classe existante.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT PutClassWmi (
   [in] IWbemClassObject*    pObject,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
);
```

## <a name="parameters"></a>Paramètres

`pObject`\
dans Pointeur vers une définition de classe valide. Elle doit être correctement initialisée avec toutes les valeurs de propriété requises.

`lFlags`\
dans Combinaison d’indicateurs qui affectent le comportement de cette fonction. Les valeurs suivantes sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :

|Constante  |`Value`  |Description  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | Si cette valeur est définie, WMI ne stocke pas de qualificateurs avec la version modifiée. <br> S’il n’est pas défini, il est supposé que cet objet n’est pas localisé, et tous les qualificateurs sont stockés avec cette instance. |
| `WBEM_FLAG_CREATE_OR_UPDATE` | 0 | Créez la classe si elle n’existe pas, ou remplacez-la si elle existe déjà. |
| `WBEM_FLAG_UPDATE_ONLY` | 1 | Mettez à jour la classe. La classe doit exister pour que l’appel réussisse. |
| `WBEM_FLAG_CREATE_ONLY` | 2 | Créez la classe. L’appel échoue si la classe existe déjà. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | L’indicateur provoque un appel semi-synchrone. |
| `WBEM_FLAG_OWNER_UPDATE` | 0x10000 | Les fournisseurs de notifications push doivent spécifier `PutClassWmi` cet indicateur lors de l’appel de pour indiquer que cette classe a été modifiée. |
| `WBEM_FLAG_UPDATE_COMPATIBLE` | 0 | Permet à une classe d’être mise à jour s’il n’y a pas de classes dérivées et aucune instance de cette classe. Il autorise également les mises à jour dans tous les cas si la modification concerne uniquement des qualificateurs peu importants, tels que le qualificateur de description. Si la classe a des instances ou des modifications pour des qualificateurs importants, la mise à jour échoue. |
| `WBEM_FLAG_UPDATE_SAFE_MODE` | 0x20 | Autorise les mises à jour des classes, même s’il existe des classes enfants tant que la modification n’entraîne pas de conflits avec les classes enfants. Par exemple, cet indicateur permet d’ajouter une nouvelle propriété à la classe de base qui n’a pas été précédemment mentionnée dans une des classes enfants. Si la classe a des instances, la mise à jour échoue. |
| `WBEM_FLAG_UPDATE_FORCE_MODE` | 0x40 | force les mises à jour des classes lorsque des classes enfants sont en conflit. Par exemple, cet indicateur force une mise à jour si un qualificateur de classe est défini dans une classe enfant, et si la classe de base tente d’ajouter le même qualificateur qui est en conflit avec l’option existante. En mode forcé, le conflit tis est résolu en supprimant le qualificateur en conflit dans la classe enfant. |

`pCtx`\
dans En général, cette valeur `null`est. Dans le cas contraire, il s’agit d’un pointeur vers une instance [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) qui peut être utilisée par le fournisseur qui fournit les classes demandées.

`ppCallResult`\
à Si `null`la condition est, ce paramètre n’est pas utilisé. Si `lFlags` `WBEM_S_NO_ERROR`contient `WBEM_FLAG_RETURN_IMMEDIATELY`, la fonction retourne immédiatement avec. Le `ppCallResult` paramètre reçoit un pointeur vers un nouvel objet [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) .

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :

|Constante  |Valeur  |Description  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | L’utilisateur n’a pas l’autorisation de créer ou de modifier des classes. |
| `WBEM_E_FAILED` | 0x80041001 | Une erreur non spécifiée s’est produite. |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | La classe spécifiée n’est pas valide. En général, cela indique `pObject` que spécifie un objet d’instance. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Un paramètre n’est pas valide. |
| `WBEM_E_INVALID OPERATION` | 0x80041016 | Le nom de classe spécifié n’est pas valide. |
| `WBEM_E_CLASS_HAS_CHILDREN` | 0x80041025 | Une tentative a été effectuée pour apporter une modification qui invaliderait une sous-classe. |
| `WBEM_E_ALREADY_EXISTS` | 0x80041019 | L' `WBEM_FLAG_CREATE_ONLY` indicateur a été spécifié, mais la classe existe déjà. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | `WBEM_FLAG_UPDATE_ONLY`a été spécifié `lFlags`dans, et la classe est introuvable. |
| `WBEM_E_INCOMPLETE_CLASS` | 0x80041020 | Les propriétés requises pour les classes n’ont pas toutes été définies. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | La mémoire disponible est insuffisante pour terminer l’opération. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI a probablement été arrêté et redémarré. Appelez à nouveau [ConnectServerWmi](connectserverwmi.md) . |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Le lien de l’appel de procédure distante (RPC) entre le processus en cours et WMI a échoué. |
| `WBEM_S_NO_ERROR` | 0 | L’appel de la fonction a réussi.  |

## <a name="remarks"></a>Notes

Cette fonction encapsule un appel à la méthode [IWbemServices ::P utclass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putclass) .

L’utilisateur ne peut pas créer de classes dont les noms commencent ou se terminent par un caractère de soulignement.

Si l’appel de fonction échoue, vous pouvez obtenir des informations supplémentaires sur l’erreur en appelant la fonction [GetErrorInfo](geterrorinfo.md) .

## <a name="requirements"></a>Configuration requise

**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).

**En-tête :** WMINet_Utils.idl

**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performance (informations de référence sur les API non managées)](index.md)
