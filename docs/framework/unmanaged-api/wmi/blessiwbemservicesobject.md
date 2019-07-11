---
title: Blessiwbemservicesobject, fonction (référence des API non managées)
description: Blessiwbemservicesobject, de la fonction indique si les informations d’identification de l’utilisateur autorisent l’accès à un objet IWbemServices
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b7f24606e3b021b0df5bdbaab795e4f672f724fa
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761714"
---
# <a name="blessiwbemservicesobject-function"></a>BlessIWbemServicesObject, fonction
Indique si les informations d’identification utilisateur autorisent l’accès à une certaine [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) objet. 

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
[in] Pointeur vers un objet de service WMI.

`strUser`\
[in] Le nom d’utilisateur.

`strPassword`\
[in] Le mot de passe associé `strUser`.

`strAuthority`\
[in] Le nom de domaine de l’utilisateur. Consultez le [ConnectServerWmi](connectserverwmi.md) (fonction) pour plus d’informations.

`impLevel`\
[in] Le niveau d’emprunt d’identité.

`authnLevel`\
[in] Le niveau d’autorisation.

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes est retournées par cette fonction sont définies dans le *WinError.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :

|Constante  |`Value`  |Description  |
|---------|---------|---------|
| `E_INVALIDARG` | 0x80070057 | Un ou plusieurs arguments ne sont pas valides. |
| `E_POINTER` | 0x80004003 | `pIWbemServices` a la valeur `null`. | 
| `E_FAIL` | 0x80000008 | Une erreur non spécifiée s’est produite. |
| `E_OUTOFMEMORY` | 0x80000002 | Mémoire disponible est insuffisante pour effectuer l’opération. | 
| `S_OK` | 0 | L’appel de fonction a réussi. | 

## <a name="requirements"></a>Configuration requise

 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).

 **En-tête :** WMINet_Utils.idl

 **Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
