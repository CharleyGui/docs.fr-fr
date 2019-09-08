---
title: Fonction PutInstanceWmi (référence des API non managées)
description: La fonction PutInstanceWmi crée ou met à jour une instance d’une classe existante.
ms.date: 11/06/2017
api_name:
- PutInstanceWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutInstanceWmi
helpviewer_keywords:
- PutInstanceWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 37810ecab2e02d4ec250dd2a4b2657c3b898f714
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798372"
---
# <a name="putinstancewmi-function"></a>PutInstanceWmi fonction)

Crée ou met à jour une instance d’une classe existante. L’instance est écrite dans le référentiel WMI.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT PutInstanceWmi (
   [in] IWbemClassObject*    pInst,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
);
```

## <a name="parameters"></a>Paramètres

`pInst`\
dans Pointeur vers l’instance à écrire.

`lFlags`\
dans Combinaison d’indicateurs qui affectent le comportement de cette fonction. Les valeurs suivantes sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :

|Constante  |`Value`  |Description  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | Si cette valeur est définie, WMI ne stocke pas de qualificateurs avec la version **modifiée** . <br> S’il n’est pas défini, il est supposé que cet objet n’est pas localisé, et tous les qualificateurs sont stockés avec cette instance. |
| `WBEM_FLAG_CREATE_OR_UPDATE` | 0 | Créez l’instance si elle n’existe pas, ou remplacez-la si elle existe déjà. |
| `WBEM_FLAG_UPDATE_ONLY` | 1 | Mettez à jour l’instance. L’instance doit exister pour que l’appel réussisse. |
| `WBEM_FLAG_CREATE_ONLY` | 2 | Créez l’instance. L’appel échoue si l’instance existe déjà. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | L’indicateur provoque un appel semi-synchrone. |

`pCtx`\
dans En général, cette valeur `null`est. Dans le cas contraire, il s’agit d’un pointeur vers une instance [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) qui peut être utilisée par le fournisseur qui fournit les classes demandées.

`ppCallResult`\
à Si `null`la condition est, ce paramètre n’est pas utilisé. Si `lFlags` `WBEM_S_NO_ERROR`contient `WBEM_FLAG_RETURN_IMMEDIATELY`, la fonction retourne immédiatement avec. Le `ppCallResult` paramètre reçoit un pointeur vers un nouvel objet [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) .

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :

|Constante  |`Value`  |Description  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | L’utilisateur n’a pas l’autorisation de mettre à jour une instance de la classe spécifiée. |
| `WBEM_E_FAILED` | 0x80041001 | Une erreur non spécifiée s’est produite. |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | La classe prenant en charge cette instance n’est pas valide. |
| `WBEM_E_ILLEGAL_NULL` | 0x80041028 | un `null` a été spécifié pour une propriété qui ne `null`peut pas être, telle que celle qui est marquée par un qualificateur **indexé** ou **not_null** . |
| `WBEM_E_INVALID_OBJECT` | 0x8004100f | L’instance spécifiée n’est pas valide. (Par exemple, l' `PutInstanceWmi` appel de avec une classe retourne cette valeur.) |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Un paramètre n’est pas valide. |
| `WBEM_E_ALREADY_EXISTS` | 0x80041019 | L' `WBEM_FLAG_CREATE_ONLY` indicateur a été spécifié, mais l’instance existe déjà. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | `WBEM_FLAG_UPDATE_ONLY`a été spécifié `lFlags`dans, mais l’instance n’existe pas. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | La mémoire disponible est insuffisante pour terminer l’opération. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI a probablement été arrêté et redémarré. Appelez à nouveau [ConnectServerWmi](connectserverwmi.md) . |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Le lien de l’appel de procédure distante (RPC) entre le processus en cours et WMI a échoué. |
| `WBEM_S_NO_ERROR` | 0 | L’appel de la fonction a réussi. |

## <a name="remarks"></a>Notes

Cette fonction encapsule un appel à la méthode [IWbemServices ::P utinstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putinstance) .

La `PutInstanceWmi` fonction prend en charge la création d’instances et la mise à jour des instances de classes existantes uniquement.  Selon la façon dont le `pCtx` paramètre est défini, une partie ou la totalité des propriétés de l’instance est mise à jour.

Lorsque l’instance désignée par `pInst` appartient à une sous-classe, la gestion Windows appelle tous les fournisseurs responsables des classes dont dérive la sous-classe. Tous ces fournisseurs doivent être correctement exécutés pour `PutInstanceWmi` que la demande d’origine aboutisse. Le fournisseur qui prend en charge la classe de niveau supérieur dans la hiérarchie est appelé en premier. L’ordre appelant continue avec la sous-classe de la classe la plus haute et s’exécute de haut en bas jusqu’à ce que la gestion de Windows atteigne le fournisseur `pInst`de la classe propriétaire de l’instance désignée par.
La gestion Windows n’appelle pas les fournisseurs pour les classes enfants d’une instance.

Quand une application doit mettre à jour une instance qui appartient à une hiérarchie de `pInst` classes, le paramètre doit pointer vers l’instance contenant les propriétés à modifier. Autrement dit, considérez une instance cible qui appartient à **ClassB**. L’instance de **ClassB** dérive de **classa**, et **classa** définit la propriété **PROPA**. Si une application souhaite apporter une modification à la valeur de **PROPA** dans l’instance de **ClassB** , elle doit être `pInst` définie sur cette instance plutôt que sur une instance de **classa**.

L' `PutInstanceWmi` appel de sur une instance d’une classe abstraite n’est pas autorisé.

Si l’appel de fonction échoue, vous pouvez obtenir des informations supplémentaires sur l’erreur en appelant la fonction [GetErrorInfo](geterrorinfo.md) .

## <a name="requirements"></a>Configuration requise

**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).

**En-tête :** WMINet_Utils.idl

**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performance (informations de référence sur les API non managées)](index.md)
