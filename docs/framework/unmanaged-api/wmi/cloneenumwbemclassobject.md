---
title: CloneEnumWbemClassObject fonction (référence API non géré)
description: La fonction CloneEnumWbemClassObject fait une copie logique d’un enumérateur.
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
ms.openlocfilehash: f2a3a7e848108e50c04f0ec70cf42586755a0a88
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175016"
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
[out] Reçoit un pointeur à un nouveau [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject).

`authLevel`\
[dans] Le niveau d’autorisation.

`impLevel`\
[dans] Le niveau d’usurpation d’identité.

`pCurrentEnumWbemClassObject`\
[out] Un pointeur à l’instance [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) à cloner.

`strUser`\
[dans] Le nom d’utilisateur. Consultez la fonction [ConnectServerWmi](connectserverwmi.md) pour plus d’informations.

`strPassword`\
[dans] Le mot de passe. Consultez la fonction [ConnectServerWmi](connectserverwmi.md) pour plus d’informations.

`strAuthority`\
[dans] Le nom de domaine de l’utilisateur. Consultez la fonction [ConnectServerWmi](connectserverwmi.md) pour plus d’informations.

## <a name="return-value"></a>Valeur retournée

Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli.h,* ou vous pouvez les définir comme des constantes dans votre code :

|Constant  |Valeur  |Description  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Il y a eu un échec général. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Un paramètre est invalide. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Pas assez de mémoire est disponible compléter l’opération. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Le lien d’appel à distance (RPC) entre le processus actuel et WMI a échoué. |
| `WBEM_S_NO_ERROR` | 0 | L’appel de fonction a été réussi.  |

## <a name="remarks"></a>Notes 

Cette fonction enveloppe un appel à [l’IEnumWbemClassObject::Méthode Clone.](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone)

Cette méthode ne fait qu’une copie du « meilleur effort ». En raison de la nature dynamique de nombreux objets CIM, il est possible que le nouvel énumérateur n’énumère pas le même ensemble d’objets que l’enumérateur source.

Si l’appel de fonction échoue, vous pouvez obtenir des informations d’erreur supplémentaires en appelant la fonction [GetErrorInfo.](geterrorinfo.md)

## <a name="example"></a> Exemple

Par exemple, voir la méthode [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) méthode.

## <a name="requirements"></a>Spécifications
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).

 **En-tête:** WMINet_Utils.idl

 **.NET Versions-cadre:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
