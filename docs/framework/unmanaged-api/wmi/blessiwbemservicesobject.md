---
title: Fonction BlessIWbemServicesObject (référence des API non managées)
description: La fonction BlessIWbemServicesObject indique si les informations d’identification de l’utilisateur autorisent l’accès à un objet IWbemServices
ms.date: 11/06/2017
api_name:
- BlessIWbemServicesObject
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BlessIWbemServicesObject
helpviewer_keywords:
- BlessIWbemServicesObject function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 1aab2076f57f938715a3e65481a3540dc52279c6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719747"
---
# <a name="blessiwbemservicesobject-function"></a>BlessIWbemServicesObject, fonction

Indique si les informations d’identification de l’utilisateur autorisent l’accès à un objet [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) spécifié.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT BlessIWbemServicesObject (
   [in] IUnknown* pIUnknown,
   [in] BSTR strUser,
   [in] BSTR strPassword,
   [in] BSTR strAuthority,
   [in] DWORD impLevel,
   [in] DWORD authnLevel
);
```

## <a name="parameters"></a>Paramètres

`pIWbemServices`\
dans Pointeur vers un objet de service WMI.

`strUser`\
dans Nom d’utilisateur.

`strPassword`\
dans Mot de passe associé à `strUser` .

`strAuthority`\
dans Nom de domaine de l’utilisateur. Pour plus d’informations, consultez la fonction [ConnectServerWmi](connectserverwmi.md) .

`impLevel`\
dans Niveau d’emprunt d’identité.

`authnLevel`\
dans Niveau d’autorisation.

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *winerror. h* , ou vous pouvez les définir comme des constantes dans votre code :

|Constante  |Value  |Description  |
|---------|---------|---------|
| `E_INVALIDARG` | 0x80070057 | Un ou plusieurs arguments ne sont pas valides. |
| `E_POINTER` | 0x80004003 | `pIWbemServices` a la valeur `null`. |
| `E_FAIL` | 0x80000008 | Une erreur inconnue s’est produite. |
| `E_OUTOFMEMORY` | 0x80000002 | La mémoire disponible est insuffisante pour effectuer l’opération. |
| `S_OK` | 0 | L’appel de la fonction a réussi. |

## <a name="requirements"></a>Configuration requise

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).

 **En-tête :** WMINet_Utils. idl

 **Versions de .NET Framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
