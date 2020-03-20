---
title: BlessIWbemServicesObject fonction (Référence API non gestion)
description: La fonction BlessIWbemServicesObject indique si les informations d’identification des utilisateurs permettent l’accès à un objet IWbemServices
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
ms.openlocfilehash: fd822f78d29ad3a75fb5e57dd7c23b7049d445b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175029"
---
# <a name="blessiwbemservicesobject-function"></a>BlessIWbemServicesObject, fonction
Indique si les informations d’identification de l’utilisateur permettent l’accès à un objet [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) spécifié.

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
[dans] Un pointeur vers un objet de service WMI.

`strUser`\
[dans] Le nom d’utilisateur.

`strPassword`\
[dans] Le mot `strUser`de passe associé à .

`strAuthority`\
[dans] Le nom de domaine de l’utilisateur. Consultez la fonction [ConnectServerWmi](connectserverwmi.md) pour plus d’informations.

`impLevel`\
[dans] Le niveau d’usurpation d’identité.

`authnLevel`\
[dans] Le niveau d’autorisation.

## <a name="return-value"></a>Valeur retournée

Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WinError.h,* ou vous pouvez les définir comme des constantes dans votre code :

|Constant  |Valeur  |Description  |
|---------|---------|---------|
| `E_INVALIDARG` | 0x80070057 | Un ou plusieurs arguments sont invalides. |
| `E_POINTER` | 0x80004003 | `pIWbemServices` a la valeur `null`. |
| `E_FAIL` | 0x80000008 | Une erreur inconnue s’est produite. |
| `E_OUTOFMEMORY` | 0x80000002 | Une mémoire insuffisante est disponible pour effectuer l’opération. |
| `S_OK` | 0 | L’appel de fonction a été réussi. |

## <a name="requirements"></a>Spécifications

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).

 **En-tête:** WMINet_Utils.idl

 **.NET Versions-cadre:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
