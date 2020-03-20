---
title: Fonction BlessIWbemServices (Référence API non galée)
description: La fonction BlessIWbemServices indique si les informations d’identification des utilisateurs permettent l’accès à une classe IWbemServices.
ms.date: 11/06/2017
api_name:
- BlessIWbemServices
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BlessIWbemServices
helpviewer_keywords:
- BlessIWbemServices function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 4b15af840cc00b3ec261604db4f3625c6b975d3e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176862"
---
# <a name="blessiwbemservices-function"></a>BlessIWbemServices, fonction
Indique si les informations d’identification de l’utilisateur permettent l’accès à la classe [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) spécifiée.
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT BlessIWbemServices (
   [in] IWbemServices* pIWbemServices,
   [in] BSTR strUser,
   [in] BSTR strPassword,
   [in] BSTR strAuthority,
   [in] DWORD impLevel,
   [in] DWORD authnLevel
);
```  

## <a name="parameters"></a>Paramètres

`pIWbemServices`\
[dans] Un pointeur sur l’objet [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) pour lequel des autorisations sont requises.

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
