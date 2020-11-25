---
title: Fonction CloneEnumWbemClassObject (référence des API non managées)
description: La fonction CloneEnumWbemClassObject effectue une copie logique d’un énumérateur.
ms.date: 11/06/2017
api_name:
- CloneEnumWbemClassObject
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CloneEnumWbemClassObject
helpviewer_keywords:
- CloneEnumWbemClassObject function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: fa8a7f436c018e3e083be452d300eb21e17f93f3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708125"
---
# <a name="cloneenumwbemclassobject-function"></a>CloneEnumWbemClassObject, fonction

Effectue une copie logique d’un énumérateur, en conservant sa position actuelle dans une énumération.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CloneEnumWbemClassObject (
   [out] IEnumWbemClassObject**  ppEnum,
   [in] DWORD                    authLevel,
   [in] DWORD                    impLevel,
   [in] IEnumWbemClassObject*    pCurrentEnumWbemClassObject,
   [in] BSTR                     strUser,
   [in] BSTR                     strPassword,
   [in BSTR]                     strAuthority
);
```

## <a name="parameters"></a>Paramètres

`ppEnum`\
à Reçoit un pointeur vers un nouveau [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject).

`authLevel`\
dans Niveau d’autorisation.

`impLevel`\
dans Niveau d’emprunt d’identité.

`pCurrentEnumWbemClassObject`\
à Pointeur vers l’instance [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) à cloner.

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
| `WBEM_E_FAILED` | 0x80041001 | Une défaillance générale s’est produite. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Un paramètre n’est pas valide. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | La mémoire disponible est insuffisante pour terminer l’opération. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Le lien de l’appel de procédure distante (RPC) entre le processus en cours et WMI a échoué. |
| `WBEM_S_NO_ERROR` | 0 | L’appel de la fonction a réussi.  |

## <a name="remarks"></a>Remarques

Cette fonction encapsule un appel à la méthode [IEnumWbemClassObject :: Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) .

Cette méthode effectue uniquement une copie « meilleur effort ». En raison de la nature dynamique de nombreux objets CIM, il est possible que le nouvel énumérateur n’énumère pas le même jeu d’objets que l’énumérateur source.

Si l’appel de fonction échoue, vous pouvez obtenir des informations supplémentaires sur l’erreur en appelant la fonction [GetErrorInfo](geterrorinfo.md) .

## <a name="example"></a>Exemple

Pour obtenir un exemple, consultez la méthode [IEnumWbemClassObject :: Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) .

## <a name="requirements"></a>Configuration requise

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).

 **En-tête :** WMINet_Utils. idl

 **Versions de .NET Framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
